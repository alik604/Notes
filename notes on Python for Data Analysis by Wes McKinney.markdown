### chpt 1: why python
"Part of Python’s success in scientific computing is the ease of integrating C, C++, and
FORTRAN code. Most modern computing environments share a similar set of legacy
FORTRAN and C libraries for doing linear algebra, optimization, integration, fast
Fourier transforms, and other such algorithms."

* why not just have interns rewrite these archaic libraries into python. python might be slower than C++ but I doubt the middling manning is fast

#### 1.3 Essential Python Libraries
* NumPy, short for Numerical Python, has long been a cornerstone of numerical com‐
puting in Python. It provides the data structures, algorithms, and library glue needed
for most scientific applications involving numerical data in Python.

* pandas provides high-level data structures and functions designed to make working
with structured or tabular data fast, easy, and expressive. It enables Python to be a powerful and productive data analysis environment. The primary objects in pandas that will be used in this book are the DataFrame,
a tabular, column-oriented data structure with both row and column labels, and the
*Series*, a one-dimensional labeled array object.

* matplotlib is the most popular Python library for producing plots and other two-dimensional data visualizations.

* SciPy is a collection of packages addressing a number of different standard problem
domains in scientific computing.
    ^^ im going to love scipy.optimize & scipy.integrate :)   wonder if ill being using this the most then i start Machine learning

* scikit-learn
Since the project’s inception in 2010, scikit-learn has become the premier general purpose machine learning toolkit for Python programmers.

      * Classification: SVM, nearest neighbors, random forest, logistic regression, etc.
      * Regression: Lasso, ridge regression, etc.
      * Clustering: k-means, spectral clustering, etc.
      * Dimensionality reduction: PCA, feature selection, matrix factorization, etc.
      * Model selection: Grid search, cross-validation, metrics
      * Preprocessing: Feature extraction, normalization

### chpt 2: Python Language Basics
[my fav TL;DR video](https://www.youtube.com/watch?v=N4mEzFDjqtA)

* a // b Floor-divide a by b, dropping any fractional remainder
* a ** b Raise a to the b power
* a is b True if a and b reference the same Python object
* a is not b True if a and b reference diﬀerent Python objects

* datetime is an important OBJ. I will likely forget its name

`pass` is like `continue` from java

Ternary in python
``** 'Non-negative' if x >= 0 else 'Negative' **``



### chpt 3: Built-in Data Structures, Functions, and Files

* Tuple is a fixed-length, immutable sequence of Python objects. The easiest way to
create one is with a comma-separated sequence of values

* List In contrast with tuples, lists are variable-length and their contents can be modified
in-place. You can define them using square brackets [] or using the list type function
  * lists work well with set theory... good thing I paid attention back in MACM 101


returning multiple values

    def f():
      a = 5
      b = 6
      c = 7
      return a, b, c

    a, b, c = f()

dam I wish JS had this. nice way to confuse a code reviewer

#### functions as objects

    import re

    def clean_strings(strings):
      result = []
      for value in strings:
          value = value.strip()
          value = re.sub('[!#?]', '', value)
          value = value.title()
          result.append(value)
        return result

    In [173]: clean_strings(states)
    Out[173]:
    ['Alabama',
    'Georgia',
    'Georgia',
    'Georgia',
    'Florida',
    'South Carolina',
    'West Virginia']


#### functions as parameter

    def apply_to_list(some_list, f):
      return [f(x) for x in some_list]

    ints = [4, 0, 1, 5, 6]
    apply_to_list(ints, lambda x: x * 2)


#### Currying

Currying is computer science jargon (named after the mathematician Haskell Curry)
that means deriving new functions from existing ones by partial argument applica‐
tion. For example, suppose we had a trivial function that adds two numbers together:
      def add_numbers(x, y):
        return x + y

Using this function, we could derive a new function of one variable, add_five, that
adds 5 to its argument:

      add_five = lambda y: add_numbers(5, y)
The second argument to add_numbers is said to be curried. There’s nothing very fancy
here


#### Generators //TODO... ya java comments in python notes


#### Exceptions

    f = open(path, 'w')
    try:
      write_to_file(f)
    except:
      print('Failed')
    else:
      print('Succeeded')
    finally:
      f.close()

#### 3.3 Files and the Operating System
##### omit cuz im lazy ( ill have to use google for this anyways)





### cmpt 4: NumPy Basics

#### 2d array

    data2 = [[1, 2, 3, 4], [5, 6, 7, 8]]
     arr2 = np.array(data2)
     # 2*4 matrix

#### indexing and slicing

    Out[61]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
    In [63]: arr[5:8]
    Out[63]: array([5, 6, 7])

    In [66]: arr_slice = arr[5:8]
    In [68]: arr_slice[1] = 12345
    In [69]: arr
    Out[69]: array([ 0, 1, 2, 3, 4, 12, 12345, 12, 8, 9])

    In [70]: arr_slice[:] = 64
    In [71]: arr
    Out[71]: array([ 0, 1, 2, 3, 4, 64, 64, 64, 8, 9])


#### 3d array

    In [74]: arr2d[0][2]
    Out[74]: 3
    In [75]: arr2d[0, 2]
    Out[75]: 3
    # same thing?

    arr2d[:2]
    #outputs first 2 rows

    arr2d[:2, 1:]
    # end at 2nd row, start at 1st column

![](matrixSlice.png)

#### boolean indexing //TODO

#### fancy indexing

      In [119]: arr
      Out[119]:
      array([[ 0., 0., 0., 0.],
            [ 1., 1., 1., 1.],
            [ 2., 2., 2., 2.],
            [ 3., 3., 3., 3.],
            [ 4., 4., 4., 4.],
            [ 5., 5., 5., 5.],
            [ 6., 6., 6., 6.],
            [ 7., 7., 7., 7.]])
To select out a subset of the rows in a particular order, you can simply pass a list or ndarray of integers specifying the desired order:

          In [120]: arr[[4, 3, 0, 6]]
          Out[120]:
          array([[ 4., 4., 4., 4.],
                [ 3., 3., 3., 3.],
                [ 0., 0., 0., 0.],
                [ 6., 6., 6., 6.]])


#### 4.3 Array-Oriented Programming with Arrays pg 108 //TODO


#### 4.4 File Input and Output with Arrays

* NumPy to load and save arrays with .npy format
* multiple arrays in dictionary like formate in a .npz
        In [217]: arch = np.load('array_archive.npz')
        In [218]: arch['b']
        Out[218]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



#### 4.5 Linear Algebra

title says it all


#### 4.6 Pseudorandom Number Generation

TL;DR use NumPy for random number generation



### chpt: 5 pandas

[pandas cheat sheet](https://github.com/pandas-dev/pandas/blob/master/doc/cheatsheet/Pandas_Cheat_Sheet.pdf)

[pandas cheat sheet 2](https://www.dataquest.io/blog/large_files/pandas-cheat-sheet.pdf)



