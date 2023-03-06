# Numpy

Numpy is a library speialized in mathematical compuation with optimized C code.

### Documentation links:
- [User guide](https://numpy.org/doc/stable/user/index.html#user)
- [API Reference](https://numpy.org/doc/stable/reference/index.html#reference)
- [Source code](https://github.com/numpy/numpy)

## Syntax

### Array access

- One element:

```python
array[2] # Third element
array[-1] # Last element
```
- A range of elements:

```python
array[i:j:p] # i till j (excluded) using steps of p
array[:3] # all elements till the third 
array[3:] # all elements from the fourth
array[::-1] # start and end are reversed. Can be used to reverse a list
array[:, 6]
```

- Use conditions to acess elements

```python
array[array > 0] # Generate an array with only striclty positive values of array
array[(array > 0) & (array < 100) | (array == 6)] # Use & and | to create more complex conditions
```
---

## Create an array

- **np.array(list)**
- **np.zeros(n)**, **np.ones(n)**, **np.zeros((d1, d2))**
- **np.arange(i, j, p)**: fill the array with values from i to j with a step of p
- **np.linspace(i, j, n)**: fill te array with n values evenly spaced between i and j
- **np.random.randint((d1, d2))**, **np.random.randint(1, 10, n)**

---

## Array attributes/methods

- **dtype**: returns the type of an array ([Data types](https://numpy.org/doc/stable/user/basics.types.html))
- **shape**

```python
print(array.dtype)
print(array.shape)
```

- **mean**, **min**, **max**, ...: classical aggregation methods
- **argmin**, **argmax**: returns the index of min or max value

### modifiers
- **sort**
- **vstack**, **hstack**

```python
np.vstack((data, newLine))
```

[All Array manipulations](https://numpy.org/doc/stable/reference/routines.array-manipulation.html)

## Matrices

Compute with matrices:

- term-wise operations using +, - and *
- dot product: **A @ B** or **np.dot(A, B)**
