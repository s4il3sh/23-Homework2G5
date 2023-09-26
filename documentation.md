---
jupyter:
  colab:
    authorship_tag: ABX9TyPX1CuTZHq4AMnftGG0mIrP
    include_colab_link: true
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

::: {.cell .markdown colab_type="text" id="view-in-github"}
`<a href="https://colab.research.google.com/github/yasmensarhan27/23-Homework2G5/blob/yasmensarhan27-patch-2/documentation_inner_outer_product.ipynb" target="_parent">`{=html}`<img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>`{=html}`</a>`{=html}
:::

::: {.cell .code id="fiFn9jhHfKca"}
``` python

```
:::

::: {.cell .markdown id="SXAyhfGQfaUI"}
\#**Documentation:**

\##**Overview**

\###**The Inner Product function:** The inner product is calculated by
multiplying the corresponding elements of the two vectors and summing
the results. The inner product of 2 vectors **a** and **b** =

\#**\$ \\sum\_{i=0}\^{n} a\_{i} b\_{i}\$**

The **inner_product()** function can be used to calculate the inner
product of any two vectors of the same length.

The inner product is a scalar value that represents the similarity
between the two vectors.

#### **Input or Arguments**

The function takes two vectors as input. The vectors must be of the same
length.

\####**Output** The function returns the inner product of the two
vectors.

\###**The outer prouct function:**

The outer product is a matrix that is formed by multiplying the
corresponding elements of the two vectors and storing the results in the
corresponding elements of the matrix. The **outer_product()** function
can be used to calculate the outer product of any two vectors of any
length.

The outer product of a and b can be represented by:

\#**\$ \\sum\_{i=0,j=0}\^{n} a\_{i} b\_{j} \$**

#### **Input or Arguments**

The function takes two vectors as input.

\####**Output** The function returns a matrix that is the outer product
of the two vectors. The matrix will have dimensions \\begin{matrix}
(len(a), len(b)) \\end{matrix} where a and b are the two input vectors.

Sources: [Stover, Christopher and Weisstein, Eric W. \"Einstein
Summation.\" From MathWorld\--A Wolfram Web
Resource.](https://mathworld.wolfram.com/EinsteinSummation.html)

Source: [EINSTEIN SUMMATION
NOTATION](http://dslavsk.sites.luc.edu/courses/phys301/classnotes/einsteinsummationnotation.pdf)

Source: [NumPy
reference](https://numpy.org/doc/stable/reference/index.html)
:::

::: {.cell .markdown id="kEuDqh-wfYIW"}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="fWmZeb7BQnk_" outputId="366d3651-7197-4efb-c5d3-2a227f7376b2"}
``` python
#Python Code for inner and outer product
import numpy as np
def inner_product(a, b):
  def outer_product(a, b):


   """
   This Code Calculates the inner and outer product of two vectors using for loop.


   Args:
    a:   array representing the first vector.
    b:   array representing the second vector.

   Returns:
    The inner product of the two vectors.
    A numpy array representing the outer product of the two vectors.

   """

#Add 2 vectors a and b as arrays
a=[2,3,4]
b=[1,2,5]
#condition of inner product that return error if a and b are not of the same length
if len(a) != len(b):
  raise ValueError("The two vectors must be of the same length.")
#create variable inner_product of initial value zero
inner_product = 0
#apply for loop to calculate the inner product and return its value to the inner_product variable created obove
for i in range(len(a)):
  inner_product += a[i] * b[i]
# print the value of the inner product
print("inner product: ",inner_product)

# create (length of a x length of b) matrix for the outer product that has elements equal zero.
outer_product = np.zeros((len(a), len(b)))
#apply for loop to calculate the outer product and return its matrix to the outer_product matrix created
for i in range(len(a)):
  for j in range(len(b)):
    outer_product[i, j] = a[i] * b[j]
#print the outer product matrix
print("outer product: ",outer_product)

#Calculating the time of calculating the inner product using for loop
print("time of calculating inner product using for loop = ")
%%timeit
inner_product = 0
for i in range(len(a)):
  inner_product += a[i] * b[i]

#Calculating the time of calculating the outer product using for loop
print("time of calculating outer product using for loop = ")
%%timeit
outer_product = np.zeros((len(a), len(b)))
for i in range(len(a)):
  for j in range(len(b)):
    outer_product[i, j] = a[i] * b[j]
```

::: {.output .stream .stdout}
    inner product:  28
    outer product:  [[ 2.  4. 10.]
     [ 3.  6. 15.]
     [ 4.  8. 20.]]
    time of calculating inner product using for loop = 
:::

::: {.output .stream .stderr}
    UsageError: Line magic function `%%timeit` not found.
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="17S65Rz9R1jx" outputId="021a3cc3-23db-4de5-d762-effe1029a947"}
``` python
import numpy as np
"""
This Code Calculates the inner and outer product of two vectors using numpy built in functions
Args:
a:  NumPy array representing the first vector.
b:  NumPy array representing the second vector.
Returns:
    The inner product of the two vectors.
    A numpy array representing the outer product of the two vectors.

"""
# Create two vectors
a = np.array([2,3,4])
b = np.array([1,2,5])

# Create a new matrix of zeros with the same dimensions as the outer product
outer_product = np.zeros((len(a), len(b)))
#use numpy built in fuction to calculate the outer product
outer_product = np.outer(a,b)
#print the outer product
print("outer Product of a and b is: ", outer_product)

#use numpy builtin function to calculate the inner product
inner_product=np.inner(a,b)
# Print the inner product
print("Inner Product of a and b is: ",inner_product)

#Calculating the time of calculating the inner product using numpy
print("time of calculating inner product using numpy = ")
%timeit np.inner(a,b)

#Calculating the time of calculating the outer product using numpy
print("time of calculating outer product using numpy = ")
%timeit np.outer(a,b)
```

::: {.output .stream .stdout}
    outer Product of a and b is:  [[ 2  4 10]
     [ 3  6 15]
     [ 4  8 20]]
    Inner Product of a and b is:  28
    time of calculating inner product using numpy = 
    1.77 µs ± 74.7 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
    time of calculating outer product using numpy = 
    2.94 µs ± 75.9 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="Hj4n21Phdg5v" outputId="1899e040-972d-4206-f4c8-992625a8215c"}
``` python
#use einsum
import numpy as np
"""
This Code Calculates the inner and outer product of two vectors using numpy built in einsum function
Args:
a:  NumPy array representing the first vector.
b:  NumPy array representing the second vector.
Returns:
    The inner product of the two vectors.
    A numpy array representing the outer product of the two vectors.

"""
# Create two vectors: a and b. Each vector has three elements
a = np.array([2,3,4])
b = np.array([1,2,5])

# Calculate the inner product using Einstein notation
inner_product = np.einsum('i,i', a, b)

# Calculate the outer product using Einstein notation
outer_product = np.einsum('i,j', a, b)

# Print the outer product
print("outer product=", outer_product)

# Print the inner product
print("inner product= ", inner_product)

#Calculating the time of calculating the inner product using eisnum
print("time of calculating inner product using einsum = ")
%timeit np.einsum('i,i', a, b)

#Calculating the time of calculating the outer product using eisnum
print("time of calculating outer product using einsum = ")
%timeit np.einsum('i,j', a, b)
```

::: {.output .stream .stdout}
    outer product= [[ 2  4 10]
     [ 3  6 15]
     [ 4  8 20]]
    inner product=  28
    time of calculating inner product using einsum = 
    2.67 µs ± 69.9 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
    time of calculating outer product using einsum = 
    2.77 µs ± 71.5 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
:::
:::

::: {.cell .code id="BkgmIImpblw8"}
``` python
```
:::
