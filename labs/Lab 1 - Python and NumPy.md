---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**Lindsey Henry**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


What are some examples of magic commands and why would you use them? Which ones will be the most useful for this course? 
Are there any disadvantages to using Jupyter Notebook? 
Will we be using any Juptyer widgets for this class?


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = np.full((6,4), 2)
a
```

## Exercise 2

```python
b = np.full((6,4),1)
np.fill_diagonal(b, 3)
b
```

## Exercise 3

```python
a * b
print("a * b multiplies element by element") 
#np.dot(a,b)
print("np.dot(a,b) takes the dot product of the two matrices which requires the inner dimensions to match. ")
```

## Exercise 4

```python
np.dot(a.transpose(),b)
np.dot(a,b.transpose())
print("The result of matrix multiplication is always the outer dimensions of the matrices being multiplied.")
```

## Exercise 5

```python
def printingFunc():
    print("Something")
printingFunc()
```

## Exercise 6

```python
def randomStats():
    a = np.random.random_sample((1,5)) 
    print(a)
    print("sum: " + str(np.sum(a)))
    print("mean: " + str(np.mean(a)))
    print("")
    
randomStats()
randomStats()
randomStats()
```

## Exercise 7

```python
c = np.full((2,15), 1)

def numOnesLoop(a):
    count = 0
    for i in range(a.shape[0]):
        for j in range(a.shape[1]):
            if a[i,j] == 1:
                count += 1
    return count

print(numOnesLoop(c))


def numOnesWhere(a):
    b = np.where(a==1)
    return a[b].size
numOnesWhere(c)
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
adf = pd.DataFrame(np.ones((6,4))*2)
adf
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = np.full((6,4),1)
np.fill_diagonal(b, 3)
bdf = pd.DataFrame(b)
bdf
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
adf*bdf
print(" adf*bdf works because this just multiplies elements that align. ")
print(" adf.dot(bdf) does not work because it takes the mathematical dot product which requires outer dimensions to align in order to work. ")
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# Write a function that consists of a set of loops that run through an array and count the number of ones in it. 
#Do the same thing using the where() function (use info(where) to find out how to use it).
c =  pd.DataFrame(np.ones((6,4)))

def numOnesLoop(a):
    count = 0
    for i in range(a.shape[0]):
        for j in range(a.shape[1]):
            if a.iloc[i,j] == 1:
                count += 1
    return count

print(numOnesLoop(c))


def numOnesWhere(a):
    b = a.where(a==1)
    return sum(b.count())
numOnesWhere(c)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace = True)
titanic_df
```

```python

```

```python

```
