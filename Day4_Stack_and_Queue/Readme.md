# Day 4: Stack and Queue

## Definition of Stack and Queue Data Structures

Stacks and queues are two fundamental data structures widely used in computer science, each serving distinct purposes based on the order in which data is processed. Understanding these structures is crucial for effective algorithm design and implementation, as they facilitate specific data handling mechanisms.

**Stack:** A stack is a collection of elements that follows the Last In First Out (LIFO) principle. In this structure, elements are added (pushed) to the top of the stack and also removed (popped) from the top. This behavior can be likened to a stack of plates; the last plate placed on top is the first one to be taken off. Stacks are particularly useful in scenarios that require backtracking or reversal of actions, such as undo operations in applications.

For example, in a text editor, when a user types or deletes text, each action can be pushed onto a stack. If the user decides to undo an action, the most recent action is popped from the stack, effectively reversing the last operation.

 
 


```javascript
class Stack {
    constructor() {
        this.items = [];
    }

    push(element) {
        this.items.push(element); // Add element to the top of the stack
    }

    pop() {
        if (this.isEmpty()) {
            return "Stack is empty";
        }
        return this.items.pop(); // Remove and return the top element
    }

    peek() {
        if (this.isEmpty()) {
            return "Stack is empty";
        }
        return this.items[this.items.length - 1]; // Return the top element without removing it
    }

    isEmpty() {
        return this.items.length === 0; // Check if the stack is empty
    }

    size() {
        return this.items.length; // Return the number of elements in the stack
    }
}

// Example usage
const stack = new Stack();
stack.push('Action 1');
stack.push('Action 2');
console.log(stack.pop()); // Output: Action 2
console.log(stack.peek()); // Output: Action 1

```

**Queue:** A queue, on the other hand, operates on the First In First Out (FIFO) principle. In this structure, elements are added (enqueued) to the end of the queue and removed (dequeued) from the front. This behavior is similar to a line of people waiting for service; the first person in line is the first to be served. Queues are essential in scenarios where order of processing is crucial, such as in print job management or handling tasks in a multi-threaded environment.

For example, in a printer queue, documents are lined up in the order they are submitted. The first document submitted will be printed first, while subsequent documents wait their turn.

Here’s a simple implementation of a queue in JavaScript:




```javascript
class Queue {
    constructor() {
        this.items = [];
    }

    enqueue(element) {
        this.items.push(element); // Add element to the end of the queue
    }

    dequeue() {
        if (this.isEmpty()) {
            return "Queue is empty";
        }
        return this.items.shift(); // Remove and return the first element
    }

    front() {
        if (this.isEmpty()) {
            return "Queue is empty";
        }
        return this.items[0]; // Return the first element without removing it
    }

    isEmpty() {
        return this.items.length === 0; // Check if the queue is empty
    }

    size() {
        return this.items.length; // Return the number of elements in the queue
    }
}

// Example usage
const queue = new Queue();
queue.enqueue('Document 1');
queue.enqueue('Document 2');
console.log(queue.dequeue()); // Output: Document 1
console.log(queue.front()); // Output: Document 2

``` 
Both stacks and queues are integral to computer science and software development, providing efficient methods for organizing and managing data as it flows through various processes. Understanding their behaviors and use cases is key to developing efficient algorithms and applications.

## Application
Let’s develop a stack application that simulates undo operations in a user interface. This type of functionality is crucial in many applications, such as text editors, graphic design software, and games, where users frequently need to revert to previous states.

**Overview of the Undo Operation:**

In this application, each time a user performs an action, such as typing text, drawing a shape, or modifying an image, that action is recorded in a stack. When the user decides to undo an action, the most recent action is removed from the stack and the application reverts to the previous state. This not only enhances user experience but also provides a safety net for accidental changes.

**How the Undo Stack Works:**

- **Action Recording:** Each action that modifies the application state is pushed onto the stack. This might include actions like adding text, deleting content, or making visual changes.

- **Undo Mechanism:** When the user triggers the undo function (often through a keyboard shortcut or a button), the application pops the last action off the stack and reverts to the previous state associated with that action. If the stack is empty, it indicates that there are no actions to undo.

- **Feedback to the User:** After each action and undo operation, feedback can be provided to the user to indicate what action was performed or reverted. This keeps the user informed of the current state.

Here’s a sample implementation of an Undo Stack in JavaScript:

``` javascript
class UndoStack {
    constructor() {
        this.actions = new Stack(); // Create a new stack for actions
    }

    performAction(action) {
        this.actions.push(action); // Add the action to the stack
        console.log(`Performed: ${action}`); // Log the action for feedback
    }

    undo() {
        const lastAction = this.actions.pop(); // Remove the last action
        if (lastAction) {
            console.log(`Undid: ${lastAction}`); // Log the undone action
            // Here, you would also include logic to revert the application's state
            // For example, if the action was "Draw Circle", you might remove the circle from the canvas.
        } else {
            console.log("No actions to undo"); // Indicate that there are no actions to undo
        }
    }

    // Method to view the current stack (for debugging purposes)
    viewActions() {
        console.log("Current Actions in Stack: ", this.actions.items);
    }
}

// Example usage
const undoStack = new UndoStack();
undoStack.performAction("Draw Circle");
undoStack.performAction("Draw Square");
undoStack.viewActions(); // Output: Current Actions in Stack:  [ 'Draw Circle', 'Draw Square' ]
undoStack.undo(); // Output: Undid: Draw Square
undoStack.undo(); // Output: Undid: Draw Circle
undoStack.undo(); // Output: No actions to undo
``` 

## Potential Enhancements:

- **Redo Functionality:** In addition to undo, you could implement a redo functionality that allows users to reapply an action they just undone. This can be achieved by maintaining a separate stack for redone actions.

- **Complex Actions:** If your application allows for complex actions (like a series of steps for a drawing or a multi-step form), you might need to store more detailed state information for each action, rather than just a string description.

- **User Interface Integration:** The undo and redo functions can be tied to keyboard shortcuts (like Ctrl+Z for undo and Ctrl+Y for redo) and buttons in the user interface to enhance usability.

- **Persistent History:** You could also implement a feature that allows users to save their actions and restore them later, making the application more versatile.

By implementing this undo stack, users will have greater control over their actions within the application, leading to a more intuitive and user-friendly experience.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)