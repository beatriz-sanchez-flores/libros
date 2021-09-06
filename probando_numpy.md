# NumPy


```python
import numpy as np
```

# NumPy Arrays

# Creating Arrays


```python
a = np.array([1,2,3])
print(a)
```

    [1 2 3]
    


```python
b = np.array([(1.5,2,3), (4,5,6)], dtype = float)
```


```python
c = np.array([[(1.5,2,3), (4,5,6)], [(3,2,1), (4,5,6)]],
 dtype = float)
```

# Initial Placeholders


```python
np.zeros((3,4)) 
```




    array([[0., 0., 0., 0.],
           [0., 0., 0., 0.],
           [0., 0., 0., 0.]])




```python
 np.ones((2,3,4),dtype=np.int16)
```




    array([[[1, 1, 1, 1],
            [1, 1, 1, 1],
            [1, 1, 1, 1]],
    
           [[1, 1, 1, 1],
            [1, 1, 1, 1],
            [1, 1, 1, 1]]], dtype=int16)




```python
d = np.arange(10,25,5)
```


```python
print(d)
```

    [10 15 20]
    


```python
np.linspace(0,2,9)
```




    array([0.  , 0.25, 0.5 , 0.75, 1.  , 1.25, 1.5 , 1.75, 2.  ])




```python
e = np.full((2,2),7)
print(e)
```

    [[7 7]
     [7 7]]
    


```python
f = np.eye(2)
print(f)
```

    [[1. 0.]
     [0. 1.]]
    


```python
np.random.random((2,2))
```




    array([[0.78229207, 0.8970311 ],
           [0.48335258, 0.02852144]])




```python
np.empty((3,2))
```




    array([[0., 0.],
           [0., 0.],
           [0., 0.]])



# Saving & Loading On Disk


```python
np.save('my_array', a)
```


```python
np.savez('array.npz', a, b)
```


```python
np.load('my_array.npy')
```




    array([1, 2, 3])



# Saving & Loading Text Files


```python
np.loadtxt("myfile.txt")
```




    array([1.23456789e+08, 1.23456780e+07, 1.23456700e+06])




```python
np.genfromtxt("my_file.csv", delimiter=',')
```




    array([1.23000e+02, 1.23400e+03, 1.23450e+04, 1.23456e+05])




```python
np.savetxt("myarray.txt", a, delimiter=" ")
```

# Data Types


```python
np.int64
```




    numpy.int64




```python
np.float32
```




    numpy.float32




```python
np.complex
```




    complex




```python
np.bool
```




    bool




```python
np.object
```




    object




```python
np.string_
```




    numpy.bytes_




```python
np.unicode_
```




    numpy.str_



# Inspecting Your Array


```python
a.shape
```




    (3,)




```python
len(a)
```




    3




```python
b.ndim
```




    2




```python
e.size
```




    4




```python
b.dtype
```




    dtype('float64')




```python
b.dtype.name
```




    'float64'




```python
b.astype(int)
```




    array([[1, 2, 3],
           [4, 5, 6]])



# Asking For Help


```python
np.info(np.ndarray.dtype)
```

    Data-type of the array's elements.
    
    Parameters
    ----------
    None
    
    Returns
    -------
    d : numpy dtype object
    
    See Also
    --------
    numpy.dtype
    
    Examples
    --------
    >>> x
    array([[0, 1],
           [2, 3]])
    >>> x.dtype
    dtype('int32')
    >>> type(x.dtype)
    <type 'numpy.dtype'>
    

# Arithmetic Operations


```python
g = a - b
```


```python
np.subtract(a,b)
```




    array([[-0.5,  0. ,  0. ],
           [-3. , -3. , -3. ]])




```python
np.subtract(a,b)
```




    array([[-0.5,  0. ,  0. ],
           [-3. , -3. , -3. ]])




```python
b + a
```




    array([[2.5, 4. , 6. ],
           [5. , 7. , 9. ]])




```python
np.add(b,a)
```




    array([[2.5, 4. , 6. ],
           [5. , 7. , 9. ]])




```python
a / b
```




    array([[0.66666667, 1.        , 1.        ],
           [0.25      , 0.4       , 0.5       ]])




```python
np.divide(a,b)
```




    array([[0.66666667, 1.        , 1.        ],
           [0.25      , 0.4       , 0.5       ]])




```python
a * b
```




    array([[ 1.5,  4. ,  9. ],
           [ 4. , 10. , 18. ]])




```python
np.multiply(a,b)
```




    array([[ 1.5,  4. ,  9. ],
           [ 4. , 10. , 18. ]])




```python
np.exp(b)
```




    array([[  4.48168907,   7.3890561 ,  20.08553692],
           [ 54.59815003, 148.4131591 , 403.42879349]])




```python
np.sqrt(b)
```




    array([[1.22474487, 1.41421356, 1.73205081],
           [2.        , 2.23606798, 2.44948974]])




```python
np.sin(a)
```




    array([0.84147098, 0.90929743, 0.14112001])




```python
np.cos(b)
```




    array([[ 0.0707372 , -0.41614684, -0.9899925 ],
           [-0.65364362,  0.28366219,  0.96017029]])




```python
np.log(a)
```




    array([0.        , 0.69314718, 1.09861229])




```python
e.dot(f)
```




    array([[7., 7.],
           [7., 7.]])



# Comparison


```python
a == b
```




    array([[False,  True,  True],
           [False, False, False]])




```python
a < 2
```




    array([ True, False, False])




```python
np.array_equal(a, b)
```




    False



# Aggregate Functions


```python
a.sum()
```




    6




```python
a.min()
```




    1




```python
b.max(axis=0)
```




    array([4., 5., 6.])




```python
b.cumsum(axis=1)
```




    array([[ 1.5,  3.5,  6.5],
           [ 4. ,  9. , 15. ]])




```python
a.mean()
```




    2.0




```python
np.median(b)
```




    3.5




```python
np.corrcoef(a)
```




    1.0




```python
np.std(b)
```




    1.5920810978785667



# Copying Arrays


```python
h = a.view()
```


```python
np.copy(a)
```




    array([1, 2, 3])




```python
h = a.copy()
```

# Sorting Arrays


```python
a.sort()
```


```python
c.sort(axis=0)
```

# Subsetting, Slicing, Indexing

### Subsetting


```python
a[2]
```




    3




```python
b[1,2]
```




    6.0



### Slicing


```python
a[0:2]
```




    array([1, 2])




```python
b[0:2,1]
```




    array([2., 5.])




```python
b[:1]
```




    array([[1.5, 2. , 3. ]])




```python
c[1,...]
```




    array([[3., 2., 3.],
           [4., 5., 6.]])




```python
a[ : :-1]
```




    array([3, 2, 1])



### Boolean Indexing


```python
a[a<2]
```




    array([1])



### Fancy Indexing


```python
b[[1, 0, 1, 0],[0, 1, 2, 0]]
```




    array([4. , 2. , 6. , 1.5])




```python
b[[1, 0, 1, 0]][:,[0,1,2,0]]
```




    array([[4. , 5. , 6. , 4. ],
           [1.5, 2. , 3. , 1.5],
           [4. , 5. , 6. , 4. ],
           [1.5, 2. , 3. , 1.5]])



# Array Manipulation

### Transposing Array


```python
i = np.transpose(b)
```


```python
i.T
```




    array([[1.5, 2. , 3. ],
           [4. , 5. , 6. ]])



### Changing Array Shape


```python
b.ravel()
```




    array([1.5, 2. , 3. , 4. , 5. , 6. ])




```python
g.reshape(3,-2)
```




    array([[-0.5,  0. ],
           [ 0. , -3. ],
           [-3. , -3. ]])



### Adding/Removing Elements


```python
h.resize((2,6))
```


```python
np.append(h,g)
```




    array([ 1. ,  2. ,  3. ,  0. ,  0. ,  0. ,  0. ,  0. ,  0. ,  0. ,  0. ,
            0. , -0.5,  0. ,  0. , -3. , -3. , -3. ])




```python
np.insert(a, 1, 5)
```




    array([1, 5, 2, 3])




```python
np.delete(a,[1])
```




    array([1, 3])



### Combining Arrays


```python
np.concatenate((a,d),axis=0)
```




    array([ 1,  2,  3, 10, 15, 20])




```python
np.vstack((a,b))
```




    array([[1. , 2. , 3. ],
           [1.5, 2. , 3. ],
           [4. , 5. , 6. ]])




```python
np.r_[e,f]
```




    array([[7., 7.],
           [7., 7.],
           [1., 0.],
           [0., 1.]])




```python
np.hstack((e,f))
```




    array([[7., 7., 1., 0.],
           [7., 7., 0., 1.]])




```python
np.column_stack((a,d))
```




    array([[ 1, 10],
           [ 2, 15],
           [ 3, 20]])




```python
np.column_stack((a,d))
```




    array([[ 1, 10],
           [ 2, 15],
           [ 3, 20]])




```python
np.c_[a,d]
```




    array([[ 1, 10],
           [ 2, 15],
           [ 3, 20]])



### Splitting Arrays


```python
np.hsplit(a,3)
```




    [array([1]), array([2]), array([3])]




```python
np.vsplit(c,2)
```




    [array([[[1.5, 2. , 1. ],
             [4. , 5. , 6. ]]]), array([[[3., 2., 3.],
             [4., 5., 6.]]])]


