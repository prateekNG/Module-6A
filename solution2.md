### Solution:

#### `inventoryUtils.js`

In this file, we define our `addBook`, `filterBooksByGenre`, and `getBookInfo` functions. The `addBook` function is exported as the default, while the other two functions are named exports.

```javascript
// inventoryUtils.js

// Default export function to add a book
export default function addBook(books, newBook) {
    const { title, author, genre, quantity = 1 } = newBook; // Use default parameter for quantity
    books.push({ title, author, genre, quantity });
}

// Named export function to filter books by genre
export function filterBooksByGenre(books, genre) {
    return books.filter(book => book.genre === genre);
}

// Named export function to get book information by title
export function getBookInfo(books, title) {
    const book = books.find(book => book.title === title);
    return book || { error: "Book not found" };
}
```

---

#### `main.js`

In this file, we import the functions from `inventoryUtils.js`, initialize the bookstore's inventory, and use each function to manage the inventory.

```javascript
// main.js

// Importing the functions
import addBook from './inventoryUtils.js';
import { filterBooksByGenre, getBookInfo } from './inventoryUtils.js';

// Sample data for bookstore's initial inventory
const books = [
    { title: "1984", author: "George Orwell", genre: "Dystopian", quantity: 4 },
    { title: "To Kill a Mockingbird", author: "Harper Lee", genre: "Classic", quantity: 2 },
    { title: "The Great Gatsby", author: "F. Scott Fitzgerald", genre: "Classic", quantity: 5 }
];

// Adding a new book without specifying quantity (should default to 1)
addBook(books, { title: "Brave New World", author: "Aldous Huxley", genre: "Dystopian" });

// Filtering books by genre
const dystopianBooks = filterBooksByGenre(books, "Dystopian");
console.log("Dystopian Books:", dystopianBooks);

// Getting information about a specific book by title
const bookInfo = getBookInfo(books, "1984");
console.log("Book Information:", bookInfo);

// Trying to get information about a non-existent book
const nonExistentBookInfo = getBookInfo(books, "Unknown Title");
console.log("Non-existent Book Information:", nonExistentBookInfo);
```

---

### Expected Console Output

```javascript
// Console Output:
Dystopian Books: [
    { title: "1984", author: "George Orwell", genre: "Dystopian", quantity: 4 },
    { title: "Brave New World", author: "Aldous Huxley", genre: "Dystopian", quantity: 1 }
]
Book Information: { title: "1984", author: "George Orwell", genre: "Dystopian", quantity: 4 }
Non-existent Book Information: { error: "Book not found" }
```

---

### Explanation

- **`addBook`**: Adds a new book to the `books` array. The function uses object destructuring and sets a default value of `1` for the `quantity` property if it's not provided.
- **`filterBooksByGenre`**: Filters the array by genre, allowing the bookstore to view all books in a specific category.
- **`getBookInfo`**: Finds a book by its title. If no book matches the title, it returns an error message object, `{ error: "Book not found" }`.
