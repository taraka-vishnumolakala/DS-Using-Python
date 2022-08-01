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

## Loops

## Functions

## String

## List