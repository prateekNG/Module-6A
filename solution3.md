### Solution:

```javascript
// Mock API calls with simulated delay and occasional error

function fetchBooks() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (Math.random() > 0.1) {
                resolve([
                    { title: "The Stars My Destination", authorId: 1, genre: "Science Fiction", quantity: 5 },
                    { title: "Neuromancer", authorId: 2, genre: "Science Fiction", quantity: 3 },
                    { title: "Pride and Prejudice", authorId: 3, genre: "Classic", quantity: 4 },
                    { title: "Snow Crash", authorId: 2, genre: "Science Fiction", quantity: 2 }
                ]);
            } else {
                reject("Failed to fetch books");
            }
        }, 1000);
    });
}

function fetchAuthors() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (Math.random() > 0.1) {
                resolve([
                    { id: 1, name: "Alfred Bester", birthYear: 1913 },
                    { id: 2, name: "William Gibson", birthYear: 1948 },
                    { id: 3, name: "Jane Austen", birthYear: 1775 }
                ]);
            } else {
                reject("Failed to fetch authors");
            }
        }, 1000);
    });
}

// Solution function that combines data
async function getScienceFictionBooksWithAuthors() {
    try {
        const [booksResult, authorsResult] = await Promise.allSettled([fetchBooks(), fetchAuthors()]);

        if (booksResult.status === "rejected") {
            console.error("Error fetching books:", booksResult.reason);
            return;
        }

        if (authorsResult.status === "rejected") {
            console.error("Error fetching authors:", authorsResult.reason);
            return;
        }

        const books = booksResult.value;
        const authors = authorsResult.value;

        // Filter for Science Fiction books and map with author data
        const sciFiBooksWithAuthors = books
            .filter(book => book.genre === "Science Fiction")
            .map(book => {
                const author = authors.find(author => author.id === book.authorId);
                return {
                    title: book.title,
                    authorName: author ? author.name : "Unknown Author",
                    birthYear: author ? author.birthYear : "Unknown Year"
                };
            });

        console.log(sciFiBooksWithAuthors);
        return sciFiBooksWithAuthors;
    } catch (error) {
        console.error("Unexpected error:", error);
    }
}

// Run the function to see the output
getScienceFictionBooksWithAuthors();
```

### Explanation of Key Parts:
1. **Mock API Functions**: `fetchBooks` and `fetchAuthors` each return a Promise that resolves or rejects based on a random condition to simulate occasional errors.
2. **`Promise.allSettled`**: Ensures the code can handle individual failures in fetching data and log errors while still running successfully if possible.
3. **Combining Data**: After filtering books by genre, each book is matched with its author by `authorId`, and the necessary fields are returned as part of a new object.
