# Day 3: Objects

## Introduction to Objects

Objects are one of the most efficient ways to organize and organize data structures in JavaScript. An object is a structure that holds data in the form of key-value pairs. A key is a name that identifies a property or value within an object, while a value can be the data that corresponds to that key. This structure is ideal for keeping and managing groups of data together. For example, we can create an object that holds information about a person:

 
```javascript
const person = {
    name: 'Alice',
    age: 30,
    job: 'Engineer'
};


```

In this example, the object named person contains three properties: name, age, and job. These properties allow us to store the user's information in a more organized way.

## Object Creation Methods
There are several different ways to create objects in JavaScript. One of the most common methods is to use an object literal. In this method, the object is defined with curly braces {}. You can also create objects using the new Object() construct:

```javascript
const car = new Object();
car.make = 'Toyota';
car.model = 'Camry';
car.year = 2021;
``` 

Both methods are valid, but the object literal is generally more readable and preferred.

## Accessing Object Properties

In JavaScript, there are two main methods for accessing properties within an object: dot notation and square bracket notation. These two methods are very effective for accessing and manipulating object data. Each method offers advantages for different scenarios.

- **Dot Notation:** Dot notation is the most widely used and most readable method. To access a property, we put a period (.) after the object name, followed by the name of the property. For example, let's access the name property of the person object in the following object example:

```javascript
const person = {
    name: 'Alice',
    age: 30,
    job: 'Engineer'
};
```

This method is extremely effective when the property names are known directly. However, dot notation has some limitations. The property name must be a valid JavaScript variable name. That is, names that contain special characters or spaces cannot be used. For example, it is not possible to use a property name like the following with dot notation:

```javascript
const car = {
    model: 'Camry',
    'manufacturing year': 2021 // Invalid for dot notation
};

console.log(car.model); // Valid
// console.log(car.'manufacturing year'); // SyntaxError


console.log(person.name); // Output: Alice

```

## Square Bracket Notation:

Square bracket notation is another way to access object properties and provides more flexibility. We use it by writing the property name as a string in square brackets. This method allows us to use property names that contain special characters or are taken from variables. For example:

```javascript
const car = {
    model: 'Camry',
    'manufacturing year': 2021
};

console.log(car['model']); // Output: Camry
console.log(car['manufacturing year']); // Output: 2021
``` 

The square bracket notation is especially useful in cases where property names are determined dynamically. For example, we can access the property name using a variable:

```javascript
const propertyName = 'age';
console.log(person[propertyName]); // Output: 30
``` 

This is an important point to consider when deciding which method to use when working with objects. If the property name is known in advance and is a valid variable name, dot notation is preferable. However, if the property names are dynamic or contain special characters, square bracket notation should be used.

Accessing object properties is one of the cornerstones of the JavaScript programming language and allows efficient management of objects. Using these methods, you can access, update, or delete data within objects.

## Object Methods

One of the strengths of objects is that they can define functions inside them. These functions are called methods of the object. Methods are used to define operations associated with the object and provide access to the properties of the object. This structure increases the behavior and functionality of objects. When you create an object, adding functions that can interact with its properties as well as its properties makes your code more organized and meaningful.

## Defining Methods:

Methods are defined inside the object definition and are usually added as a key-value pair. The key specifies the name of the method, while the value is a function. In the following example, we create a person object and define a method inside it:

```javascript
const person = {
    name: 'Alice',
    age: 30,
    greet: function() {
        console.log(`Hello, my name is ${this.name}.`);
    }
};

// Calling the method
person.greet(); // Output: Hello, my name is Alice.

``` 

In this example, the greet method accesses the name property of the person object. The this keyword refers to the current object, so the expression this.name returns the name property of the person object. This is a good example of how to access data and integrate functions within an object.

**The this Keyword in Methods:**

The this keyword is used to specify the context of a method. Inside a method, this refers to the object that is calling that method. This makes it easy to access object properties. For example:

``` javascript
const car = {
    make: 'Toyota',
    model: 'Camry',
    getDetails: function() {
        return `${this.make} ${this.model}`;
    }
};

console.log(car.getDetails()); // Output: Toyota Camry
``` 

Here, the getDetails method accesses the make and model properties of the car object using this.

**Usage and Importance of Methods:**

Methods are used to model the behavior of objects. For example, you can add a method to update the information of a user object:

``` javascript
const user = {
    username: 'john_doe',
    email: 'john@example.com',
    updateEmail: function(newEmail) {
        this.email = newEmail; // Updating the email property
    }
};

user.updateEmail('john.doe@example.com');
console.log(user.email); // Output: john.doe@example.com
``` 

In this example, the updateEmail method lets us interact with the object by updating the user’s email address.

Object methods make your code more modular because you can hide certain functionality within the object, making it inaccessible to the outside. This way, you can use the functionality specific to your objects only in the context of that object.

Ultimately, object methods in JavaScript allow you to manage and interact with your data more effectively. Understanding and using methods is key to developing powerful and dynamic JavaScript applications.

## Implementation of Objects
To reinforce what you have learned today, I propose to make a simple application that manages user information with an object. This application will help you understand how to use JavaScript objects, how to access and update properties. Below is a detailed example that creates an object that holds user information and updates the information through this object.

**Sample Application: Managing User Information**

This application will create an object that holds information such as username, email, and age, and will allow you to update the user's information. We will also add a method to display the user information.


``` javascript
// User object creation
const user = {
    username: 'john_doe',
    email: 'john@example.com',
    age: 25,
    // Method to display user information
    displayInfo: function() {
        console.log(`Username: ${this.username}`);
        console.log(`Email: ${this.email}`);
        console.log(`Age: ${this.age}`);
    },
    // Method to update the user's email
    updateEmail: function(newEmail) {
        this.email = newEmail;
        console.log(`Email updated to: ${this.email}`);
    },
    // Method to update the user's age
    updateAge: function(newAge) {
        if (newAge > 0) {
            this.age = newAge;
            console.log(`Age updated to: ${this.age}`);
        } else {
            console.log('Please enter a valid age.');
        }
    }
};

// Display initial user information
console.log('Initial User Information:');
user.displayInfo();

// Update the user's email
user.updateEmail('john.doe@example.com');

// Update the user's age
user.updateAge(30);

// Attempt to set an invalid age
user.updateAge(-5);

// Display updated user information
console.log('Updated User Information:');
user.displayInfo();
``` 

## Application Explanation:

**Object Creation:** First, we create an object named user. This object holds three properties: username, email, and age.

**Defining Methods:**

- **displayInfo:** This method prints the user's information to the console. The this keyword allows access to the object's properties.
- **updateEmail:** This method takes a new email address as an argument and updates the user's email.
- **updateAge:** This method takes a new age as an argument and updates the user's age. It also checks whether the entered age is valid.

**Displaying and Updating Information:** At the beginning of the application, the user's information is displayed using the displayInfo method. Then, the updateEmail and updateAge methods are called to update the user's information. Finally, the updated information is displayed again.

**Invalid Input Check:** The updateAge method checks whether the age entered by the user is valid. This makes the application more reliable and user-friendly.

This example will help you understand how to use objects and methods, while also reinforcing the basic principles of working with JavaScript data structures. In real-world applications, objects are often used for data management and business logic, so it's important to have a good understanding of this concept.
 


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)