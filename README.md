# MSCS532 Assignment 4

This repository contains implementations for various algorithms and data structures as part of Assignment 4. Each file demonstrates a specific concept, showcasing examples and performance analysis.

## Files and How to Run Them

### 1. `Heap Sort.py`
- **Description**: It contains the implementation of the Heap Sort algorithm.
- **How to Run**:
    ```bash
    python Heap Sort.py
    ```

### 2. `Priority Queue.py`
- **Description**: Implements a Priority Queue using a Binary Heap with task scheduling features.
- **How to Run**:
    ```bash
    python Priority Queue.py
    ```

### 3. `Heap and Quick Sort.py`
- **Description**: Implements a Heap and Quick Sort and performance times for heap and quick sort.
- **How to Run**:
    ```bash
    python Heap and Quick Sort.py
    ```


###  **`Summary of Findings`**

- Heap Sort is a comparison-based sorting algorithm that builds a Max-Heap and repeatedly extracts the maximum element while adjusting the heap. It operates with a consistent time complexity of O(n log n) in the worst, average, and best cases, regardless of input distribution. The space complexity of Heap Sort is O(1) as it sorts in-place, though recursive heapify calls add small overheads. Compared to Quick Sort, Heap Sort is less efficient, as Quick Sort's adaptive partitioning strategy leads to better performance, especially for larger datasets. While Heap Sort offers predictable performance, it is slower than Quick Sort in practical use, especially for large input sizes.
- The task scheduling system uses a max-heap to manage tasks based on priority, ensuring higher-priority tasks are executed first. The Task class represents tasks with attributes such as task_id, priority, arrival_time, and deadline, and overrides the __lt__ method to compare tasks by priority. The custom MaxHeap class provides key operations like insert, extract_max, and increase_key/decrease_key to manage tasks. Heapify operations (_heapify_up and _heapify_down) maintain the heap property after task insertion, extraction, or priority modification. The time complexity for insertion and extraction is O(log n), while priority modifications require O(n) due to the search step. Overall, the system is efficient for real-time scheduling with moderate numbers of tasks, though priority modifications can become costly in larger systems.
