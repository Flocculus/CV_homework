# Problem 1

## Find matrix M(magnification matrix) R(rotation matrix) S(shear matrix) where A=[1 1 ; 1 3]=M*R*S

### 1.Decompose the matrix A=[1 1 ; 1 3]

Apply SVD on the giving matrix, then rearrange the singular value matrix and the corresponding martix. What we get will be
```
A=U*\S\*V'
```
where 
```
U=[-0.9239 -0.3827 ; 0.3827 -0.9239]
X=[0.5858 0 ; 0 3.4142]
V=[-0.9239 -0.3827 ; 0.3827 -0.9239]
```

### 2.Create matrixes M, R and S

We know that any shear transform can be decompsed to three transforms:

1.Rotate by &alpha;

2.Do a magnification transform

3.Rotate back by &beta; 

We also note that matrixes U and V are rotation matrixes, matrix X is a magnification matrix. So we can create a matrix v and let v\*X\*V' be a shear tranform, that is:
```
A=U*X*V'=α*I*U*v'*v*X*V'=M*R*S
```
where we can use v\*X\*V' to generate S, U*v' to generate R and &alpha;*I to generate M.

### 3.Get matrix v 

The shearing matrix S = v\*X\*V' can be explain as: 1. Rotate every point of the original picture by degree &alpha;. 2. Do a magnification transform. 3 Rotate the picture back to the original picture by degree &beta;. What we want to find is just the degree &beta as the following picture shows:

![pic](https://github.com/Flocculus/CV/blob/master/pic/20180912_130520.jpg)

Sine we already know the matrix S, X and V', it is easy to get v.

Finally what we get is:
```
v=[-0.3827 -0.9239 ; 0.9239 -0.3827]
M=[1.1413 0 ; 0 1.1413];
R=[0.7071 -0.7071 ; 0.7071 0.7071];
S=[1 2 ; 0 1];
```    

where v is the rotation matrix we find. M is the magnification matrix, R is the rotation matrix and S is the shearing matrix. It is easy to proof that M\*R\*S=1

## interpolation

If we just maping every input point to image by using matlab, we may meet some problems. For example an 2x2 square can be represented by a 2x2 image [1 1 ; 1 1]. If we want to magnify it to a 4x4 square, that is [X；Y]=[2 0 ; 0 2]*[x;y], what we get is not [1 1 1 1 ;1 1 1 1 ; 1 1 1 1 ; 1 1 1 1] but [0 0 0 0 ; 0 1 0 1 ; 0 0 0 0 ; 0 1 0 1]. In this case, we need to use some interpolation algorithm to make up the holes.

### nearest neighbor algorithm
In my matlab algorithm, I use the nearest neighbor method to interpolate these holes, that is, the value of a hole is the value of the nearest point.

### the way to realize the algorithm.
The way I realize the nearest neighbor is some kind of "oversampling". As the previous example, instead of just calculate the new coordinate of point (1,1), (1,2), (2,1), (2,2), we also calculate the coordinate of some not exist point like (1,1.1), (1,1.2) ...
For example, when we calculate the new coordinate of point(1.5,1.5), we will map it to (3,3), and then we just need to assign the value of point (1.5,1.5)'s nearest neighbot  (2,2) to it.