**PRACTICAL NO 1
**
Stack Implementation using List in Python

stack = []

# Push Operation
def push(item):
    stack.append(item)
    print(f"{item} pushed into stack")

# Pop Operation
def pop():
    if len(stack) == 0:
        print("Stack Underflow! Stack is empty.")
    else:
        print(f"{stack.pop()} popped from stack")

# Peek Operation
def peek():
    if len(stack) == 0:
        print("Stack is empty.")
    else:
        print(f"Top element is: {stack[-1]}")

# Display Stack
def display():
    print("Stack:", stack)

# Demonstration
push(10)
push(20)
push(30)

display()

peek()      

pop()      
display()

peek()     

**PRACTICAL NO 2
1. Queue Using Array (Python List) 

class QueueArray:
    def __init__(self):
        self.queue = []
    def enqueue(self, item):
        self.queue.append(item)
    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
            return None
        return self.queue.pop(0)
    def peek(self):
        if self.is_empty():
            return None
        return self.queue[0]
    def is_empty(self):
        return len(self.queue) == 0
    def size(self):
        return len(self.queue)
    def display(self):
        print("Queue:", self.queue)


# Example Usage
q = QueueArray()

q.enqueue(10)
q.enqueue(20)
q.enqueue(30)

q.display()

print("Dequeued:", q.dequeue())
print("Front Element:", q.peek())

q.display()
print("Size:", q.size())


2. Queue Using Linked List 

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class QueueLinkedList:
    def __init__(self):
        self.front = None
        self.rear = None
    def enqueue(self, item):
        new_node = Node(item)
        if self.rear is None:
            self.front = self.rear = new_node
            return
        self.rear.next = new_node
        self.rear = new_node
    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
            return None
        temp = self.front
        self.front = self.front.next
        if self.front is None:
            self.rear = None
        return temp.data
    def peek(self):
        if self.is_empty():
            return None
        return self.front.data
    def is_empty(self):
        return self.front is None
    def display(self):
        temp = self.front
        print("Queue:", end=" ")
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example Usage
q = QueueLinkedList()

q.enqueue(10)
q.enqueue(20)
q.enqueue(30)

q.display()

print("Dequeued:", q.dequeue())
print("Front Element:", q.peek())

q.display()


**PRACTICAL NO 3
**
Singly Linked List Operations: Write a program to
implement a Singly Linked List with the following
operations:
● Insert at beginning
● Insert at end
● Insert at given position
● Delete from beginning
● Delete from end
● Search an element
● Display list


class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
    def insert_begin(self, data):
        new = Node(data)
        new.next = self.head
        self.head = new
    def insert_end(self, data):
        new = Node(data)
        if self.head is None:
            self.head = new
        else:
            temp = self.head
            while temp.next:
                temp = temp.next
            temp.next = new
    def insert_pos(self, data, pos):
        if pos == 1:
            self.insert_begin(data)
            return
        temp = self.head
        for i in range(pos - 2):
            if temp is None:
                print("Invalid Position")
                return
            temp = temp.next
        new = Node(data)
        new.next = temp.next
        temp.next = new
    def delete_begin(self):
        if self.head:
            self.head = self.head.next
        else:
            print("List is empty")
    def delete_end(self):
        if self.head is None:
            print("List is empty")
        elif self.head.next is None:
            self.head = None
        else:
            temp = self.head
            while temp.next.next:
                temp = temp.next
            temp.next = None
    def search(self, key):
        temp = self.head
        pos = 1
        while temp:
            if temp.data == key:
                print("Element found at position", pos)
                return
            temp = temp.next
            pos += 1
        print("Element not found")
    def display(self):
        if self.head is None:
            print("List is empty")
            return
        temp = self.head
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")

l = LinkedList()

while True:
    print("\n1.Insert at Beginning")
    print("2.Insert at End")
    print("3.Insert at Position")
    print("4.Delete from Beginning")
    print("5.Delete from End")
    print("6.Search")
    print("7.Display")
    print("8.Exit")
    ch = int(input("Enter your choice: "))
    if ch == 1:
        x = int(input("Enter element: "))
        l.insert_begin(x)
    elif ch == 2:
        x = int(input("Enter element: "))
        l.insert_end(x)
    elif ch == 3:
        x = int(input("Enter element: "))
        p = int(input("Enter position: "))
        l.insert_pos(x, p)
    elif ch == 4:
        l.delete_begin()
    elif ch == 5:
        l.delete_end()
    elif ch == 6:
        x = int(input("Enter element to search: "))
        l.search(x)
    elif ch == 7:
        l.display()
    elif ch == 8:
        print("Program Ended")
        break
    else:
        print("Invalid Choice")


**PRACTICAL NO 4
**
Binary Tree Traversals: Write a program to create a Binary
Tree. Implement Preorder, Inorder, and Postorder Traversals.


# Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None


# Preorder Traversal (Root -> Left -> Right)
def preorder(root):
    if root:
        print(root.data, end=" ")
        preorder(root.left)
        preorder(root.right)


# Inorder Traversal (Left -> Root -> Right)
def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=" ")
        inorder(root.right)


# Postorder Traversal (Left -> Right -> Root)
def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" ")


# Create Binary Tree
root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)
root.right.left = Node(6)
root.right.right = Node(7)

# Display Traversals
print("Preorder Traversal:")
preorder(root)

print("\n\nInorder Traversal:")
inorder(root)

print("\n\nPostorder Traversal:")
postorder(root)

Tree
        1
      /   \
     2     3
    / \   / \
   4   5 6   7
   
**PRACTICAL NO 5
**
Graph Representation and Traversals:
● Depth First Search (DFS)
● Breadth First Search (BFS)

DFS Implementation:-

# Undirected Graph
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}


def dfs(graph, node, visited):
    visited.add(node)
    print(node, end=" ")
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)


visited = set()

print("Graph:")
for vertex in graph:
    print(vertex, "->", graph[vertex])

print("\nDFS Traversal starting from vertex A:")
dfs(graph, 'A', visited)



BFS Implementation:-

from collections import deque

# Undirected Graph
graph = {
    1: [2, 3],
    2: [1, 4, 5],
    3: [1, 6],
    4: [2],
    5: [2, 6],
    6: [3, 5]
}

# BFS Function
def bfs(graph, start):
    visited = set()
    queue = deque()
    visited.add(start)
    queue.append(start)
    while queue:
        node = queue.popleft()
        print(node, end=" ")
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

print("Graph:")
for vertex in graph:
    print(vertex, "->", graph[vertex])

print("\nBFS Traversal starting from vertex 1:")
bfs(graph, 1)

**PRACTICAL NO 6
**
Shortest Path using Dijkstra's Algorithm: Implement
Dijkstra’s Algorithm to find the shortest path from a source
node to all other nodes in a weighted graph.


import heapq

# Weighted Graph
graph = {
    'A': [('B', 4), ('C', 2)],
    'B': [('A', 4), ('D', 5)],
    'C': [('A', 2), ('D', 3), ('E', 4)],
    'D': [('B', 5), ('C', 3), ('F', 2)],
    'E': [('C', 4), ('F', 3)],
    'F': [('D', 2), ('E', 3)]
}

# Dijkstra's Algorithm
def dijkstra(graph, source):
    distance = {vertex: float('inf') for vertex in graph}
    previous = {vertex: None for vertex in graph}
    distance[source] = 0
    priority_queue = [(0, source)]
    while priority_queue:
        current_distance, current_vertex = heapq.heappop(priority_queue)
        for neighbor, weight in graph[current_vertex]:
            new_distance = current_distance + weight
            if new_distance < distance[neighbor]:
                distance[neighbor] = new_distance
                previous[neighbor] = current_vertex
                heapq.heappush(priority_queue, (new_distance, neighbor))
    return distance, previous

# Function to display shortest path
def shortest_path(previous, destination):
    path = []
    while destination:
        path.append(destination)
        destination = previous[destination]
    return path[::-1]

# Driver Code
source = 'A'
distance, previous = dijkstra(graph, source)

print("Shortest Paths from Source:", source)

for vertex in graph:
    print(f"{source} -> {vertex}")
    print("Distance =", distance[vertex])
    print("Path =", " -> ".join(shortest_path(previous, vertex)))
    print()


**PRACTICAL NO 7
**
Write a program to compute MST (Minimum Spanning Tree) for a connected graph using Prim’s Algorithm.

Source code

graph = [
    [0, 2, 0, 6, 0],
    [2, 0, 3, 8, 5],
    [0, 3, 0, 0, 7],
    [6, 8, 0, 0, 9],
    [0, 5, 7, 9, 0]
]

n = len(graph)
selected = [False] * n
selected[0] = True

cost = 0

print("Edge\tWeight")

for _ in range(n - 1):
    minimum = 999
    x = y = 0
    for i in range(n):
        if selected[i]:
            for j in range(n):
                if not selected[j] and graph[i][j] != 0:
                    if graph[i][j] < minimum:
                        minimum = graph[i][j]
                        x, y = i, j
    print(x, "-", y, "\t", graph[x][y])
    cost += graph[x][y]
    selected[y] = True

print("Total Cost =", cost)

**PRACTICAL NO 8
**
Implementing and Analysing Sorting Algorithms:
● Bubble Sort,
● Insertion Sort
.Selection Sort

Practical 8a
● Bubble Sort:-
def bubble_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        swapped = False
        for j in range(n - 1 - i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break
    return arr


arr = [64, 34, 25, 12, 22, 11, 90]

print("Original Array:", arr)
print("Sorted Array:", bubble_sort(arr))


Practical 8b
● Insertion Sort:-
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr


arr = [64, 34, 25, 12, 22, 11, 90]

print("Original Array:", arr)
print("Sorted Array:", insertion_sort(arr))


Practical 8c
.Selection Sort:-
def selection_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        min_index = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr

arr = [64, 25, 12, 22, 11]

print("Original Array:", arr)
print("Sorted Array:", selection_sort(arr))

**PRACTICAL NO 9
**
Sorting Algorithm Performance Comparison:
● Merge Sort
● Quick Sort

import time
import random

# Merge Sort
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)


def merge(left, right):
    result = []
    i = 0
    j = 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result


# Quick Sort

def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[-1]
    left = []
    right = []
    for x in arr[:-1]:
        if x <= pivot:
            left.append(x)
        else:
            right.append(x)
    return quick_sort(left) + [pivot] + quick_sort(right)


# Performance Comparison

# Generate random data
data = [random.randint(1, 100) for _ in range(10)]

# Merge Sort
start = time.time()
merge_result = merge_sort(data.copy())
merge_time = time.time() - start

# Quick Sort
start = time.time()
quick_result = quick_sort(data.copy())
quick_time = time.time() - start
# Display results
print("Original Data (First 10):", data[:10])
print("\nMerge Sort Result (First 10):", merge_result[:10])
print("Merge Sort Time:", merge_time, "seconds")
print("\nQuick Sort Result (First 10):", quick_result[:10])
print("Quick Sort Time:", quick_time, "seconds")
# Compare
if merge_time < quick_time:
    print("\nMerge Sort is faster for this input.")
elif quick_time < merge_time:
    print("\nQuick Sort is faster for this input.")
else:
    print("\nBoth algorithms took approximately the same time.")

**   PRACTICAL NO 10
**
Searching Techniques Comparison Implement:
● Linear Search
● Binary Search

def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i
    return -1

def binary_search(arr, key):
    low = 0
    high = len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == key:
            return mid
        elif key < arr[mid]:
            high = mid - 1
        else:
            low = mid + 1
    return -1

# Input
arr = list(map(int, input("Enter elements separated by space: ").split()))
key = int(input("Enter element to search: "))

# Linear Search
linear_result = linear_search(arr, key)

if linear_result != -1:
    print("\nLinear Search: Element found at index", linear_result)
else:
    print("\nLinear Search: Element not found")


# Binary Search requires sorted data
sorted_arr = sorted(arr)

print("Sorted Array:", sorted_arr)

binary_result = binary_search(sorted_arr, key)

if binary_result != -1:
    print("Binary Search: Element found at index", binary_result)
else:
    print("Binary Search: Element not found")



