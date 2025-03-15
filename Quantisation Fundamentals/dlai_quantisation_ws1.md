# Quantization Fundamentals with Hugging Face (Deeplearning.ai course)
Ref: https://learn.deeplearning.ai/courses/quantization-fundamentals

## Lesson 1: Introduction 

Watch `Introduction`, and then answer these questions: 
1. Andrew mentions **PyTorch** library. What is PyTorch? Which library that you have used so far in the course is similar to PyTorch?

   [Your answer here]
   
2. Andrew also talks about **data types**. What are data types used for? List the data types that are mentioned in this video.

   [Your answer here]
   
3. What is the purpose of this course?

   [Your answer here]

Watch `Handling Big Models`, and then answer these questions: 

4. Why is handling big models a problem for the AI community?

   [Your answer here]
   
5. To solve this problem, the video mentions 2 techniques (not covered in detail) apart from quantization. What are they?

   [Your answer here]

6. What makes a model "big"? Should we be concerned about where we store the model or how we run the model? Or both?

   [Your answer here]
   
7. The video describes how quantization is done by moving from floating point (FP32) to integer (INT8). Explain how this makes the model "smaller".

   [Your answer here]
   
## Lesson 2: Data types & sizes 

Watch `Data types & sizes` video to answer the questions below: 

### Integer data type

The video shows the range of values for the 2 types of integer data types: **unsigned integer** and **signed integer**. 

8. Show the formula used to calculate the **range**.

   [Your answer here]
   
9. Compute the range for **unsigned int** with 8-bits. Show the steps in your calculation.

   [Your answer here]
   
10. Compute the range for **signed int** with 8-bits. Show the steps in your calculation.

    [Your answer here]
   
11. Represent the values, 2, 6, 33 and 100 in the 8-bit unsigned int data format.

    [Your answer here]
   
12. What is the value represented by **11010101** in unisgned integer format? What is the value in signed integer format?

    [Your answer here]

### Floating point data type

13. What type of data is stored using the floating point data type?

    [Your answer here]
    
14. Explain the 3 components in the floating point data type. Identify the components that represent the **range** and **precision**.

    [Your answer here]
    
16. What is "floating" in this data type? Explain with an example. 

    [Your answer here]
    
17. Compare FP32, FP16 and BF16 formats in terms of precision and range.

    [Your answer here]
    
18. The video mentions **tensor**. What is a tensor?

    [Your answer here]
    
   
19. What PyTorch function can I use to print the range of the floating point data type? Show the code for checking the range for the brain float BF16 data type.

    [Your answer here]
    
### Impact of downcasting 

20. What is **downcasting**? Why do it? 

    [Your answer here]
        

21. What is the impact of **downcasting** on the result of matrix multiplication?
    
    [Your answer here]
    

23. Why did the video choose matrix multiplication to check the impact of downcasting on the precision of the result?
    
    [Your answer here]
    

24. One of the advantages of downcasting is reduced memory footprint. How does this allow us to enable larger batch sizes? Why is having larger batch sizes beneficial to training?
   
    [Your answer here]
    
25. The video mentions a use case of **mixed precision training** with downcasting. Why would this work?
   
    [Your answer here]
    


   
