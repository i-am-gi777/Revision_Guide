For Loop:
The for loop is used to iterate over a sequence (like a list, string, or range).

```python
for i in range(5):
    print(i)  #output:0 1 2 3 4
NOTE: range(5) generates numbers from 0 to 4 (not inclusive of 5).

While Loop:
The while loop repeats as long as the condition is True.

i = 0
while i < 5:
    print(i)  #output:0 1 2 3 4
    i += 1



# Loop Control: break, continue, pass
break
Exits the loop immediately.

for i in range(5):
    if i == 3:
        break
    print(i).  #output:0 1 2 


continue
Skips the current iteration and moves to the next one.

for i in range(5):
    if i == 2:
        continue
    print(i).   #output:0 1 3 4


pass
Does nothing — it's a placeholder.

for i in range(5):
    if i == 2:
        pass  # placeholder for future code
    print(i)  #output:0 1 2 3 4

Optional: else with Loops
for i in range(5):
    print(i)
else:
    print("Loop finished without break.")

