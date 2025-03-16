# Quantization Fundamentals with Hugging Face (Deeplearning.ai course)
Ref: https://learn.deeplearning.ai/courses/quantization-fundamentals

## Lesson 3: Loading ML Models with Different Data Type 

Watch `Loading models by data type`, and then answer these questions: 

### Model casting 
1. What does the `print_param_dtype()` function do? 

   It loops through the parameters of a model and prints their corresponding data types. 
   
2. Show the code that can be used to **cast** the model parameters to bfloat16 data type. 

   model = model.to(torch.bfloat16)

3. What do we mean by performing an **inference** of a model. 

    Using a trained model to make predictions on new data. 

4. What is `deepcopy` used in this video?

   deepcopy is used to create an exact duplicate of the model. The modifications to one instance do not affect the other. This is important when comparing model versions FP32 vs.      BF16 while maintaining the same weights across both models for a fair comparison.

5. The `model_bf16` uses lesser precision than the FP32 `model`. In the video, how do they compare the impact of this low precision on the model performance? Is the performance degradation significant?

   They compare by by running an inference on both and observing the generated outputs. They compute the mean difference between the logit values of both models to assess any major    discrepancies. There are only very small differences between BF16 and FP32 outputs, meaning the performance degradation is not significant. Therefore, casting to BF16 does not      noticeably impact the accuracy of the model, but significantly reduces memory usage.

### Loading model in low precision 

6. Name the Pytorch method that can be used to get the memory footprint of a model. 

   model.get_memory_footprint()

7. How is loading the model at low precision better than downcasting the weights of a loaded model?

   Loading the model directly at a lower precision is more memory-efficient because the model is initialized in the desired precision right from the start.
   Downcasting the weights after loading the model in full precision requires first loading the full-size model into memory, which increases memory usage temporarily before            reducing it.

### Linear quantisation

8. How is linear quantisation different from lower precision floating point representation?

   Lower precision floating point representation reduces the number of bits used to store each parameter but still maintains a floating-point format.
   Linear quantization converts floating-point numbers to fixed-point integers. It scales the weights using a fixed quantization factor. It then stores the weights as integers         instead of floating-point numbers

9. How does linear quantization lead to lower memory footprint?

   Linear quantization reduces the number of bits required to represent weights.
   FP32 uses 32 bits per weight INT8 uses only 8 bits per weight, so there is a 4x memory reduction.
   Since matrix multiplications and convolutions can be performed in lower-bit arithmetic (INT8 instead of FP32), quantization also leads to faster inference and reduced power         consumption.


   
