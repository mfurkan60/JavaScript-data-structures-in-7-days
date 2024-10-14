# Day 7: Graphs


## Fundamental Components of Graphs

Graphs are versatile data structures that represent relationships between entities. Each graph consists of nodes (or vertices) connected by edges. These components work together to create a framework for modeling complex relationships, making graphs applicable in a variety of fields such as computer networking, biology, and social sciences.

**Usage of Graphs and Algorithms
Graphs are incredibly powerful tools for representing relationships and connections. They are used in many real-world applications:**

- **Social Networks:** Users are represented as nodes, while friendships or connections between them are represented as edges. This allows for the analysis of social interactions and community detection.
- **Navigation Systems:** Locations can be represented as nodes, with roads or paths as edges, enabling efficient route planning.
- **Web Page Linking:** Websites are nodes, and hyperlinks between them form the edges, allowing search engines to index and rank pages.


To navigate and manipulate graphs effectively, various algorithms are employed:

**Depth-First Search (DFS):**

DFS explores the graph by going as deep as possible along a branch before backtracking. It is implemented using a stack (or recursion) and is useful for tasks like maze solving and topological sorting.



```javascript
function dfs(graph, start, visited = new Set()) {
    if (!visited.has(start)) {
        visited.add(start); // Mark the node as visited
        console.log(start); // Process the node
        for (const neighbor of graph[start]) {
            dfs(graph, neighbor, visited); // Recur for each neighbor
        }
    }
}
```

**Breadth-First Search (BFS):**

BFS explores the graph layer by layer, visiting all neighbors at the present depth before moving on to nodes at the next depth level. This is particularly useful for finding the shortest path in unweighted graphs.

```javascript
function bfs(graph, start) {
    const visited = new Set();
    const queue = [start]; // Initialize the queue with the starting node

    while (queue.length > 0) {
        const node = queue.shift(); // Dequeue the first node
        if (!visited.has(node)) {
            visited.add(node); // Mark the node as visited
            console.log(node); // Process the node
            for (const neighbor of graph[node]) {
                queue.push(neighbor); // Enqueue all unvisited neighbors
            }
        }
    }
}
```

## Code Examples

Here’s a simple implementation of a graph structure in JavaScript, along with examples of DFS and BFS:

```javascript
class Graph {
    constructor() {
        this.adjacencyList = {}; // Initialize the adjacency list
    }

    // Add a vertex to the graph
    addVertex(vertex) {
        if (!this.adjacencyList[vertex]) {
            this.adjacencyList[vertex] = []; // Create an array for neighbors
        }
    }

    // Add an edge between two vertices
    addEdge(v1, v2) {
        this.adjacencyList[v1].push(v2); // Add v2 to v1's list
        this.adjacencyList[v2].push(v1); // Add v1 to v2's list (for undirected graph)
    }
}

// Example usage
const socialNetwork = new Graph();
socialNetwork.addVertex('Alice');
socialNetwork.addVertex('Bob');
socialNetwork.addVertex('Charlie');
socialNetwork.addEdge('Alice', 'Bob');
socialNetwork.addEdge('Alice', 'Charlie');

console.log(socialNetwork.adjacencyList);
// Output: { Alice: [ 'Bob', 'Charlie' ], Bob: [ 'Alice' ], Charlie: [ 'Alice' ] }

// Perform DFS and BFS
console.log("DFS Traversal:");
dfs(socialNetwork.adjacencyList, 'Alice'); // Output: Alice Bob Charlie

console.log("BFS Traversal:");
bfs(socialNetwork.adjacencyList, 'Alice'); // Output: Alice Bob Charlie
``` 

## Application

In this application, we will develop a simple graph model to represent a social network. In this model, each user will be represented as a node, while the connections (friendships) between users will be represented as edges. This structure will enable us to effectively manage and analyze social interactions within the network.

**Key Features of the Social Network Model**

**User Representation:**

Each user in the social network will be represented as a node (or vertex) in the graph. This allows us to encapsulate user-specific information such as usernames, profile details, and other relevant attributes.
The graph will support operations for adding new users, allowing the social network to grow dynamically as more members join.

**Friendship Connections:**
Connections between users will be represented as edges in the graph. These edges can be undirected (representing a mutual friendship) or directed (representing a one-sided following relationship, similar to platforms like Twitter).
The ability to establish and remove connections will allow users to manage their friendships, enhancing the interactivity of the social network.

**Graph Traversal:** We will implement algorithms such as Depth-First Search (DFS) and Breadth-First Search (BFS) to explore the graph. These algorithms will enable users to find friends, discover connections, and traverse the social network efficiently.
For example, using DFS, a user can explore all friends and their friends recursively, while BFS can help find the shortest path to a distant connection.

**Mutual Friendships:**
One useful feature will be the ability to find mutual friends between two users. By traversing the graph, we can identify common connections, fostering a sense of community and encouraging users to connect with each other.

**Network Analysis:** The application can be enhanced with analytical features such as:
Finding Isolated Users: Identifying users who have no connections, which could prompt actions to engage them more effectively.

**Degree of Separation:** Analyzing the degree of separation between two users, which can reveal insights into the network's structure.
Friend Recommendations: Suggesting potential friends based on shared connections, helping users expand their network.

**User Interface:** A simple user interface can be developed to allow users to interact with the social network. Users can add friends, view their connections, and explore the network visually.
Graph visualization tools can be integrated to represent the network visually, making it easier for users to understand their connections and relationships.
Implementation Example
Here’s a brief overview of how we might implement some of these features:

``` javascript

class SocialNetwork {
    constructor() {
        this.graph = new Graph(); // Initialize the graph for users
    }

    // Add a user to the network
    addUser(username) {
        this.graph.addVertex(username); // Create a new node for the user
    }

    // Add a friendship
    addFriendship(user1, user2) {
        this.graph.addEdge(user1, user2); // Create an edge between the two users
    }

    // Find mutual friends between two users
    findMutualFriends(user1, user2) {
        const friendsOfUser1 = new Set(this.graph.adjacencyList[user1]);
        const friendsOfUser2 = this.graph.adjacencyList[user2];
        const mutualFriends = friendsOfUser2.filter(friend => friendsOfUser1.has(friend));
        return mutualFriends;
    }

    // Display the network
    displayNetwork() {
        console.log(this.graph.adjacencyList);
    }
}

// Example usage
const myNetwork = new SocialNetwork();
myNetwork.addUser('Alice');
myNetwork.addUser('Bob');
myNetwork.addUser('Charlie');
myNetwork.addFriendship('Alice', 'Bob');
myNetwork.addFriendship('Alice', 'Charlie');

console.log("Social Network:");
myNetwork.displayNetwork(); // Output the current state of the network

console.log("Mutual Friends between Alice and Bob:", myNetwork.findMutualFriends('Alice', 'Bob'));

``` 

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)