# 🧱 Python Object-Oriented Programming (OOP)

**OOP** is a programming paradigm based on the concept of **"objects"** — instances of **classes** that encapsulate data and behavior.

---

## 🔹 Key OOP Concepts

| **Class**   | Blueprint for creating objects                |
| **Object**  | Instance of a class                           |
| **Method**  | Function defined inside a class               |
| **Attribute** | Variable associated with an object          |
| **Constructor** | `__init__()` method to initialize objects |
| **Self**    | Refers to the current object                  |
| **Encapsulation** | Hiding internal state (using private attrs)|
| **Inheritance** | One class inherits from another           |
| **Polymorphism** | Same method behaves differently by context|

---

## 🔹 Defining a Class & Object

```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, my name is {self.name}")

# Creating an object
p1 = Person("Abhi", 22)
p1.greet()    # Output: Hello, my name is Abhi

