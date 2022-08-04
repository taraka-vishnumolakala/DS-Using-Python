# Python Programming Foundation

## Python Basics

- Compiler Vs Interpreter 
  - Compiler takes the whole chunk of code and converts it to binary or low level language that the machine can understand  and then executes it. 
  - Interpreter on the other hand converts the code line by line and executes it.
- How are python programs executed ?
  - Write code and save it as a `.py` file --> Compile and convert it platform independent intermediate byte code --> Interpreter now reads the intermediate binary code line by line and executes it.
- Python doesn't have any primitive types unlike java or c++. Any variable declared in python creates an object behind the scenes. 

## Variables and Data Types

- Swapping variables in python

  ```python
  x = 100
  y = 200
  x,y = y,x
  ```

- What is **id()** function in python ?

  - `id(variable)` returns a unique identifier for each memory address reference of a value.

- What is **type()** function in python ?

  - `type(variable)` returns the type of a variable which is automatically assigned by python.

- Different types in python

  ```python
  # string
  strVal = 'GeeksForGeeks'
  # list - mutable (values can be modified)
  listValues = [10,20,30]
  # tuple - immutable (cannot be modified)
  tupleValues = (10,20,30)
  # set - All values are distinct
  setValues = {10,20,30}
  # dict - map
  dictValues = {10:'Geeks', 20:'For', 30:'Geeks'}
  ```

### List Introduction []

- Retriving values from a list

  ```python
  listValues = [10,20,30,40,50]
  print(listValues) # [10,20,30,40,50]
  print(listValues[3]) # 40
  print(listValues[-1]) # 50
  
  # [10 20 30 40 50]
  # [0   1  2  3  4] index values
  # [-5 -4 -3 -2 -1] index values
  ```

- Consider another example on list

  ```python
  values = [10, 20, 30, 40, 50]
  values.append(30) # [10, 20, 30, 40, 50, 30]
  values.insert(1, 15) # [10, 15, 20, 30, 40, 50, 30]
  15 in values # True
  values.count(30) # 2 --> since 30 is repeated two times
  values.index(30) # 3 --> since 30 appears first at index 3
  values.index(30,4,7) # 6 --> since 30 appears at index 6 between indexes 4 - 7
  ```

- Another example on list to remove values:

  ```python
  values = [10,20,30,40,50,60,70,80]
  values.remove(20) # [10,30,40,50,60,70,80]
  values.pop() # 80 --> since it removes the last value from the list and returns the value
  values.pop(2) # 40 --> since we passed the index value of the list our pop function removed value 40 which is index 2 and returned the value. Our new list after our last two pop operations [10,30,50,60,70]
  del values[1] # [10,50,60,70] --> returns a list after deleting the value at index 1
  del values[0:2] # [60,70] --> returns a list after deleting values from start index to end-1 index
  ```

-  Other general purpose functions in python

  ```python
  values = [10,40,20,50]
  max(values) # 50 --> since 50 is the highest value in our list
  min(values) # 10 --> since 10 is the lowest value in our list
  sum(values) # 120
  values.reverse() # [50,20,40,10]
  values.sort() # [10,20,40,50]
  ```

### Tuples in Python ()

- Tuples in python are similar to list expect that they are immutable. 
- **Advantage of tuples** faster than list.

### Set in Python {}

- **Set doesn't maintain the order of insertion.** 

- Set doesn't have indexing unlike list or tuple.

- Advantages of set over a list are finding union, intersection, set difference of two or more sets. This is possible because set uses **hashing internally** which makes the search operation easier and faster.

- **How to create an empty set in python ?**

  ```python
  isSet = {}
  type(isSet) # <class,'dict'> --> when using curly braces with no values python creates a dict instead of a set
  emptySet = set()
  type(emptySet) # <class, 'set'> --> Empty set can be created by calling the set constructor method
  ```

- **Updating an existing set by passing one or more list**

  ```python
  exampleSet = {10,20}
  exampleSet.update([40,50]) # {40,10,50,20} --> set doesn't maintain the insertion order
  exampleSet.update([60,70],[80,90]) # {10,20,40,50,60,70,80,90}
  ```

- **What is difference between discard and remove ?**

  ```python
  setVals = {10,30,20,40}
  setVals.discard(50) # checks if 50 is present in the set and removes if present. doesn't throw any error if not present
  setVals.remove(50) # throws an error if the specified value is not present in set.
  ```

- **what is the difference between `del` vs `clear` ?**

  ```python
  setVals = {10,20,30,50,40,90}
  setVals.clear() # clears the values from the set but the setVals can be still be accessed and will be an empty set
  del setVals # delete the values and the varaible reference as well. After this setVals cannot be accessed.
  ```

- **Python operations on two sets**

  ```python
  set1 = {2,4,6,8}
  set2 = {3,6,9}
  print(set1|set2) # {2,3,4,6,8,9} --> union operation. We can also do set1.union(set2)
  print(set1&set2) # {6} --> intersection operation. We can also do set1.intersection(set2)
  print(set1-set2) # {2,4,8} --> minus operation. Elements present in set1 but not in set2. We can also do set1.difference(set2)
  print(set1^set2) # {2,3,4,8,9} --> symmetric difference. Elements present in both set1 and set2 eliminating the common elements.
  ```

- **More operations on sets**

  ```python
  set1 = {2,4,6,8}
  set2 = {4,8}
  print(set1.disjoint(set2)) # False --> Returns true only if there are no common elements between the two sets
  print(set1<=set2) # False --> Returns true only if set1 is a subset of set2
  print(set1<set2) # False --> Returns true only if set1 is a proper subset of set2
  print(set1>=set2) # True --> since set1 is superset of set2
  print(set1>set2) # True --> since set1 is a proper superset of set 2
  ```

### Dictionary in Python {}

- **Creating a dictionary and adding values**

  ```python
  dictVals = {}
  dictVals['laptop'] = 4000
  dictVals['mobile'] = 15000
  print(dictVals) # {'laptop':4000, 'mobile':15000}
  print(dictVals['mobile']) # 15000
  print(dictVals.get('mobile')) # 15000
  print(dictVals.get('iphone')) # None
  print(dictVals.get('iphone','Couldnot find')) # Couldnot find
  print(dictVals.['iphone']) # throws and error since the key is not found
  ```

- **Deleting values from dictionary**

  ```python
  dictVals = {}
  dictVals['laptop'] = 4000
  dictVals['mobile'] = 15000
  dictVals['iphone'] = 75000
  print(dictVals) # {'laptop':4000, 'mobile':15000, 'iphone':75000}
  print(dictVals.pop('iphone')) # 75000 --> deletes the key and returns the deleted value
  del dictVals['mobile'] # returns nothing unlike pop. Silently deletes the key value
  print(dictVals.popitem()) # deletes the last inserted item from the dictionary
  ```

### Type Conversion in Python

- Implicit type conversion

  - Examples:

    ```python
    a = 10
    b = 11.5
    c = a+b
    print(c) # 11.5 with a type of float
    
    d=True
    e=a+d 
    print(e) # 11 --> True is implicitly converted to 1 and the result is 10+1 = 11
    ```

- Explicit type conversion

  - Example:

    ```python
    s = "135"
    i = 10+int(s)
    f = float(s)
    print(i) # 145
    print(f) # 135.0
    ```

  - Other examples of explicit type conversion

    ```python
    s = 'GEEKS'
    print(list(s)) # ['G','E','E','K','S']
    print(tuple(s)) # ('G','E','E','K','S')
    print(set(s)) # {'S','G','K','E'}
    ```

  - Converting int to binary, hex, oct

    ```python
    a = 20
    print(bin(a)) # 0b10100
    print(hex(a)) # 0x14
    print(oct(a)) # 0o24
    ```

## Input and Output in Python

### print()

- `end` and `sep` options with print function

  - By default end is set to new line and sep is set to space unless specifically mentioned by the user.

  ```python
  print('GEEKS', end=' ')
  print('FOR GEEKS')
  print('07','24','2022',sep='/')
  print(10,20,30,sep='-',end=' ')
  print(40,50)
  ```

  Output:

  ```basic
  GEEKS FOR GEEKS
  07/24/2022
  10-20-30 40 50
  ```

## Operators

### Arithmetic Operators

- What is the difference between division **(/)** and floor **(//)** ?

  - Division returns a float with numbers after the decimal point where as floor rounds off the number and returns an integer.

    ```python
    print(9/4) # 2.25
    print(9//4) # 2
    ```

- How to return power of something ?

  ```python
  print(9**4) # 9 power of 4 --> 6561
  ```

- Order of precedence:

  ```basic
  ** --> power has highest precendence
  * / // --> multiplication and division has second highest precendence 
  + - --> Least precedence
  ```

- **Floating point numbers require higher number of bits to store the numbers and also, the division operator is not reliable when dealing with large numbers. It's ideal to use floor operator when dividing large numbers**

### Logical Operators

- `and`, `or`, `not`

- **Ternary operation in python**

  ```python
  s1 = ""
  s2 = s1 or "DefaultValue"
  print(s2) # DefaultValue
  ```

  - Line two in the above code says if s1 is empty then assign "DefaultValue" to string s2 if not assign s1.
  - We can also do the same with list, tuple, dictionary, set, etc.

- Logical operators also consider any non-zero values as true and all zero values are treated as false.

  ```python
  x = 10
  print(x or 20) # 20 --> x is evaluated as true. Since 20 is the last evaluated value our output will be 20
  y = 0
  print(y or 30) # 30 --> y is considered false and 30 is our last evaluated value.
  z = 40
  print(z and 50) # 50 --> z is considered true and 50 is our last evaluated value.
  ```

### Identity Comparison

- `is` and `isnot`

- **is** compared the id values are returns true only if they match. **id** is the memory location where the object is stored.

- **is not** returns a negation of **is**.

  ```python
  x = 10
  y = x
  print(x is y) # True
  print(x is not y) # false
  ```

  Other examples:

  ```python
  x1 = 10
  x2 = 10
  z1 = "GeeksForGeeks"
  z2 = "GeeksForGeeks"
  print(x1 is x2) # True
  print(z1 is z2) # True
  ```

  - Python stores values to the same memory location if they have the same value. **This is not true for lists, sets, tuples, etc.**

### Membership Test

- `in` and `not in`

  ```python
  s = "GeeksForGeeks"
  print("G" in s) # True --> in checks for substring in a string
  
  d = {10:"abc", 20:"efg"}
  print(10 in d) # True
  print(15 in d) # False
  
  l = [10,20,30,15]
  print(30 in l) # True
  print([20,30] in l) # False --> only returns true if a value is member of a list but not for sublists
  ```

- `not in` returns negation of `in`

### Arithmetic Progression nth Term

- A series that has a common difference between the elements in called arithmetic progression.

- Mathematical formula to calculate arithmetic progression for nth term. **a+(n-1)d** where **a = first term** and **d = common difference**

- Example series:

  ```basic
  {5000, 7000, 9000, 11000, ....}
  ```

### Geometric Progression nth Term

- A series that has common ration between terms is called geometric progression.
- Mathematical formula **ar\**(n-1) ** where **a = first term** and **r = common ratio**

### Sum of Natural Numbers

- Mathematical formula: **n*(n+1)/2**

## Flow Control

- if, else and elif condition syntax in python

  ```python
  if condition:
      # statements to execute
  elif condition:
      # statements to execute
  else:
      # statements to execute
  ```

- Nothing more in this section. Talks about couple of problems and solving them using if, else conditions.

## Loops

### range()

- generates a range object with numbers starting from zero to n-1 assuming n is a positive number.

  ```python
  r = range(5)
  print(r) # range(0,5)
  l = list(r)
  print(l) # [0,1,2,3,4]
  print(type(r)) # <class,'range'>
  ```

- range function with two parameters

  ```python
  print(list(range(10,20))) # [10,11,12,13,14,15,16,17,18,19]
  print(list(range(-2,2))) # [-2,-1,0,1]
  ```

- range function with three parameters

  ```python
  print(list(range(10,20,2))) # [10,12,14,16,18]
  print(list(range(10,20,3))) # [10,13,16,19]
  print(list(range(20,10,-2))) # [20,18,16,14,12]
  ```

### Continue

-  continues to the next iteration without executing the next statements after the condition.

  ```python
  l = [10,16,17,18,19,15]
  for x in l:
      if x%5 == 0:
          continue
      print(x)
  ```

- We can always use other conditions without using continue. Continue just makes the code more elegant and readable.

## Functions

- syntax

  ```python
  def funcName():
  ```

- functions with parameters

  ```python
  def printDate(date, month, year):
      print(date, month, year, sep="-")
  ```

- Default arguments

  ```python
  def printDetails(id, name="NA", price="NA"):
      print(f"Id is {id}")
      print(f"Id is {name}")
      print(f"Id is {price}")
      
  printDetails(101,"abc",100)
  printDetails() # throws an error since id is not a default argument
  ```

  - `id` is not a default argument. So, we need to pass a value for id when calling `printDetails` function.

- Default and keyword arguments

  ```python
  def printDetails(id, name="NA", price="NA"):
      print(f"Id is {id}")
      print(f"Id is {name}")
      print(f"Id is {price}")
      
  printDetails(name="abc", id=101) # passing keyword before the argument
  ```

- Variable length arguments **(one star prefixed will be tuple)**

  ```python
  def sum(*elements):
      result = 0
      for element in elements:
          result = result+element
      return result
  
  print(sum(10,20)) # 30
  print(sum()) # 0
  ```

  - An argument prefixed with star is considered as a tuple and variable length arguments can be passed to it. 

- Keyword variable length arguments **(two stars prefixed will be dictionary)**

  ```python
  def printDetails(**elements):
      for d,v in elements.items():
          print(f"{d} is {v}")
          
  printDetails(id=101, name="abc", price=100)
  ```

### Parameter passing

- Consider the two functions below and understand the differences in output

  - Example 1

  ```python
  def assignVariableToNewValue(x):
      x = 15
  x = 10
  assignVariableToNewValue(x)
  print(x) # 10
  ```

  - Example 2

  ```python
  def appendToExistingObject(l):
      l.append(15)
  l = [10,20,30]
  appendToExistingObject(l)
  print(l) # [10,20,30,15]
  ```

  - In example one when value `x` is passed to function it still holds the same reference to that object. However, when the value of x is assigned to a new value the reference is modified and the local variable inside the function now refers to a new memory location which is 15
  - In example two we are not assigning a new value to our list but instead we are just appending a new value to our existing reference to the object. 
  - Try printing the id's of each variable to understand the difference 

### Returning multiple values

```python
def add_multiply(x,y):
    sum = x+y
    multiply = x*y
    return sum,multiply # packed as a tuple 

s,m=add_multiply(10,20) # unpacks the tuple and assigns the values based on the indexes/positions
print(s) #30
print(m) #200
```

### Global variables

- Modifying global variables inside functions

  ```python
  def func():
      global x 
      x = 15 # references global variable x and modifies the value
  x = 10
  func()
  print(x) # 15
  ```

- Accessing both global and local variables with same name inside the function

  ```python
  def fun():
      x = 10
      globals()['x'] = 20
      print(x) # 10
  x = 15
  fun()
  print(x) # 20
  ```


## String

- Values of characters from **'A'** to **'Z'** start from **65** to **90**. 

- Values of characters from **'a'** to **'z'** start from **97** to **122**.

  - Example:

    ```python
    print(ord("a")) # 97
    print(ord("A")) # 65
    print(chr(97)) # a
    print(chr(65)) # A
    ```

- String indexes in python

  |  G   |  E   |  E   |  K   |
  | :--: | :--: | :--: | :--: |
  |  0   |  1   |  2   |  3   |
  |  -4  |  -3  |  -2  |  -1  |

- Triple quoted strings to create multi line strings

  ```python
  str = """Hi,
  Use triple quotes to create multi line strings.
  Can also use triple single quotes instead of double."""
  print(str) # prints the string retaining the new line characters.
  ```

### Escape sequences and raw strings

- Escape sequence

  ```python
  str = 'Geek\'s for Geek\'s'
  print(str) # Geek's for Geek's
  ```

- Escaping escape sequence

  ```python
  str1 = "Backslash at the end \\"
  str2 = "\\n"
  print(str1) # Backslash at the end \
  print(str2) # \n
  ```

- Raw strings

  ```python
  str1 = "C:\files\new.py"
  str2 = r"C:\files\new.py"
  print(str1) # C:\files and prints ew.py on a new line
  print(str2) # adding r ignores escape sequences in the string and prints C:\files\new.py
  ```

### Formatted strings

- python has three ways to format strings

  - Old school C language style

    ```python
    name = "John"
    course = "Python Course"
    welcome_str = "Welcome %s to the %s."%(name,course)
    print(welcome_str) # Welcome John to the Python Course
    ```

  - Using format()

    ```python
    name = "John"
    course = "Python Course"
    welcome_str = "Welcome {0} to the {1}.".format(name,course)
    print(welcome_str) # Welcome John to the Python Course
    ```

  - Using f-String - **Recommended**

    ```python
    name = "John"
    course = "Python Course"
    welcome_str = f"Welcome {name} to the {course}."
    print(welcome_str) # Welcome John to the Python Course
    ```

  - Can also use the **+** operator

    ```python
    name = "John"
    course = "Python Course"
    welcome_str = "Welcome " + name + " to the " + course"
    print(welcome_str) # Welcome John to the Python Course
    ```

- We can also use expressions and call methods using f-String

  ```python
  x = 10
  y = 20
  print(f"Sum of {x} and {y} is {x+y}")
  print(f"Product of {x} and {y} is {x*y}")
  ```

  ```python
  str1 = "ABC"
  str2 = "abc"
  print(f"Lower case of {str1} is {str1.lower()}")
  print(f"Uppes case of {str2} is {str2.upper()}")
  ```

- Validate if a sub string of a string

  ```python
  str1 = "geeksforgeeks"
  str2 = "geeks"
  print(str2 in str1) # True
  print(str2 not in str1) # False
  ```

- Finding index position of a substring

  ```python
  str1 = "geeksforgeeks"
  str2 = "geeks"
  print(s1.index(s2)) # 0 --> returns the index of first occurence of substring
  print(s1.rindex(s2)) # 8 --> returns the index of last occurence of substring
  print(s1.index(s2,0,13)) # 0 --> searches for the sub string from the start and end-1 index positions
  ```

- **Remember that both index() and rindex() methods return a value error if the substring is not found in the parent string.**

- **startswith() and endswith()**

  ```python
  s = "GeeksforGeeks Python Course"
  print(s.startswith("Geeks")) # True
  print(s.endswith("Course")) # True
  print(s.startswith("Geeks",1)) # False --> Since start index is 1 and the search string now becomes 'eeksforGeeks Python Course'
  print(s.startswith("Geeks",8,len(s))) # True --> Start index is 8 which means search string now becomes 'Geeks Python Course'
  ```

- **split() and join()**

  ```python
  str1 = "geeks for geeks"
  print(str1.split()) # ['geeks','for','geeks']
  str2 = "geeks,for,geeks"
  print(str2.split(",")) # ['geeks','for','geeks']
  list1 = ["geeksforgeeks", "python", "course"]
  print(" ".join(list1)) # geeksforgeeks python course
  print(",".join(list1)) # geeksforgeeks,python,course
  ```

- **strip(), lstrip(), and rstrip()**

  ```python
  s = "---geeksforgeeks---"
  print(s.strip("-")) # geeksforgeeks 
  print(s.lstrip("-")) # geeksforgeeks---
  print(s.rstrip("-")) # ---geeksforgeeks 
  ```

- **find()**

  ```python
  str1 = "geeks for geeks"
  str2 = "geeks"
  print(str1.find(str2)) # 0
  print(str1.find("John")) # -1
  print(str1.find(str2,1,len(str1))) # 10
  ```

  - How is a find() method different from index() method ?
    - Both index() and rindex() throw a value error when a sub string is not found in the parent string. Where as find() method returns **-1** when a substring is not found.

### String comparision

```python
str1 = "geeksforgeeks"
str2 = "ide"
print(str1 < str2) # True
print(str1 <= str2) # True
print(str1 > str2) # False
print(str1 >= str2) # False
print(str1 == str2) # False
print(str1 != str2) # True
```

- How are the above comparisons working ?
  - Python internally converts the strings to an array/list of characters and then gets the unicode value of each character and compares them.

## List

### Slicing

```python
list1 = [10,20,30,40,50]
print(list1[0:5:2]) # [10,30,50]
# Expression list1[0:5:2] is interpreted as list[start:stop:step] which means it returns a new list which begins at start index and continues till stop-1 index by adding start+step every time. 
print(list1[:4]) # [10,20,30,40] --> start is set to 0 by default
print(list1[2:]) # [30,40,50] --> stop is set to len by default
print(list1[4:1:-1]) # [50,40,30] --> getting items in reverse order
```

- Consider the below example and understand the difference

  ```python
  l1 = [10,20,30]
  l2 = l1[:]
  t1 = (10,20,30)
  t2 = t1[:]
  s1 = "Geeks"
  s2 = s1[:]
  print(l1 is l2) # False
  print(t1 is t2) # True
  print(s1 is s2) # True
  ```

  - Since tuple's and string's are immutable, python creates a same reference to both the objects and hence it returns true.  On the other hand list is mutable and python creates two objects for list. 

### Comprehensions in python

- Gives us ability to write a shortcut syntax to create a resulting iterable. Consider the below example where we need to create a list of even numbers till 10.

  ```python
  l1 = []
  for x in range(11):
      if x%2 == 0:
          l1.append(x)
  # we can do the same with a one liner as shown below
  l1 = [x for x in range(11) if x % 2 == 0]
  ```

- Other examples

  ```python
  l1 = ["geeks","for","geeks","gfg","ide"]
  print([x.upper for x in l1 if x.startswith("g")]) # ["GEEKS","GEEKS","GFG"]
  ```

- Similarly, we can create a set using curly braces

  ```python
  l = [10,20,30,40,50,10,20,30,40,50]
  even = {e for e in l if e%2 == 0} # {10,20,30,40,50}
  odd = {e for e in l if e%2 != 0} # {}
  ```

- Compressions using dictionary

  ```python
  l1 = [1,3,4,2,5]
  d1 = {x:x**3 for x in l}
  print(d1) # {1:1, 3:7, 4:64, 2:8, 5:125}
  
  d2 = {x:f"ID{x}" for x in range(5)}
  print(d2) # {0:'ID0', 1:'ID1', 2:'ID2', 3:'ID3', 4:'ID4'}
  
  l2 = [101,102,103]
  l3 = ["gfg","ide","courses"]
  d3 = {l2[i]:l3[i] for i in range(len(l2))}
  print(d3) # {101:'gfg', 102:'ide', 103:'courses'} 
  ```

- A better way to combine two lists and create a dictionary

  ```python
  l2 = [101,102,103]
  l3 = ["gfg","ide","courses"]
  #-----d3 = {l2[i]:l3[i] for i in range(len(l2))}----
  d3 = dict(zip(l2,l3))
  print(d3) # {101:'gfg', 102:'ide', 103:'courses'} 
  ```

- Reversing key value pairs in dictionary using comprehensions

  ```python
  d1 = {101:'gfg', 102:'ide', 103:'courses'}
  d2 = {v:k for (k,v) in d1.items()}
  print(d2) # {'gfg':101, 'ide':102, 'courses':103}
  ```

  