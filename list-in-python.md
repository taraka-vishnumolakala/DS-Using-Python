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

### average of a list

```python
def average_list(list):
    return sum(list)/len(list)
```

### separate even and odd

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

### get smaller elements

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

### largest element in a list

```python
def getLargestNumber(list_1):
    max = list_1[0]
    for i in range(1, len(list_1)):
        if(list_1[i] > max):
            max = list_1[i]
    return max

print(getLargestNumber([10,5,20,8]))
```

### Second largest element in a list

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



