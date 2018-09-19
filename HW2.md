Assume the fourier transform of a picture is &alpha;, the amplitude response is A_&alpha; and the phase response is P_&alpha;

We also know that the **phase change** in frequency domain is just the **space shift** in space domain

So without the phase response, or just set all the phase response of &alpha; to 0, what we do is just equal to overlape a lot of waves ***e<sup>j&omega;x</sup>*** at the origin point as the following picture.

![pic](https://github.com/Flocculus/CV/blob/master/pic/example_of_overlape.png)

No matter the weights of different waves, when we overlape all these wave, what we will get is a spike like wave. And this is why the four corners of our reconstructed picture are significantly bright. So amplitude reponse contains little information.

![pic](https://github.com/Flocculus/CV/blob/master/pic/HWP2.png)

On the other hand, the phase response P_&alpha; can be generate as the original fourier transform &alpha; times a special filter &beta;, whose amplitude response is just the **reciprocal** of A_&alpha; and whose phase response is just 1 at everywhere.

That is **P_&alpha; = &alpha; * &beta;**

And we know the multiplying in frequency domain is just equal to the convolution in space domain.

Also note that &beta; is also a overlap of a lot of waves ***e<sup>j&omega;x</sup>*** , so &beta; just looks like a **impulse function** .
 
Any singal convolutes with a impulse like function will not change a lot. So phase response P_&alpha; contains more information.