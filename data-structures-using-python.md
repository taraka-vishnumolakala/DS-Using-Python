# Data Structures Using Python

## Module 1

### Analysis of Algorithms

#### Order of Growth

- How do we know which terms are lower order ?

  - Using the below order of terms we have a direct way of time complexity of algorithms

    **constant < loglogn < logn < n^1/3 < n^1/2 < n < n^2 < n^3 < n^4 < 2^n < n^n** 

  - Ignore lower order terms

  - Ignore leading constants

- Consider the below example and give a justification as to why f(n) is a bad algorithm

  ```basic
  f(n) = c1n^2 + c3n + c4
  g(n) = c5nlogn + c6n + c7
  
  Step-1: Ignore lower order terms
  f(n) = n^2
  g(n) = nlogn
  
  Now, after cancelling out the common "n" between both the algorithms we have "f(n)=n" and "g(n)=logn"
  We can clearly say that g(n) takes less time compared to f(n)
  ```

#### Best, Average and Worst Cases

- Asymptotic Notations
  - **Big O** represents exact or upper bound --> Worst Case ??
  - **Theta** represents exact bound
  - **Omega** represents exact or lower bound --> Best Case ??

#### Big O Notation

#### Omega Notation

#### Theta Notation

#### Analysis of Common Loops

#### Analysis of Recursion

#### Space Complexity

