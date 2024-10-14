# Day 5: Linked Lists


## Singly Linked Lists and Doubly Linked Lists

A singly linked list is made up of nodes, where each node contains two parts: the data and a reference to the next node in the sequence. This allows for efficient traversal and manipulation of the list.

In contrast, a doubly linked list contains nodes with three parts: the data, a reference to the next node, and a reference to the previous node. This bidirectional structure enables more versatile operations, such as traversing the list in either direction.

## Advantages of Linked Lists
Linked lists offer several benefits compared to other data structures:

- **Dynamic Size:** Unlike arrays, linked lists can easily grow and shrink as elements are added or removed. This means that memory can be utilized more efficiently.

- **Efficient Insertions and Deletions:** Adding or removing elements in a linked list does not require shifting other elements, as is the case with arrays. Instead, pointers are adjusted, which makes these operations more efficient, particularly for larger datasets.

- **Memory Efficiency:** Linked lists allocate memory for each node as needed, which can lead to better memory utilization, especially in cases where the number of elements fluctuates.


Here’s a simple implementation of a singly linked list in JavaScript:



```javascript
class Node {
    constructor(data) {
        this.data = data; // Store the data
        this.next = null; // Initialize the next pointer to null
    }
}

class SinglyLinkedList {
    constructor() {
        this.head = null; // Initialize the head of the list
        this.size = 0; // Track the size of the list
    }

    // Add a new node at the end of the list
    append(data) {
        const newNode = new Node(data); // Create a new node
        if (!this.head) {
            this.head = newNode; // If the list is empty, set the new node as head
        } else {
            let current = this.head;
            while (current.next) {
                current = current.next; // Traverse to the end of the list
            }
            current.next = newNode; // Link the new node
        }
        this.size++; // Increment the size of the list
    }

    // Remove a node by value
    remove(data) {
        if (!this.head) return; // If the list is empty, do nothing
        if (this.head.data === data) {
            this.head = this.head.next; // Remove the head
            this.size--;
            return;
        }
        let current = this.head;
        while (current.next) {
            if (current.next.data === data) {
                current.next = current.next.next; // Bypass the node to be removed
                this.size--;
                return;
            }
            current = current.next;
        }
    }

    // Print the list
    printList() {
        let current = this.head;
        let result = '';
        while (current) {
            result += current.data + ' -> ';
            current = current.next;
        }
        console.log(result + 'null'); // Display the list
    }
}

// Example usage
const taskList = new SinglyLinkedList();
taskList.append('Task 1');
taskList.append('Task 2');
taskList.printList(); // Output: Task 1 -> Task 2 -> null
taskList.remove('Task 1');
taskList.printList(); // Output: Task 2 -> null

```

## Application
In this section, we will create a data structure using a linked list to manage a task list (to-do list). This task list will enable users to efficiently add, remove, and display tasks, providing a flexible and dynamic way to manage their daily activities.

## Overview of the Task List Application

The task list application will leverage a singly linked list to store tasks as nodes, each containing a task description. By utilizing a linked list, we can benefit from its dynamic size and efficient operations, such as adding and removing tasks without needing to shift other elements.

**Key Features:**

- **Adding Tasks:** Users can add new tasks to the end of the list. This is accomplished using the append method, which creates a new node with the task description and links it to the current end of the list.

- **Removing Tasks:** Users can remove tasks by specifying the task description. The remove method searches for the task in the list and adjusts the pointers accordingly to remove it. If the task is found at the head of the list, it updates the head to the next node.

- **Displaying Tasks:** The printList method provides a visual representation of the current tasks in the list. This allows users to easily see what needs to be done.


Here’s a more detailed breakdown of the SinglyLinkedList implementation, focusing on the task management functionalities:


```javascript
class Node {
    constructor(data) {
        this.data = data; // Store the task description
        this.next = null; // Initialize the next pointer to null
    }
}

class SinglyLinkedList {
    constructor() {
        this.head = null; // Initialize the head of the list
        this.size = 0; // Track the size of the list
    }

    // Add a new task to the end of the list
    append(task) {
        const newNode = new Node(task); // Create a new node for the task
        if (!this.head) {
            this.head = newNode; // If the list is empty, set the new node as head
        } else {
            let current = this.head;
            while (current.next) {
                current = current.next; // Traverse to the end of the list
            }
            current.next = newNode; // Link the new node to the end of the list
        }
        this.size++; // Increment the size of the list
        console.log(`Task added: ${task}`); // Provide feedback to the user
    }

    // Remove a task by its description
    remove(task) {
        if (!this.head) return console.log("Task list is empty"); // Check if the list is empty
        if (this.head.data === task) {
            this.head = this.head.next; // Remove the head if it matches the task
            this.size--;
            console.log(`Task removed: ${task}`);
            return;
        }
        let current = this.head;
        while (current.next) {
            if (current.next.data === task) {
                current.next = current.next.next; // Bypass the node to be removed
                this.size--;
                console.log(`Task removed: ${task}`);
                return;
            }
            current = current.next;
        }
        console.log(`Task not found: ${task}`); // Feedback if task is not found
    }

    // Print the list of current tasks
    printList() {
        let current = this.head;
        let result = 'Task List: ';
        while (current) {
            result += `${current.data} -> `;
            current = current.next;
        }
        console.log(result + 'null'); // Display the complete task list
    }
}

// Example usage
const taskList = new SinglyLinkedList();
taskList.append('Complete project report');
taskList.append('Attend team meeting');
taskList.printList(); // Output: Task List: Complete project report -> Attend team meeting -> null
taskList.remove('Complete project report');
taskList.printList(); // Output: Task List: Attend team meeting -> null
taskList.remove('Go shopping'); // Output: Task not found: Go shopping

```
## User Interaction
Adding Tasks: When a user wants to add a task, they can call the append method with the task description as an argument. The application will create a new node for the task and add it to the end of the list, providing immediate feedback to confirm the addition.

- **Removing Tasks:** To remove a task, the user can call the remove method with the task description. The application will search for the task, and if found, it will remove it from the list and inform the user. If the task is not found, an appropriate message will be displayed.

- **Displaying Tasks:** Users can view all current tasks at any time by calling the printList method. This will output the entire list of tasks, making it easy to track what needs to be done.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)