Defining Functions:
```python
def greet(name):
    return f"Hello, {name}"
result = greet("Abhi")
 print(result)


Default & Keyword Arguments:
def greet(name="Guest"):
    print(f"Hello, {name}")

greet()              # Output: Hello, Guest
greet("Abhi")        # Output: Hello, Abhi
greet(name="Ravi")   # Output: Hello, Ravi

