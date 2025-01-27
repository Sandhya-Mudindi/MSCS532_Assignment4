def heapify(arr, n, i):
    """
    Maintains the max-heap property for a subtree rooted at index i.

    Parameters:
    arr (list): The array representing the heap.
    n (int): The size of the heap.
    i (int): The index of the root of the subtree.
    """
    largest = i  # Initialize largest as root
    left = 2 * i + 1  # Left child index
    right = 2 * i + 2  # Right child index

    # Check if left child exists and is greater than root
    if left < n and arr[left] > arr[largest]:
        largest = left

    # Check if right child exists and is greater than the current largest
    if right < n and arr[right] > arr[largest]:
        largest = right

    # If the largest element is not the root
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]  # Swap
        # Recursively heapify the affected subtree
        heapify(arr, n, largest)

def heapsort(arr):
    """
    Sorts an array in ascending order using the Heapsort algorithm.

    Parameters:
    arr (list): The array to be sorted.

    Returns:
    list: The sorted array.
    """
    n = len(arr)

    # Step 1: Build a max-heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # Step 2: Extract elements from the heap one by one
    for i in range(n - 1, 0, -1):
        # Move current root (max element) to the end
        arr[0], arr[i] = arr[i], arr[0]
        # Call heapify on the reduced heap
        heapify(arr, i, 0)

    return arr

# Example usage
if __name__ == "__main__":
    data = [12, 11, 13, 5, 6, 7]
    print("Original array:", data)
    sorted_data = heapsort(data)
    print("Sorted array:", sorted_data)
