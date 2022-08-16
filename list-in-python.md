# List in Python

- List in python is a collections of items which **allows items of <u>DIFFERENT</u> types**. 

- Explain each function mentioned below:

  ```python
  list = [10,20,30,40,50]
  list.append(value)
  list.insert(index, value)
  print(value in list)
  print(list.count(value))
  print(list.index(value))
  print(list.index(value, start_index, end_index))
  list.remove(value)
  list.pop()
  list.pop(index)
  del list[index]
  del list[start_index:end_index]
  max(list)
  min(list)
  sum(list)
  list.reverse()
  list.sort()
  sorted_list = sorted(list)
  ```

- **Advantages** of list:

  - **Random access** --> get the value using an index in constant time.
  - **Cache Friendly** --> usually computers/processors fetch the item and any reference values and load them to the cache. Since, list is stored in contiguous memory locations it is likely possible that all the values are loaded into the cache which reduces the time to fetch data.

- **Disadvantages** of list:

  - **Insertion, Deletion are slow** --> inserting/deleting an element at an index value takes linear time to move other referenced values to the next contiguous locations. 
  - **Search operation is also slow** --> takes linear time to search for an element since it has to traverse through all the n elements. 

- **How does dynamic size work ?**

  - Pre-allocate some extra space during the initialization.
  - If the list becomes full, do the following
    - Allow a new space of larger size (multiply by x which is **1.5** for python. value of x varies by programming language)
    - Copy old values to the newly allocated space.
    - De-allocate the old referenced memory locations for the values.

**NOTE: So, based on how the dynamic sizing works time complexity of insertion increases every time the size of list has to be increased.**

## slicing (list, tuple, and string)

- slicing in python follows the syntax **list[start:stop:step]**
- we can also use negative value for step but remember that start should be a higher index value and stop should be lower index value when using negative integer for step.

## Problems

#### average of a list

```python
def average_list(list):
    return sum(list)/len(list)
```

#### separate even and odd

```python
def evenAndOdd(list):
    even = []
    odd = []
    for i in list:
        if(i%2 == 0):
            even.append(i)
        else:
            odd.append(i)
    return even,odd

e,o = evenAndOdd([10,20,30,40,50,60,70])
print(e)
print(o)
```

#### get smaller elements

```python
def getSmallerElements(list, n):
    smaller = []
    for i in list:
        if(i<n):
            smaller.append(i)
     return smaller

print(getSmallerElements([10,20,30,40,50,60,70,80]), 65)
```

Alternatively, we can also use comprehensions.

```python
def getSmallerElements(list, n):
    return [smaller for smaller in list if(smaller < n)]

print(getSmallerElements([10,20,30,40,50,60,70,80]), 65)
```

#### largest element in a list

```python
def getLargestNumber(list_1):
    max = list_1[0]
    for i in range(1, len(list_1)):
        if(list_1[i] > max):
            max = list_1[i]
    return max

print(getLargestNumber([10,5,20,8]))
```

#### Second largest element in a list

```python
def getSecondLargest(list_1):
    if len(list_1) <= 1:
        return None
    largest = list_1[0]
    second_largest = None
    for i in list_1[1:]:
        if(i > largest):
            second_largest = largest
            largest = i
        elif i != largest:
            if second_largest == None or second_largest < i:
                second_largest = i
    return second_largest

list_1 = [5,20,12,10,20,12,10]
print(list_1)
# [5, 20, 12, 10, 20, 12, 10]
getSecondLargest(list_1)
# 12
```

#### check if a list is sorted

```python
def isSorted(list_1):
    if len(list_1) == 0:
        return None
    else:
        start = 0
        end = start + 1
        for i in range(0, len(list_1)-1):
            if(list_1[start] > list_1[end]):
                return False
            else:
                start+=1
                end+=1
    return True
```

#### find the only odd

```python
def getOddRepetition(list_1):
    if len(list_1) == 0:
        return None
    else:
        current = list_1[0]
        repeated = 1
        for i in list_1[1:]:
            if repeated%2 != 0 and current != i:
                return current
            elif current == i:
                repeated+=1
            else:
                repeated = 1
                current = i
                
list_2 = [10,30,30,10,30,30,20]
sorted_list = sorted(list_2)
sorted_list
# [10, 10, 20, 30, 30, 30, 30]
getOddRepetition(sorted_list)
# 20
```

A much simpler solution:

```python
def getOddRepetition(list_1):
    for i in list_1:
        if list_1.count(i)%2 != 0:
            return i

list_2 = [10,30,30,10,30,30,20]
sorted_list = sorted(list_2)
sorted_list
# [10, 10, 20, 30, 30, 30, 30]   
getOddRepetition(sorted_list)
# 20
getOddRepetition(list_2)
# 20
```

#### reverse a list in python

```python
def reverseList(list_1):
    if len(list_1) == 0:
        return None
    else:
        end = len(list_1)-1
        start = 0
        while start < end:
            list_1[start], list_1[end] = list_1[end], list_1[start] 
            start += 1
            end -= 1
    return list_1

list_1 = [10, 20, 'geeks', 30, 'for', 40, 'geeks']
getReversedList(list_1)
# ['geeks', 40, 'for', 30, 'geeks', 20, 10]
```

Alternative methods:

```python
list_1 = [10, 20, 'geeks', 30, 'for', 40, 'geeks']
list_2 = list(reversed(list_1))
list_3 = list_1[::-1]
list_1.reverse()
```

#### left rotate a list by one

```python
def rotate_list(list_1):
    if len(list_1) == 0:
        return None
    else:
        start_element=list_1[0]
        for i in range(0,len(list_1)-1):
            list_1[i] = list_1[i+1]
        list_1[len(list_1)-1] = start_element
    return list_1

rotate_list([1,2,3,4,5,6])
# [2, 3, 4, 5, 6, 1]
```

Alternative methods:

```python
list_1 = [1,2,3,4,5]
list_1[1:] + list_1[0:1]
# [2, 3, 4, 5, 1]
list_1.append(list_1.pop(0))
list_1
# [2, 3, 4, 5, 1]
```

#### left rotate a list by d places

- A solution that works in **O(n)** would be
  - reverse elements from 0 to d-1
  - reverse elements from d to n-1
  - reverse the whole list 0 to n-1

```python
l = [1,2,3,4,5]
d = 3
def reverse(l, start, end):
    while start<end:
        l[start],l[end] = l[end], l[start]
        start += 1
        end -= 1       
def leftRotate(l, d):
    n = len(l)
    reverse(l, 0, d-1)
    reverse(l, d, n-1)
    reverse(l, 0, n-1)

leftRotate(l,d)
l
# [4, 5, 1, 2, 3]
```

Alternative methods:

```python
list_1 = [1,2,3,4,5]
list_1[r:] + list_1[:r]
# [3, 4, 5, 1, 2]
```

```python
def leftrotate(list_1,d):
    for i in range(0,d):
        list_1.appent(list_1.pop(0))
```

#### sliding window technique

- Find the maximum sum of K consecutive elements

```python
def maxSubArray(l, k):
    start, end, maxSum, currentMax = 0, 0, 0, 0
    while end <= len(l)-1:    
        if end-start <= k-1:
            currentMax += l[end]
            end += 1
        else:
            print(currentMax, sep='/', end=' ')
            currentMax -= l[start]
            start += 1
            
	maxSum = max(currentMax, maxSum)
    return maxSum

l = [1,8,30,-5,20,7]
maxSubArray(l,3)
# 39 33 45 45
```

Alternative implementation of sliding window technique

```python
def kMaxSum(l, k):
    current=0
    for i in range(k):
        current+=l[i]
    maxSum = current
    for i in range(k,len(l)):
        current = current+l[i]-l[i-k]
        maxSum = max(maxSum, current)
    return maxSum
```

#### subarray with given sum

```python
def findSubArrayWithGivenSum(l,s):
    current, start, end = 0, 0, 0
    for i in range(len(l)):
        current += l[i]
        while current > s:
            current -= l[start]
            start += 1
        if current == s:
            end = i
            break
    return l[start:end+1]

l = [1,4,20,3,10,5]
s = 33
findSubArrayWithGivenSum(l,s)
# [20, 3, 10]
```

