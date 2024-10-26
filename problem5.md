### Problem 5: Shopping Cart System

**Problem Statement:**

You are developing an advanced shopping cart system for an online marketplace. In this application, you will create classes to manage products, handle cart operations, and simulate data fetching from an external server. The shopping cart should handle products dynamically, providing functionality to add, remove, update quantities, and calculate total prices for the items. 

To implement access control, make sure certain properties, such as `items`, remain private and only accessible through specific methods.

#### Requirements:

1. **`Product` Class**:
   - **Properties**:
     - `id` (unique identifier, string) – A unique product ID.
     - `name` (string) – The product name.
     - `price` (number) – The price per unit.
     - `quantity` (number) – Available stock for this product. **Stock should be mutable** only within certain conditions.

   - **Methods**:
     - `adjustStock(newQuantity)` – Adjusts the stock of the product but does not allow it to go below zero. If an invalid quantity is given, throw an error: `"Invalid stock quantity"`.
     - `getDetails()` – Returns a formatted string using destructuring (e.g., "Product: Laptop, Price: $1000, Stock: 5").

2. **`Cart` Class**:
   - **Private Property**:
     - `#items` – A private array of items in the cart, each representing a `Product` with added properties.

   - **Methods**:
     - `addProduct(productId, quantity)` – Adds a specified quantity of a product to the cart. If the product already exists in the cart, increment the quantity. Ensure the product stock is updated and does not exceed availability. Throw an error if stock is insufficient.
     - `removeProduct(productId)` – Removes a product from the cart by its `id`. If the product doesn’t exist in the cart, throw an error: `"Product not found in cart."`.
     - `updateProductQuantity(productId, newQuantity)` – Updates the quantity of a specific product in the cart, ensuring it does not exceed available stock. If an invalid quantity is provided, throw an error.
     - `calculateTotal()` – Calculates the total cost of all items in the cart.
     - `getCartDetails()` – A getter that returns all product details in the cart, displaying each item’s name, quantity, and total price (price per item * quantity) in a structured format.

3. **`Store` Class**:
   - **Purpose**: Acts as a mock API to asynchronously fetch products.
   - **Method**:
     - `fetchProductData(productId)` – Returns a promise that resolves after a delay with a new `Product` object. If the product ID doesn’t match a product in the "database" (you can use a static array of product objects), the promise should reject with `"Product not found."`

4. **Additional Requirements**:
   - Use the `#` syntax to create private properties where necessary.
   - Products in the cart should not expose direct modification options to the user outside the class methods.
   - Use destructuring for better readability in methods like `getCartDetails`.

#### Functionality Example:

Write a script that:
1. Fetches several products from the `Store` class using `fetchProductData`.
2. Adds the products to the `Cart` and adjusts quantities.
3. Attempts to add a product with insufficient stock to validate error handling.
4. Displays cart details with product quantities, names, and line-item totals.
5. Calculates the final total using `calculateTotal`.

#### Hints

- **Private Properties**: Use `#` to declare private properties for controlling data access.
- **Asynchronous Fetch**: Use Promises and `async/await` to handle asynchronous fetching of products.
- **Error Handling**: Carefully handle errors for invalid operations (like over-adding stock or adjusting quantity) to test robustness.

---

**Learning Objectives:**

1. **Advanced class syntax and method handling**, including managing dependencies across classes.
2. **Control access with private properties** using modern JavaScript conventions.
3. **Error handling in promise-based asynchronous code** for real-world API simulation.
4. **Data immutability and encapsulation** to enforce object integrity and secure operations.
5. **Working with destructuring and conditional property handling** in class-based objects. 
