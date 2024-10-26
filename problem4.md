### Problem 4: Design Bank Account Class

---

**Problem Statement: Bank Account Management**

You are tasked with creating a simple **Bank Account** class in JavaScript that simulates basic bank account operations while ensuring that sensitive information (like the account balance) is kept private.

1. **Properties**:
   - A private property `#holderName` to store the name of the account holder.
   - A private property `#balance` that stores the current balance of the account (should start at 0).

2. **Constructor**:
   - The class should have a constructor that initializes the `#holderName` and sets the `#balance` to 0.

3. **Getters**:
   - Implement a getter method called `getBalance` that returns the current balance of the account.

4. **Setters**:
   - Implement a setter method called `deposit` that allows adding a specified amount to the `#balance`. Ensure that the amount being deposited is positive; otherwise, log an error message.
   - Implement a setter method called `withdraw` that allows deducting a specified amount from the `#balance`. Ensure that the withdrawal does not exceed the current balance; otherwise, log an error message.

5. **Error Handling**:
   - Use `console.error` to log messages when invalid transactions occur (e.g., depositing a negative amount or withdrawing more than the balance).

6. **Demonstration**:
   - After implementing the class, create an instance of the **Bank Account** class and demonstrate the following:
     - Display the initial balance.
     - Deposit a valid amount and display the updated balance.
     - Attempt to deposit a negative amount and observe the error message.
     - Withdraw a valid amount and display the updated balance.
     - Attempt to withdraw more than the balance and observe the error message.
     - Attempt to access or modify the private properties directly and see that it results in an error.

### Hints

- Remember that private properties are defined using the `#` symbol in front of the property name.
- Use `console.log()` to display output and `console.error()` for error messages.
- Consider how you would check the validity of deposit and withdrawal amounts.

### Example of Usage

```javascript
const account = new BankAccount("Alice Johnson");

console.log(account.getBalance()); // Initial balance: 0

account.deposit(100);
console.log(account.getBalance()); // Updated balance: 100

account.deposit(-50); // Error: Deposit amount must be positive.

account.withdraw(30);
console.log(account.getBalance()); // Updated balance: 70

account.withdraw(100); // Error: Insufficient funds.

console.log(account.#balance); // Error: Private field '#balance' must be declared in an enclosing class
account.#balance = 500; // Error: Private field '#balance' cannot be assigned to from outside its class
```

---
### Learning Objectives

1. **Understand Class Syntax**: Learners will grasp how to define a class in JavaScript and create instances.

2. **Use of Constructors**: Learners will learn to use constructors to initialize properties in an object.

3. **Implement Private Properties**: Learners will understand how to create private properties using the `#` syntax for encapsulation.

4. **Implement Getters and Setters**: Learners will learn how to create getter and setter methods for controlled access to private properties.

5. **Validation in Setters**: Learners will apply validation within setter methods to ensure proper data handling (e.g., checking for positive deposits and sufficient balances for withdrawals).

6. **Error Handling**: Learners will practice logging error messages to the console for invalid operations.

7. **Encapsulation**: Learners will recognize the importance of encapsulation and controlled access to object properties.
