
## Resources
1. Intro to numerical computing with NumPy (Beginner) | Alex Chobot-Leclerc (https://www.youtube.com/watch?v=V0D2mhVt7NE), and its accompanied [slices](https://github.com/enthought/Numpy-Tutorial-SciPyConf-2018/blob/master/slides.pdf)

# Important things to know
1. numpy array is **row-important** (don't use np matrix, MATALB is column-important)
2. numpy array is different from python array


```python
a = [1, 2, 4, 5]
b = [4, 6, 9, 20]
a+b
```




    [1, 2, 4, 5, 4, 6, 9, 20]



### Array creation


```python
import numpy as np
a = np.array([1, 2, 4, 5])
b = np.array([4, 6, 9, 20])
a+b
```




    array([ 5,  8, 13, 25])




```python
a.ndim
```




    1




```python
a.shape
```




    (4,)




```python
a.dtype
```




    dtype('int32')




```python
c = np.array([[8, 9, 10], [11, 20, 22]])
```


```python
c
```




    array([[ 8,  9, 10],
           [11, 20, 22]])



### Slicing -- var[lower:upper:step]


```python
c[0,0]
```




    8




```python
#Partial indexing
c[0]
```




    array([ 8,  9, 10])



It is important to remember that lower-bound element is included, but the upper-bound element is **not** included.


```python
a = np.array([10, 11, 12, 13, 14])
a[1:3]
```




    array([11, 12])



Omitted boundaries are assumed to be the beginning (or end) of the list


```python
a[:3]
```




    array([10, 11, 12])



![](numpy/1.png)

Important about slicing: if you do slicing, you keep the dimension of the arrays. In comparison, you drop 1 dimension if you do indexing.


```python
a = np.arange(25).reshape(5,5); a
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])




```python
red = a[:, 1::2]
```


```python
red[-1,-1] = 0
```

Slices are **references** to memory in the original array. **Changing values in a slice also chages the original array.**


```python
a
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22,  0, 24]])




```python
red.flags
```




      C_CONTIGUOUS : False
      F_CONTIGUOUS : False
      OWNDATA : False
      WRITEABLE : True
      ALIGNED : True
      WRITEBACKIFCOPY : False
      UPDATEIFCOPY : False




```python
red.data
```




    <memory at 0x000002CBB2F13708>



### Fancy indexing - masks

One major difference between fancy indexing and slicing is that unlike slicing, fancy indexign **creates copies** instead of a view into original array as in slicing. 


```python
a = np.array([2, 3, -1, 4, 8, 9])
```


```python
a > 2
```




    array([False,  True, False,  True,  True,  True])




```python
a[a>2]
```




    array([3, 4, 8, 9])



![](numpy/2.png)


```python
a = np.arange(25).reshape(5,5)
np.where(a%3==0, a, np.nan)
```




    array([[ 0., nan, nan,  3., nan],
           [nan,  6., nan, nan,  9.],
           [nan, nan, 12., nan, nan],
           [15., nan, nan, 18., nan],
           [nan, 21., nan, nan, 24.]])



![](numpy/3.png)

## Computations with arrays

**Rule 1** Operations between multiple array objects are first checked for proper shape match.  
**Rule 2** Mathematical operators apply element by element, on the value.  
**Rule 3** Reduction operations (mean, std, skew ...) apply to the whole array, unless an axis is specified.  
**Rule 2** Missing values propagate unless explicitly ignored (nanmean, nansum, ...)  

to 1:55:00
