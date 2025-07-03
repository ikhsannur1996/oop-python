# 🏦 Full Python OOP Project: Bank System

### ✅ Includes:

* Abstract Base Class (`BankAccount`)
* Two Account Types (`SavingsAccount`, `CheckingAccount`)
* Methods to deposit, withdraw, and check balance
* Encapsulation to protect balance
* Abstraction to enforce account type
* Inheritance to reuse code
* Polymorphism with flexible method behavior
* Utility function to print summaries

---

### 🔧 Step-by-Step Code (Copy & Run)

```python
from abc import ABC, abstractmethod

# ================================
# 🧱 ABSTRACT BASE CLASS
# ================================

class BankAccount(ABC):
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.__balance = balance  # 🔐 Encapsulated attribute

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            print(f"Deposited ${amount}. New balance: ${self.__balance}")
        else:
            print("❌ Deposit amount must be positive.")

    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
            print(f"Withdrew ${amount}. New balance: ${self.__balance}")
        else:
            print("❌ Insufficient balance.")

    def get_balance(self):
        return self.__balance

    @abstractmethod
    def account_type(self):  # Must be implemented in child classes
        pass

# ================================
# 🏦 CHILD CLASSES (INHERITANCE)
# ================================

class SavingsAccount(BankAccount):
    def account_type(self):
        return "Savings Account"

class CheckingAccount(BankAccount):
    def account_type(self):
        return "Checking Account"

# ================================
# 📊 POLYMORPHIC FUNCTION
# ================================

def print_account_summary(account: BankAccount):
    print("🔸 Account Summary 🔸")
    print(f"Type   : {account.account_type()}")
    print(f"Owner  : {account.owner}")
    print(f"Balance: ${account.get_balance()}")
    print("-" * 30)

# ================================
# 🧪 CREATE ACCOUNTS (OBJECTS)
# ================================

# Create a savings account
savings = SavingsAccount("Alice", 1000)
savings.deposit(200)
savings.withdraw(150)

# Create a checking account
checking = CheckingAccount("Bob", 500)
checking.deposit(300)
checking.withdraw(800)  # Should fail

# ================================
# 🖨️ OUTPUT ACCOUNT INFO
# ================================

print_account_summary(savings)
print_account_summary(checking)
```

---

### 🖨️ Output

```text
Deposited $200. New balance: $1200
Withdrew $150. New balance: $1050
Deposited $300. New balance: $800
❌ Insufficient balance.
🔸 Account Summary 🔸
Type   : Savings Account
Owner  : Alice
Balance: $1050
------------------------------
🔸 Account Summary 🔸
Type   : Checking Account
Owner  : Bob
Balance: $800
------------------------------
```

---

## 📘 OOP Concepts Recap (Used in Code)

| Concept           | Example in Code                                           |
| ----------------- | --------------------------------------------------------- |
| **Class**         | `class BankAccount`, `class SavingsAccount`               |
| **Object**        | `savings = SavingsAccount("Alice", 1000)`                 |
| **Attribute**     | `self.owner`, `self.__balance`                            |
| **Method**        | `deposit()`, `withdraw()`, `get_balance()`                |
| **Encapsulation** | `__balance` is private, only changed through methods      |
| **Abstraction**   | `account_type()` is abstract in base class                |
| **Inheritance**   | `SavingsAccount` inherits from `BankAccount`              |
| **Polymorphism**  | `print_account_summary()` calls `account_type()` flexibly |

---

## 💡 Ideas to Expand This Project

Let me know if you want help building these features:

| Feature                    | Concept Practice               |
| -------------------------- | ------------------------------ |
| Add `User` login class     | Composition & multiple classes |
| Add `transfer()` method    | Object-to-object interaction   |
| Apply interest for savings | Method override, math logic    |
| Store accounts in a list   | Collection of objects          |
| Save/load data to file     | File I/O, persistence          |

