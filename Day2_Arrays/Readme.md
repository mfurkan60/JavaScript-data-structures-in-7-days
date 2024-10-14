# Day 2: Arrays


Introduction to Arrays
Arrays are fundamental data structures in JavaScript used to store ordered collections of data. They allow you to keep multiple values under a single variable, which helps in organizing and managing data systematically. Each element is identified by an index number that starts from zero. This index is used to access specific elements within the array. For example, you can create an array of fruits like this:




```javascript
const fruits = ['apple', 'banana', 'orange'];
```

In this array, **fruits[0]** accesses the value ***'apple'***, **fruits[1]** accesses ***'banana'***, and **fruits[2]** accesses ***'orange'***. Arrays not only make data more organized and accessible but also facilitate various operations and manipulations through built-in methods.


## Array Methods
JavaScript arrays come with many built-in methods that allow you to perform various operations on them. Here are some basic and advanced array methods:

**Basic Array Methods:**

- **push():** Adds one or more elements to the end of the array. This method increases the array's length.

- **pop():** Removes the last element from the array and returns it. This decreases the array's length.

- **shift():** Removes the first element from the array and returns it. This also decreases the array's length.

- **unshift():** Adds one or more elements to the beginning of the array, increasing its length.





```javascript
const numbers = [1, 2, 3];
numbers.push(4); // numbers: [1, 2, 3, 4]
console.log(numbers); // Output: [1, 2, 3, 4]

const lastNumber = numbers.pop(); // Returns 4; numbers: [1, 2, 3]
console.log(lastNumber); // Output: 4
console.log(numbers); // Output: [1, 2, 3]

```

**Advanced Array Methods:**

- **map():** Creates a new array by applying a specified function to each element in the original array.

- **filter():** Creates a new array with all elements that pass a test provided as a function.

- **reduce():** Reduces the array to a single value by executing a provided 

```javascript
function for each value (from left to right).

const numbers = [1, 2, 3, 4];

const doubled = numbers.map(num => num * 2); // [2, 4, 6, 8]
console.log(doubled);

const evens = numbers.filter(num => num % 2 === 0); // [2, 4]
console.log(evens);

const sum = numbers.reduce((acc, num) => acc + num, 0); // 10
console.log(sum);
``` 


## Application with Arrays

To reinforce what you've learned today, I recommend doing a simple application. Below is an example that takes user input for numbers, stores them in an array, and performs various operations on that array.

## Example Application: User Input for Numbers and Operations

This application will take numbers from the user, store them in an array, and then perform some operations on this array.


```javascript
// Create an empty array to hold user numbers
const userNumbers = [];

// Function to add a number to the array
function addNumber(num) {
    userNumbers.push(num);
}

// Function to display the numbers
function displayNumbers() {
    console.log('User Numbers:', userNumbers);
}

// Function to double the numbers in the array
function doubleNumbers() {
    return userNumbers.map(num => num * 2);
}

// Function to calculate the sum of the numbers
function sumNumbers() {
    return userNumbers.reduce((acc, num) => acc + num, 0);
}

// Adding numbers
addNumber(5);
addNumber(10);
addNumber(15);

// Displaying the numbers
displayNumbers(); // Output: User Numbers: [5, 10, 15]

// Doubling the numbers
const doubledNumbers = doubleNumbers();
console.log('Doubled Numbers:', doubledNumbers); // Output: [10, 20, 30]

// Calculating the sum of the numbers
const totalSum = sumNumbers();
console.log('Total Sum:', totalSum); // Output: 30
```


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)