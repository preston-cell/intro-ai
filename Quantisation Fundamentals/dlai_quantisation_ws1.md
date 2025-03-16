# Quantization Fundamentals with Hugging Face (Deeplearning.ai course)
Ref: https://learn.deeplearning.ai/courses/quantization-fundamentals

## Lesson 1: Introduction 

Watch `Introduction`, and then answer these questions: 
1. Andrew mentions **PyTorch** library. What is PyTorch? Which library that you have used so far in the course is similar to PyTorch?

   PyTorch is a library for Deep learning, dynamic computation graphs, GPU acceleration. It is similar to the Keras library we used in the Jupyter notebooks. 
   
2. Andrew also talks about **data types**. What are data types used for? List the data types that are mentioned in this video.

   Data types are used for the storage, optimized memory & computation of data. There is int8, int16, int32, int64, uint8, uint16, uint32, uint64, float16, bfloat16, float32.
   
3. What is the purpose of this course?

   Teach me how to optimize large ML models using quantization & compression to fit on limited hardware.

Watch `Handling Big Models`, and then answer these questions: 

4. Why is handling big models a problem for the AI community?

   Big models require huge memory (7B model = 280GB). Consumer GPUs (NVIDIA T4) have only 16GB RAM.
   
5. To solve this problem, the video mentions 2 techniques (not covered in detail) apart from quantization. What are they?

   Pruning = Remove unnecessary weights.
   Knowledge Distillation = Train a small model using a large one as a guide.

6. What makes a model "big"? Should we be concerned about where we store the model or how we run the model? Or both?

   Big models have many parameters, abd high memory needs.
   We should be concerned with both storage and runtime.
   
7. The video describes how quantization is done by moving from floating point (FP32) to integer (INT8). Explain how this makes the model "smaller".

   FP32 = 4 bytes/parameter, INT8 = 1 byte/parameter = 75% reduction in memory use.
   
## Lesson 2: Data types & sizes 

Watch `Data types & sizes` video to answer the questions below: 

### Integer data type

The video shows the range of values for the 2 types of integer data types: **unsigned integer** and **signed integer**. 

8. Show the formula used to calculate the **range**.

   Unsigned: 0 to (2^n-1)
   Signed: -2^(n-1) to (2^(n-1)-1)
   
10. Compute the range for **unsigned int** with 8-bits. Show the steps in your calculation.

   0 to 2^8, so 0 to 255
   
11. Compute the range for **signed int** with 8-bits. Show the steps in your calculation.

    -2^7 to (2^7 -1), so -128 to 127
   
12. Represent the values, 2, 6, 33 and 100 in the 8-bit unsigned int data format.

   2 = 00000010
   6 = 00000110
   33 = 00100001
   100 = 01100100
   
13. What is the value represented by **11010101** in unisgned integer format? What is the value in signed integer format?

    Unsigned: 213
    Signed (two’s complement): -43

### Floating point data type

13. What type of data is stored using the floating point data type?

   Decimals (real numbers)

    
14. Explain the 3 components in the floating point data type. Identify the components that represent the **range** and **precision**.

    Sign bit – Positive/negative.
    Exponent – range.
    Mantissa – precision.
    
16. What is "floating" in this data type? Explain with an example. 

    Decimal point float because they shifts based on exponent.
    1.23 × 10^2 = 123, 1.23 × 10^-2 = 0.0123.
    
17. Compare FP32, FP16 and BF16 formats in terms of precision and range.

    Format	Exponent Bits	Mantissa Bits	Precision	Range
    FP32	   8	            23	            High	      High
    FP16	   5	            10	            Lower	      Medium
    BF16	   8	            7	            Lower	      High
    
18. The video mentions **tensor**. What is a tensor?

    A multidimensional array or generalization of scalars, vectors, matrices.
    
   
19. What PyTorch function can I use to print the range of the floating point data type? Show the code for checking the range for the brain float BF16 data type.

    print(torch.finfo(torch.bfloat16))
    
### Impact of downcasting 

20. What is **downcasting**? Why do it? 

    Lower precision (FP32 to FP16/INT8) to save memory & speed up computation.
        

21. What is the impact of **downcasting** on the result of matrix multiplication?
    
    Reduces precision = possible numerical errors.
    

23. Why did the video choose matrix multiplication to check the impact of downcasting on the precision of the result?
    
    It is a core operation in deep learning. The error accumulation shows precision loss.
    

24. One of the advantages of downcasting is reduced memory footprint. How does this allow us to enable larger batch sizes? Why is having larger batch sizes beneficial to training?
   
    Smaller memory footprint = fit more samples per batch = faster, more stable training.
    
25. The video mentions a use case of **mixed precision training** with downcasting. Why would this work?
   
    It combines low precision for efficiency & high precision for critical computations (balancing speed & accuracy).
    


   
