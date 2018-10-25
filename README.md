
# Numpy vs. Pure Python - Lab

## Introduction 

Numpy, Scipy and Pandas libraries provide a significant increase in computational efficiency with complex mathematical operations as compared to Python's built in arithmatic functions.  In this lab we shall calculate and compare the processing speed required for calculating a dot product both using basic arithmatic operations in Python and Numpy's `.dot()` method. 

## Objectives
You will be able to:
* Compare the performance of high dimensional matrix operations in Numpy vs. pure Python. 

## Problem
> **Write a routine to calculate the dot product between two 200 x 200 dimensional matrices using:**

> **a) Pure Python**

> **b) Numpy's `.dot()`**


### Create two 200 x 200 matrices in Python and fill them with random values using `np.random.rand()` 


```python
##### Compare 200x200 matrix-matrix multiplication speed
import numpy as np
# Set up the variables

SIZE = 200
A = np.random.rand(SIZE,SIZE)
B = np.random.rand(SIZE,SIZE)
```

### Pure Python

* Initialize an zeros filled numpy matrix with necessary rows and columns for storing result. 
* In Python Calculate the dot product using the formula 
![](formula.png)
* Use Python's `timeit` library to calculate the processing time. 
* [Visit this link](https://www.pythoncentral.io/time-a-python-function/) for an indepth explanation on how to time a function or routine in python. 

**Hint**: Use nested for loop for accessing, calculating and storing each scalar value in the result matrix.


```python
import timeit

# Start the timer
start = timeit.default_timer()

# Matrix multiplication in pure Python

out2 = np.zeros((SIZE,SIZE))

for i in range(SIZE):
  for j in range(SIZE):
    for k in range(SIZE):
      
        out2[i,k] += A[i,j]*B[j,k]

time_spent = timeit.default_timer() - start

print('Pure Python Time:', time_spent, 'sec.')
```

    Pure Python Time: 4.917119136007386 sec.


## Numpy 
Set the timer and calculate the time taken by `.dot()` function for multiplying A and B 



```python
# start the timer
start = timeit.default_timer()

# Matrix multiplication in numpy
out1 = A.dot(B)

time_spent = timeit.default_timer() - start
print('Numpy Time:', time_spent, 'sec.')
```

    Numpy Time: 0.001027324004098773 sec.


### Your comments 

```
Numpy is much faster than pure python 

NumPy provides support for large multidimensional arrays and matrices along with a collection of mathematical functions to operate on these elements. 

Numpy relies on well-known packages implemented in other languages (like Fortran) to perform efficient computations, bringing the user both the expressiveness of Python and a performance similar to MATLAB or Fortran.
```

## Summary

In this lab, we performed a quick comparison between calculating a dot product in numpy vs python built in function. We saw that Numpy is computationally much more efficient that Python code due to highly sophisticated implementation of Numpy source code. You are encouraged to always perform such tests to fully appreciate the use of an additional library in Python. 
