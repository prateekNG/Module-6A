### Solution:

```javascript
class BankAccount {
    // Private properties
    #holderName;
    #balance;

    constructor(holderName) {
        this.#holderName = holderName;
        this.#balance = 0; // Start balance at 0
    }

    // Getter for the balance
    getBalance() {
        return this.#balance;
    }

    // Setter for depositing money
    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
            console.log(`Deposited: ${amount}. New balance: ${this.getBalance()}`);
        } else {
            console.error("Deposit amount must be positive.");
        }
    }

    // Setter for withdrawing money
    withdraw(amount) {
        if (amount <= this.#balance) {
            this.#balance -= amount;
            console.log(`Withdrew: ${amount}. New balance: ${this.getBalance()}`);
        } else {
            console.error("Insufficient funds.");
        }
    }
}

// Example usage
const account = new BankAccount("Alice Johnson");

console.log(account.getBalance()); // Initial balance: 0

account.deposit(100); // Deposited: 100. New balance: 100
console.log(account.getBalance()); // Updated balance: 100

account.deposit(-50); // Error: Deposit amount must be positive.

account.withdraw(30); // Withdrew: 30. New balance: 70
console.log(account.getBalance()); // Updated balance: 70

account.withdraw(100); // Error: Insufficient funds.

console.log(account.#balance); // Error: Private field '#balance' must be declared in an enclosing class
account.#balance = 500; // Error: Private field '#balance' cannot be assigned to from outside its class
```
