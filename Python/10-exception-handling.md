# 🛑 Python Exception Handling

**Exceptions** are runtime errors that interrupt the flow of a program.

Python provides a way to **gracefully handle errors** using `try` and `except`.

---

## 🔹 Why Use Exception Handling?

- Prevent program crashes
- Display user-friendly messages
- Handle unexpected scenarios (e.g., file not found, divide by zero)

---

## 🔹 Basic Syntax

```python
try:
    # Code that might throw an error
    x = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")


try:
    x = 5 / 1
except ZeroDivisionError:
    print("Error occurred")
else:
    print("Success:", x)
