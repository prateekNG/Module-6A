### Problem 2: Inventory Management System

---

**Problem Description**:

You're building a small inventory management system for a local bookstore that requires modular, reusable code. The bookstore's inventory includes books, each with certain properties such as title, author, genre, and quantity in stock. You will create two modules:

1. **`inventoryUtils.js`**: 
   - Contains utility functions to manage book records in the inventory.
   - Exports functions using both named and default exports.
  
2. **`main.js`**:
   - Imports functions from `inventoryUtils.js` to manage and display the bookstore's inventory.
   - This file will include sample function calls to demonstrate the functionality of the inventory management system.

**Requirements**:

1. In `inventoryUtils.js`, write the following:
   - A default exported function named `addBook`, which takes a `books` array and a `newBook` object and adds the new book to the inventory.
     - `newBook` should have the following structure: `{ title, author, genre, quantity }`.
     - Set `quantity` to a default value of 1 if it's not provided.
   - A named export function called `filterBooksByGenre`, which takes the `books` array and a `genre` string and returns an array of books in that genre.
   - A named export function called `getBookInfo`, which takes the `books` array and a `title` string and returns the information about a book with that title. If no such book exists, return an object `{ error: "Book not found" }`.

2. In `main.js`, write:
   - Import and use `addBook` as a default import, while `filterBooksByGenre` and `getBookInfo` are imported as named imports.
   - Define an initial `books` array with some sample data. For example:
      ```javascript
      const books = [
          { title: "1984", author: "George Orwell", genre: "Dystopian", quantity: 4 },
          { title: "To Kill a Mockingbird", author: "Harper Lee", genre: "Classic", quantity: 2 },
          { title: "The Great Gatsby", author: "F. Scott Fitzgerald", genre: "Classic", quantity: 5 }
      ];
      ```
   - Use the imported functions to:
     - Add a new book to the `books` array without specifying `quantity`.
     - Retrieve books in a specific genre.
     - Get the information of a book by title.

---

### Learning Objectives / Skills Practiced:

1. **Modular Code Structure**: Practice organizing functions into separate modules, allowing code to be reused and managed more effectively.
2. **Import/Export Syntax**: Learn the use of default exports, named exports, and how to import them correctly in another file.
3. **Default Parameters**: Reinforce the use of default parameters in function definitions, allowing functions to handle missing values gracefully.
4. **Array and Object Manipulation**: Enhance skills in searching, filtering, and adding items within arrays of objects, simulating real-world data management tasks. 

This problem encourages learners to create, organize, and consume modular code while also handling object destructuring and default parameter values.
