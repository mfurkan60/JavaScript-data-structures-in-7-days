# Day 1: Introduction and Basic Data Structures

## Setup

Setting up your JavaScript development environment is the first step in your programming journey. First, you need to choose a text editor to use. Popular IDEs like Visual Studio Code, Sublime Text or Atom offer several advantages when writing JavaScript code. At this stage, you can create a new project folder and prepare the `index.html` and `script.js` files in this folder.

The HTML file is required to create the user interface of the application. You should add a basic HTML structure inside the `index.html` file. The following example is a good enough structure to get you started:

```html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Veri Yapıları</title>
</head>
<body>
    <h1>JavaScript ile Veri Yapıları</h1>
    <script src="script.js"></script>
</body>
</html>
```

The JavaScript file (script.js) is the code that will contain the logic of the application. By defining a simple array and object, you can start exploring the basic features of JavaScript:

```javascript

// Creating an array of numbers
const numbers = [1, 2, 3, 4];

// Creating an object to hold user information
const user = { name: 'Alice', age: 25 };

// Logging the array and object to the console
console.log(numbers); // Output: [1, 2, 3, 4]
console.log(user); // Output: { name: 'Alice', age: 25 }

```

To check if your project is working, you should open the index.html file in a browser. Use the browser console (by pressing F12) to make sure that the console.log output appears correctly.

## What are Data Structures?

Data structures are methods used to organize, store, and manipulate data. Effective use of data structures in the software development process plays a critical role in terms of performance and **memory management**. Data structures make it easier to manipulate data, allowing developers to write more efficient and effective code. Therefore, learning the basics of data structures is important for developing software development skills.

## Memory Management

Memory management is the process of efficiently allocating and freeing memory space that is necessary for programs to run. JavaScript has a garbage collection mechanism that provides automatic memory management. This mechanism automatically detects unused objects and arrays and frees these areas in memory. However, developers also need to pay attention to memory management. Especially when managing large data structures, it is important to properly control references to prevent unnecessary memory usage and memory leaks. For example, when an object is no longer used, setting it to `null` or `undefined` helps the JavaScript engine to include this object in the garbage collection process. Careful memory management can improve application performance and reduce resource consumption, which positively affects the user experience.


## Fundamentals Data Structures
Arrays represent an ordered set of data. Each element is identified by an index number, and these index numbers are used to access the array. Arrays provide many methods for managing data sets. For example, you can add a new element to the array with the push method, while you can remove the last element with the **pop** method. In addition, methods such as **map**, **filter**, and **reduce** allow you to perform more complex operations on arrays.

```javascript
// Array of fruits
const fruits = ['apple', 'banana', 'orange'];

// Adding a new fruit to the array
fruits.push('grape'); // Adds 'grape' to the end of the array
console.log(fruits); // Output: ['apple', 'banana', 'orange', 'grape']

// Removing the last fruit from the array
const lastFruit = fruits.pop(); // Removes the last element
console.log(lastFruit); // Output: 'grape'
console.log(fruits); // Output: ['apple', 'banana', 'orange']

// Using map to create a new array with the lengths of each fruit's name
const fruitLengths = fruits.map(fruit => fruit.length);
console.log(fruitLengths); // Output: [5, 6, 6]
```

## Objects

Objects are one of the fundamental building blocks for storing data in JavaScript. They store data in the form of key-value pairs, making them incredibly useful for grouping and organizing information. Each key acts as a unique identifier, allowing easy access to the associated data. For instance, a user object can contain keys like name, age, and email:

```javascript
const user = {
    name: 'Alice',
    age: 30,
    email: 'alice@example.com'
};
```
Within this object, you can access related information using its keys. This structure allows for a more systematic management of data. For example, you can directly access the user's information using the keys:

```javascript
console.log(user.name); // Output: Alice
console.log(user['age']); // Output: 30
```

## CRUD (Create, Read, Update, Delete) Operations

When working with objects, four fundamental operations are typically used: Create, Read, Update, and Delete. These operations enable you to effectively manage the data.

- **Create:** You can create a new object by defining key-value pairs. For example:

```javascript
//Create
const product = {
    id: 1,
    name: 'Laptop',
    price: 1200
};
```

- **Read:** To access the values within an existing object, you use the keys. For instance, you can read the name value from the product object:

```javascript
//Read
console.log(product.name); // Output: Laptop
```
- **Update:** Updating the properties of an existing object is straightforward. You can change the value associated with a specific key:

```javascript
//Update
product.price = 1100; // Update
console.log(product.price); // Output: 1100

```

- **Delete:** To remove an unnecessary or unused key-value pair, you can use the delete keyword:

```javascript
//Delete

delete product.id; // Delete
console.log(product); // Output: { name: 'Laptop', price: 1100 }


```


## Sample Application: Creating a User Profile

In the following example, we will create a simple user profile using an array and an object. This profile will hold the names and ages of the users and print the users in the array to the console.

```javascript
// Creating an array of user profiles
const users = [
    { name: 'Alice', age: 25 },
    { name: 'Bob', age: 30 },
    { name: 'Charlie', age: 28 }
];

// Logging user profiles to the console
users.forEach(user => {
    // Outputting each user's name and age
    console.log(`Name: ${user.name}, Age: ${user.age}`);
});

// Adding a new user to the array
users.push({ name: 'David', age: 22 });
console.log('Updated user list:');
users.forEach(user => {
    console.log(`Name: ${user.name}, Age: ${user.age}`);
});
```
In this code, we created an array containing user profiles and printed the name and age of each user to the console using the forEach method. Then, we added a new user using the push method. We used the find method to search for users and found a specific user. This is a comprehensive example of how to manipulate arrays and objects.


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)