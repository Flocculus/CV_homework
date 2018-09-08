# Problem 1

## Find matrix M(magnification matrix) R(rotation matrix) S(shear matrix) where A=[1 1 ; 1 3]=M*R*S

### 1.Decompose the matrix A=[1 1 ; 1 3]

Apply SVD on the giving matrix, then rearrange the singular value matrix and the corresponding martix. What we get will be
```matlab
A=U*S*V'
```
where 
```matlab
U=[-0.9239 -0.3827 ; 0.3827 -0.9239]
X=[0.5858 0 ; 0 3.4142]
V=[-0.9239 -0.3827 ; 0.3827 -0.9239]
```

### 2.Create matrixes M, R and S

We know that any shear transform can be decompsed to three transforms:

1.Rotate by &alpha;
2.Do a magnification transform
3.Rotate back by &beta; 