# Quantization
Step 1: First you will walk through code to quantize tensors. We will do a limited form of post training quantization, where we only will quantize the inputs passing between layers

What is quantization in this scenario?

It means given a range of values,  and a desired precision of  bits.

Find the minimum and maximum values of X,  and .

Find the minimum and maximum value of the bits, namely  and .

Set .

Note that besides scaling, we also have to consider the bias , or what  will map to. Set  as follows:

a. If ,  \ b. Else if , .
c. Else . \ d. https://docs.openvinotoolkit.org/latest/pot_compression_algorithms_quantization_README.html

The formula for quantization of  then becomes: 
 
.

The formula to dequantize becomes: .

We work through a quick example. Consider the values , . \ Then  and . . \ The quantization becomes: .

The dequantization becomes 
 
.

Qs 1.) Now fill out the following two functions to carry out quantization and dequantization. Verify for the example, but also one or two other reasonable tensors. You may need to use the clamp_ function in quantize_tensor, to make sure data remains in the range of  to . See https://pytorch.org/docs/stable/tensors.html
