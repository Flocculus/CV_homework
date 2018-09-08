# Problem 1

## Devide the matrix to M(magnification matrix)*R(rotation matrix)*S(shear matrix)

### 1.Decompose the matrix A=[1 1 ; 1 3]

Apply SVD on the giving matrix, then rearrange the singular value matrix and the corresponding martix. What we get will be
```matlab
A=U*S*V\'
```
where 
```matlab
U=[-0.9239 -0.3827 ; 0.3827 -0.9239]
S=[0.5858 0 ; 0 3.4142]
V=[-0.9239 -0.3827 ; 0.3827 -0.9239]
```matlab