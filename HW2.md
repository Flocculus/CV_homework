# P1

The total routine is similar to the previous homework.

First, I need to choose 4 points and create 4 corresponding new points. From these four pair of points, I can generate 8 equations to find the exact value of H matrix's 8 unknow parameters.

Second, I use SVD or just the command ***null()*** to find the eigvector of the null space, wich is just the answer of the function Y=HX

Third, after getting transformation matrix H, I just need to do transformation and interpolation as the previous homework.

The following picture is the input:
![pic](https://github.com/Flocculus/CV/blob/master/pic/inputCVP1P1.jpg)
The following picture is the answer for question 1, the top one shows the points I choose, the bottom one is the corrected picture.
![pic](https://github.com/Flocculus/CV/blob/master/pic/output1.jpg)
The following picture is the answer for question2.
![pic](https://github.com/Flocculus/CV/blob/master/pic/output2.jpg)

# P2

The first problem is to write two matlab functions: a function that fits a line to a set of points and a function determines the intersection of a set of lines. I will use least square method to find the best solution.

Due to the duality of lines and points in homogeneouls coordinate axis, these two functions are exactly the same.
```
The input is a (n,3) matirx, it contains an homogeneous coordinate of a point/line in each row.

Assume the point/line we get is (a,-1,b) and the format of the line/point is (x,1,y)

 the point/line should lie on the line/point: [1/b]=[a/b,1]*[x,y]', it has the form Y=HX

Then we want to minimizing J(X)=||Y-HX||^2

X=inv(H'*H)*H'*Y;
```

The following picture is the input picture:

![pic](https://github.com/Flocculus/CV/blob/master/pic/input.jpg)

The following picture shows the vanishing line (red line) and the vertical vanishing point (blue point):

![pic](https://github.com/Flocculus/CV/blob/master/pic/VanishingPoint%26Line.jpg)

The following picture shows the transferred point, (purple point transfer to orange point, green point transfer to yellow point):

![pic](https://github.com/Flocculus/CV/blob/master/pic/TransferredPoint.jpg)


Then you can easily calculate the height of the desk from the height of the man in the picture.






# P3

The following pictures are the input of the homwork:

![pic](https://github.com/Flocculus/CV/blob/master/pic/1.jpg)

![pic](https://github.com/Flocculus/CV/blob/master/pic/2.jpg)

The following pictures are the solutions of the homwork:

![pic](https://github.com/Flocculus/CV/blob/master/pic/CVP1P_3output1.png)

![pic](https://github.com/Flocculus/CV/blob/master/pic/CVP1P3output2.png)

Assume the fourier transform of a picture is &alpha;, the amplitude response is A_&alpha; and the phase response is P_&alpha;

We also know that the **phase change** in frequency domain is just the **space shift** in space domain

So without the phase response, or just set all the phase response of &alpha; to 0, what we do is just equal to overlape a lot of waves ***e<sup>j&omega;x</sup>*** at the origin point as the following picture.

![pic](https://github.com/Flocculus/CV/blob/master/pic/example_of_overlape.png)

No matter the weights of different waves, when we overlape all these wave, what we will get is a spike like wave. And this is why the centers of our reconstructed picture are significantly bright. So amplitude reponse contains little information.

![pic](https://github.com/Flocculus/CV/blob/master/pic/HWP_2.png)

On the other hand, the phase response P_&alpha; can be generate as the original fourier transform &alpha; times a special filter &beta;, whose amplitude response is just the **reciprocal** of A_&alpha; and whose phase response is just 1 at everywhere.

That is **P_&alpha; = &alpha; * &beta;**

And we know the multiplying in frequency domain is just equal to the convolution in space domain.

Also note that &beta; is also an overlap of a lot of waves ***e<sup>j&omega;x</sup>*** , so &beta; just looks like a **impulse function** .
 
Any singal convolutes with a impulse like function will not change a lot. So phase response P_&alpha; contains more information.
