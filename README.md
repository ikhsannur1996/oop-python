# 🧠 What is OOP?

OOP stands for **Object-Oriented Programming**. It’s a way of writing code by thinking in terms of **objects**, like in real life.

🧸 Think of real-life examples:

* A **Dog** has a name and can bark.
* A **Car** has a color and can drive.
* A **Phone** has a brand and can make calls.

Each of those is an **object**, and they:

* Have **properties** (like name, color, brand) → called **attributes** in code.
* Can **do things** (like bark, drive, call) → called **methods** in code.

OOP helps us model this behavior in Python.

---

# 🧱 OOP Basic Concepts (Explained Simply)

## 1. **Class** → The Blueprint 🏗️

A class is a **template** or blueprint for creating objects.

```python
class Dog:
    pass
```

This creates a class called `Dog`, but it doesn’t do anything yet.

---

## 2. **Object** → The Real Thing 🎯

An object is a real version of the class.

```python
my_dog = Dog()
print(type(my_dog))  # Output: <class '__main__.Dog'>
```

You just made an object called `my_dog` using the class `Dog`.

---

## 3. **Attributes** → Object's Data 📦

Attributes are **variables inside an object** that hold data (like name, age, etc.).

We use a special method called `__init__()` to set up data when creating an object.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name  # Attribute
        self.age = age    # Attribute
```

```python
my_dog = Dog("Buddy", 3)
print(my_dog.name)  # Buddy
print(my_dog.age)   # 3
```

Explanation:

* `__init__()` is run **automatically** when we make a new object.
* `self.name = name` means this dog will now have a name attribute.

---

## 4. **Methods** → What the Object Can Do 🦴

Methods are **functions inside a class**.

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        print(f"{self.name} says: Woof!")
```

```python
dog1 = Dog("Charlie")
dog1.bark()  # Output: Charlie says: Woof!
```

Explanation:

* `bark()` is a method.
* It uses `self.name` to print the dog's name.

---

## 5. **Encapsulation** → Protect the Data 🔐

Encapsulation means **hiding the details** and only showing what’s necessary.

Example: A bank account should not allow direct access to balance.

```python
class BankAccount:
    def __init__(self):
        self.__balance = 0  # Private attribute

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance
```

```python
acc = BankAccount()
acc.deposit(100)
print(acc.get_balance())  # 100
# print(acc.__balance) → Error! It's private!
```

The double underscore `__balance` hides the data from outside access.

---

## 6. **Abstraction** → Hide the Complexity 🧊

Abstraction means showing **only what the user needs** to see and hiding details.

Example: You drive a car without knowing how the engine works.

In Python, we use **abstract classes** to force certain methods in child classes.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Cat(Animal):
    def sound(self):
        print("Meow")
```

You **must** define `sound()` in `Cat`, or it will give an error.

---

## 7. **Inheritance** → Reuse Code 👪

Inheritance allows one class to **inherit** from another.

```python
class Animal:
    def eat(self):
        print("This animal eats food.")

class Dog(Animal):
    def bark(self):
        print("The dog barks.")
```

```python
d = Dog()
d.eat()   # From Animal class
d.bark()  # From Dog class
```

`Dog` gets `eat()` method **for free** from `Animal`. This avoids code duplication.

---

## 8. **Polymorphism** → One Name, Many Forms 🎭

Polymorphism means using the **same method name**, but with **different behavior**.

```python
class Cat:
    def sound(self):
        print("Meow")

class Dog:
    def sound(self):
        print("Woof")
```

```python
animals = [Cat(), Dog()]

for animal in animals:
    animal.sound()  # First Meow, then Woof
```

Even though both classes use `sound()`, they do different things.

---

# 🎓 All Concepts Summary Table

| Concept       | Simple Meaning                             | Example                          |
| ------------- | ------------------------------------------ | -------------------------------- |
| Class         | Blueprint / template                       | `class Dog:`                     |
| Object        | A real thing made from class               | `my_dog = Dog()`                 |
| Attribute     | Data (name, age) stored in the object      | `self.name = name`               |
| Method        | What the object can do (bark, run)         | `def bark(self):`                |
| Encapsulation | Hide internal data                         | `__balance`, use `get_balance()` |
| Abstraction   | Hide complex things, show simple interface | `@abstractmethod`                |
| Inheritance   | One class reuses another                   | `class Dog(Animal):`             |
| Polymorphism  | One method name, different results         | `animal.sound()` → meow or woof  |

---
