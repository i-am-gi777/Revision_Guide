List: Mutable
my_list = [1, 2, 3]

```python
l = [1,2,3]
print(l) #output:[1,2,3]
# Index
l[1]
print(l[1]) #output:1
## Insert by Replace/change value in list by using index
l[1] = 0
print(l) #output:[1,0,3]
# Append
l.Append(4)
print(l) #output:[1,0,3,4]
# Insert at Index
l.insert(0,0)  #(index, object)
print(l)  #output:[0,0,3,4]
# Remove from list
# only one is removed if there are duplicates
l.append(4)
l.append(4)
l.remove(4)
print(l)
# clear/delete 
l.clear()
print(l)
# sort: inplace sorting/permanent sorting
l = [3,1,2]
l.sort(reverse = Flase)
# reverse
l.reverse()
print(l)
# use F string & if, for loop in list
for x in l:
    if x % 2 == 0:
        print(f"even": x)
    elif x * 2 == 4:
        print(x)
    else:
        print("-")


Tuple: Immutable
my_tuple = (1, 2, 3)
# Define a tuple
t = (1, 2, 3)
print(t)  # output: (1, 2, 3)
# Indexing
print(t[0])  # output: 1
# Negative Indexing
print(t[-1])  # output: 3
# Slicing
print(t[1:])  # output: (2, 3)
# Nested Tuples
t2 = (1, (2, 3), 4)
print(t2[1])      # output: (2, 3)
print(t2[1][0])   # output: 2
# Length of tuple
print(len(t))  # output: 3
# Count elements
t3 = (1, 2, 2, 3)
print(t3.count(2))  # output: 2
# Find index of element
print(t3.index(2))  # output: 1 (first occurrence)
# Iteration using for loop
for x in t3:
    print(x)
# Tuple with different data types
mixed = (1, "hello", True, 3.14)
print(mixed)  # output: (1, 'hello', True, 3.14)
# Tuple unpacking
a, b, c = (10, 20, 30)
print(a)  # output: 10
print(b)  # output: 20
print(c)  # output: 30
# Tuple in f-string with if and for loop
t = (1, 2, 3, 4)
for x in t:
    if x % 2 == 0:
        print(f"even: {x}")
    elif x * 2 == 4:
        print(x)
    else:
        print("-")


Set: Unordered, no duplicates
my_set = {1, 2, 3}
# Define a set
s = {1, 2, 3}
print(s)  # output: {1, 2, 3} (order may vary)
# Automatically removes duplicates
s = {1, 2, 2, 3, 3, 3}
print(s)  # output: {1, 2, 3}
# Add one element
s.add(4)
print(s)  # output: {1, 2, 3, 4}
# Update set with multiple elements
s.update([5, 6])
print(s)  # output: {1, 2, 3, 4, 5, 6}
# Remove an element (throws error if not found)
s.remove(2)
print(s)  # output: {1, 3, 4, 5, 6}
# Discard an element (no error if not found)
s.discard(100)  # Safe
print(s)
# Pop removes and returns a random element
removed = s.pop()
print(f"Popped: {removed}")
print(s)
# Clear all elements
s.clear()
print(s)  # output: set()

a = {1, 2, 3}
b = {3, 4, 5}
# Union
print(a | b)  # output: {1, 2, 3, 4, 5}
# Intersection
print(a & b)  # output: {3}
# Difference
print(a - b)  # output: {1, 2}
# Symmetric Difference
print(a ^ b)  # output: {1, 2, 4, 5}

a = {1, 2, 3}
# Length
print(len(a))  # output: 3
# Check membership
print(2 in a)  # output: True
print(5 in a)  # output: False
s = {1, 2, 3, 4}
for x in s:
    if x % 2 == 0:
        print(f"even: {x}")
    elif x * 2 == 4:
        print(x)
    else:
        print("-")
