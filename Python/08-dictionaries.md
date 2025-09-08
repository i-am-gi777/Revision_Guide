```python
# Define a dictionary
d = {"name": "Alice", "age": 25, "department": "HR"}
print(d)  # output: {'name': 'Alice', 'age': 25, 'department': 'HR'}
# Access by key
print(d["name"])     # output: Alice

# Using get (safer, no error if key missing)
print(d.get("age"))  # output: 25
print(d.get("salary"))  # output: None

# Change value
d["age"] = 26
print(d)  # output: {'name': 'Alice', 'age': 26, 'department': 'HR'}

# Add new key-value pair
d["salary"] = 50000
print(d)  # output: {'name': 'Alice', 'age': 26, 'department': 'HR', 'salary': 50000}

# Remove by key
d.pop("department")
print(d)  # output: {'name': 'Alice', 'age': 26, 'salary': 50000}

# Delete specific key
del d["salary"]
print(d)  # output: {'name': 'Alice', 'age': 26}

# Clear entire dictionary
d.clear()
print(d)  # output: {}

d = {"a": 1, "b": 2, "c": 3}

# Loop over keys
for key in d:
    print(key)

# Loop over values
for value in d.values():
    print(value)

# Loop over key-value pairs
for key, value in d.items():
    print(f"{key} -> {value}")

d = {"x": 10, "y": 20}

# Check if key exists
print("x" in d)  # output: True

# Get all keys
print(d.keys())  # output: dict_keys(['x', 'y'])

# Get all values
print(d.values())  # output: dict_values([10, 20])

# Get all items
print(d.items())  # output: dict_items([('x', 10), ('y', 20)])

emp = {
    "id": 1,
    "info": {
        "name": "Alice",
        "age": 25
    }
}
print(emp["info"]["name"])  # output: Alice

