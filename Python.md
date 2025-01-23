# Object-Oriented Programming (OOP) in Python

Object-Oriented Programming (OOP) is a programming paradigm that organizes code into objects. Python’s OOP features include:
- Classes and Objects
- Instance Methods
- Static Methods
- Class Methods
- Abstract Methods
- Encapsulation, Inheritance, Polymorphism, and Abstraction

Below are concise notes with examples for each concept.

---

## 1. **Classes and Objects**
- A **class** is a blueprint for creating objects (instances).
- An **object** is an instance of a class.

### Example:
```python
class Person:
    def __init__(self, name, age):  # Constructor
        self.name = name
        self.age = age

    def greet(self):  # Instance Method
        return f"Hello, my name is {self.name}."

person = Person("Alice", 30)  # Create an object
print(person.greet())  # Output: Hello, my name is Alice.
```

---

## 2. **Instance Methods**
- Use `self` as the first parameter.
- Operate on instance-specific data.

### Example:
```python
class Counter:
    def __init__(self):
        self.count = 0

    def increment(self):
        self.count += 1
        return self.count

c = Counter()
print(c.increment())  # Output: 1
print(c.increment())  # Output: 2
```

---

## 3. **Static Methods**
- Use `@staticmethod`.
- Do not require `self` or `cls`.
- Useful for utility functions that don’t depend on class or instance data.

### Example:
```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

print(MathUtils.add(10, 20))  # Output: 30
```

**Without `@staticmethod`**:
```python
class MathUtils:
    def add(a, b):  # No self or cls
        return a + b

print(MathUtils.add(10, 20))  # Output: 30 (works but not ideal)
```
Adding `@staticmethod` improves clarity and prevents accidental misuse.

---

## 4. **Class Methods**
- Use `@classmethod`.
- Require `cls` as the first parameter.
- Operate on class-level data.

### Example:
```python
class Employee:
    company = "TechCorp"

    @classmethod
    def set_company(cls, name):
        cls.company = name

Employee.set_company("NewCorp")
print(Employee.company)  # Output: NewCorp
```

### Factory Method Example:
```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    @classmethod
    def from_string(cls, emp_str):
        name, salary = emp_str.split(",")
        return cls(name, int(salary))

emp = Employee.from_string("John,50000")
print(emp.name, emp.salary)  # Output: John 50000
```

---

## 5. **Abstract Methods**
- Use `@abstractmethod` in abstract classes.
- Enforce method implementation in subclasses.
- Defined in the `abc` (Abstract Base Class) module.

### Example:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

# c = Shape()  # ERROR: Cannot instantiate abstract class
c = Circle(5)
print(c.area())  # Output: 78.5
```

**Why Use Abstract Methods?**
- Enforce consistent structure in subclasses.
- Prevent incomplete implementations.

---

## 6. **Encapsulation**
- Restrict access to data using private variables (`__variable`).
- Use getter and setter methods to access or modify private data.

### Example:
```python
class BankAccount:
    def __init__(self):
        self.__balance = 0  # Private variable

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount()
account.deposit(1000)
print(account.get_balance())  # Output: 1000
```

---

## 7. **Inheritance**
- Allows a class (child) to inherit from another class (parent).
- Reuse and extend functionality.

### Example:
```python
class Animal:
    def speak(self):
        return "I am an animal."

class Dog(Animal):
    def speak(self):
        return "Woof!"

d = Dog()
print(d.speak())  # Output: Woof!
```

---

## 8. **Polymorphism**
- Allows different classes to have methods with the same name but different behavior.

### Example:
```python
class Cat:
    def speak(self):
        return "Meow!"

class Dog:
    def speak(self):
        return "Woof!"

def animal_sound(animal):
    print(animal.speak())

cat = Cat()
dog = Dog()
animal_sound(cat)  # Output: Meow!
animal_sound(dog)  # Output: Woof!
```

---

## 9. **Summary Table**
| **Method Type**   | **Decorator**     | **First Parameter** | **Use Case**                                      |
|--------------------|-------------------|----------------------|--------------------------------------------------|
| Instance Method    | None              | `self`              | Access or modify instance-specific data.         |
| Static Method      | `@staticmethod`   | None                | Utility functions unrelated to class or instance.|
| Class Method       | `@classmethod`    | `cls`               | Work with or modify class-level data.            |
| Abstract Method    | `@abstractmethod` | `self` (subclasses) | Enforce method implementation in subclasses.     |

---

