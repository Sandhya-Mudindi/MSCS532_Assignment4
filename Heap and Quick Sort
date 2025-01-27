import random
import time

# Heapsort Implementation
def heapify(arr, n, i):
    """
    Function to maintain the heap property.
    Args:
        arr (list): List representing the heap.
        n (int): Size of the heap.
        i (int): Index of the current element to be heapified.
    """
    largest = i  # Initialize largest as root
    left = 2 * i + 1  # Left child index
    right = 2 * i + 2  # Right child index

    # If left child is larger than root, update largest
    if left < n and arr[left] > arr[largest]:
        largest = left

    # If right child is larger than largest, update largest
    if right < n and arr[right] > arr[largest]:
        largest = right

    # If largest is not root, swap and recursively heapify the affected subtree
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]  # Swap
        heapify(arr, n, largest)  # Recursively heapify the affected subtree

def heapsort(arr):
    """
    Main function to perform heapsort.
    Args:
        arr (list): List to be sorted.
    """
    n = len(arr)

    # Build max heap (rearrange the list to satisfy the heap property)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # Extract elements one by one from the heap
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]  # Swap root (max element) with last element
        heapify(arr, i, 0)  # Heapify the reduced heap

# Quicksort Implementation
def quicksort(arr):
    """
    Function to perform quicksort on the list.
    Args:
        arr (list): List to be sorted.
    Returns:
        list: Sorted list.
    """
    if len(arr) <= 1:  # Base case: list with 0 or 1 element is already sorted
        return arr
    pivot = arr[len(arr) // 2]  # Choose the middle element as the pivot
    left = [x for x in arr if x < pivot]  # Elements smaller than pivot
    middle = [x for x in arr if x == pivot]  # Elements equal to pivot
    right = [x for x in arr if x > pivot]  # Elements larger than pivot
    # Recursively sort the left and right sublists and combine them with the pivot
    return quicksort(left) + middle + quicksort(right)

# Function to generate different input distributions
def generate_input(size, distribution):
    """
    Function to generate different types of input distributions.
    Args:
        size (int): Number of elements in the input.
        distribution (str): Type of distribution ('sorted', 'reverse-sorted', or 'random').
    Returns:
        list: Generated list based on the specified distribution.
    """
    if distribution == "sorted":
        return list(range(size))  # Sorted list
    elif distribution == "reverse-sorted":
        return list(range(size, 0, -1))  # Reverse sorted list
    elif distribution == "random":
        return [random.randint(0, size) for _ in range(size)]  # Random list

# Function to measure the execution time of sorting algorithms
def measure_time(sort_func, arr):
    """
    Function to measure the execution time of a sorting algorithm.
    Args:
        sort_func (function): Sorting function (heapsort or quicksort).
        arr (list): List to be sorted.
    Returns:
        float: Time taken by the sorting function in seconds.
    """
    start_time = time.time()  # Record the start time
    sort_func(arr)  # Sort the list using the given sorting function
    return time.time() - start_time  # Calculate the elapsed time

# Input sizes and distributions for testing
input_sizes = [100, 8000, 12000, 30000]  # Different input sizes
distributions = ["sorted", "reverse-sorted", "random"]  # Different input distributions

# Run the experiments and print results
for size in input_sizes:
    print(f"\nInput size: {size}")
    for dist in distributions:
        print(f"\nDistribution: {dist}")

        # Heapsort
        arr = generate_input(size, dist)  # Generate input array
        heapsort_time = measure_time(heapsort, arr.copy())  # Measure heapsort time
        print(f"Heapsort time: {heapsort_time:.6f} seconds")

        # Quicksort
        arr = generate_input(size, dist)  # Generate input array
        quicksort_time = measure_time(quicksort, arr.copy())  # Measure quicksort time
        print(f"Quicksort time: {quicksort_time:.6f} seconds")
