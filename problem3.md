### Problem 3: Library System - Combining Book and Author Data with Asynchronous Fetching

---

**Problem Statement**:  
You're building an asynchronous data-fetching system for a digital library. This library’s data is divided into two sources: a **Books API** and an **Authors API**. Each book contains a `title`, `authorId`, `genre`, and `quantity`, while each author has a unique `id`, `name`, and `birthYear`.

You need to:
1. Fetch data from both the Books API and the Authors API. Each function should return a Promise that resolves after 1 second.
2. Match each book with its author by `authorId`.
3. For each book in the genre of “Science Fiction,” create a new object that includes the `title`, `authorName`, and `birthYear` of the author.

**Requirements**:
1. Both `fetchBooks` and `fetchAuthors` should return a Promise that resolves after 1 second. Use `setTimeout` to simulate network delay, and simulate occasional errors by rejecting based on a random condition.
2. Use `Promise.allSettled` to handle results from both API calls and proceed only if both are successful. If either fails, log the error for the corresponding API.
3. Use array methods to filter and combine data by matching the `authorId` in books with `id` in authors.

**Hints**:
- You’ll need to use `Promise.allSettled` to handle results from both APIs.
- Use `.filter`, `.map`, and `.find` methods to transform and merge the data.
- The combined output should only contain Science Fiction books with the author’s `name` and `birthYear`.

---

### Learning Objectives/Skills:
- Using `Promise.allSettled` to handle multiple asynchronous operations.
- Combining asynchronous data sources with `filter`, `map`, and `find` array methods.
- Error handling across multiple API calls and managing conditions where only partial data is available.
