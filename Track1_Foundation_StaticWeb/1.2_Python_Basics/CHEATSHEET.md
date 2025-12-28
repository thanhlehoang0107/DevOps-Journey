# Python Basics - Cheatsheet

## Cú pháp cơ bản

```python
# Variables
name = "DevOps"
count = 10

# Lists
tools = ["docker", "k8s", "terraform"]

# Dictionaries
config = {"port": 8080, "host": "localhost"}

# Functions
def greet(name):
    return f"Hello {name}"

# Loops
for tool in tools:
    print(tool)
```

## File I/O

```python
# Read file
with open("config.txt", "r") as f:
    content = f.read()

# Write file
with open("output.txt", "w") as f:
    f.write("Hello DevOps")
```

## System Interaction

```python
import subprocess
result = subprocess.run(["ls", "-la"], capture_output=True, text=True)
print(result.stdout)
```
