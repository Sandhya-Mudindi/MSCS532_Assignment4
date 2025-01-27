class Task:
    def __init__(self, task_id, priority, arrival_time, deadline):
        """
        Initialize a task with an ID, priority, arrival time, and deadline.
        Args:
            task_id (int): Unique identifier for the task.
            priority (int): Priority of the task (lower values indicate higher priority).
            arrival_time (int): Time when the task arrives.
            deadline (int): Time by which the task must be completed.
        """
        self.task_id = task_id
        self.priority = priority
        self.arrival_time = arrival_time
        self.deadline = deadline

    def __lt__(self, other):
        """
        Define the less than comparison based on priority for heap structure.
        This is for building a max-heap (reverse for min-heap).
        Args:
            other (Task): The other task to compare to.
        Returns:
            bool: True if current task's priority is less than the other task's priority.
        """
        return self.priority < other.priority  # For max-heap, reverse comparison for min-heap

    def __repr__(self):
        """
        Define the string representation of the task object.
        Returns:
            str: A string representing the task's ID and priority.
        """
        return f"Task(ID={self.task_id}, Priority={self.priority})"

class MaxHeap:
    def __init__(self):
        """
        Initialize an empty max-heap.
        """
        self.heap = []

    def parent(self, index):
        """
        Get the index of the parent of a given node.
        Args:
            index (int): Index of the current node.
        Returns:
            int: Index of the parent node.
        """
        return (index - 1) // 2

    def left_child(self, index):
        """
        Get the index of the left child of a given node.
        Args:
            index (int): Index of the current node.
        Returns:
            int: Index of the left child node.
        """
        return 2 * index + 1

    def right_child(self, index):
        """
        Get the index of the right child of a given node.
        Args:
            index (int): Index of the current node.
        Returns:
            int: Index of the right child node.
        """
        return 2 * index + 2

    def is_empty(self):
        """
        Check if the heap is empty.
        Returns:
            bool: True if the heap is empty, False otherwise.
        """
        return len(self.heap) == 0

    def insert(self, task):
        """
        Insert a task into the heap and maintain heap properties.
        Args:
            task (Task): The task to be inserted into the heap.
        """
        self.heap.append(task)  # Add task to the end of the heap
        self._heapify_up(len(self.heap) - 1)  # Heapify upwards to restore heap property

    def extract_max(self):
        """
        Extract the task with the maximum priority (root of the heap).
        Returns:
            Task: The task with the highest priority.
        Raises:
            IndexError: If the heap is empty.
        """
        if self.is_empty():
            raise IndexError("Heap is empty")

        max_task = self.heap[0]  # The task with the highest priority (root)
        self.heap[0] = self.heap[-1]  # Move the last task to the root
        self.heap.pop()  # Remove the last task
        self._heapify_down(0)  # Heapify downwards to restore heap property
        return max_task

    def increase_key(self, task_id, new_priority):
        """
        Increase the priority of a task (must be higher than the current priority).
        Args:
            task_id (int): The ID of the task to update.
            new_priority (int): The new priority to set for the task.
        Raises:
            ValueError: If the new priority is lower than the current priority or task not found.
        """
        for i, task in enumerate(self.heap):
            if task.task_id == task_id:
                if new_priority < task.priority:
                    raise ValueError("New priority must be higher than current priority")
                self.heap[i].priority = new_priority  # Update priority
                self._heapify_up(i)  # Heapify upwards to restore heap property
                return
        raise ValueError("Task not found")

    def decrease_key(self, task_id, new_priority):
        """
        Decrease the priority of a task (must be lower than the current priority).
        Args:
            task_id (int): The ID of the task to update.
            new_priority (int): The new priority to set for the task.
        Raises:
            ValueError: If the new priority is higher than the current priority or task not found.
        """
        for i, task in enumerate(self.heap):
            if task.task_id == task_id:
                if new_priority > task.priority:
                    raise ValueError("New priority must be lower than current priority")
                self.heap[i].priority = new_priority  # Update priority
                self._heapify_down(i)  # Heapify downwards to restore heap property
                return
        raise ValueError("Task not found")

    def _heapify_up(self, index):
        """
        Restore the heap property by moving the node at the given index upwards.
        Args:
            index (int): Index of the node to heapify upwards.
        """
        while index > 0 and self.heap[self.parent(index)] < self.heap[index]:
            # Swap current node with its parent
            self.heap[self.parent(index)], self.heap[index] = self.heap[index], self.heap[self.parent(index)]
            index = self.parent(index)  # Move up to the parent's index

    def _heapify_down(self, index):
        """
        Restore the heap property by moving the node at the given index downwards.
        Args:
            index (int): Index of the node to heapify downwards.
        """
        max_index = index
        left = self.left_child(index)
        if left < len(self.heap) and self.heap[left] > self.heap[max_index]:
            max_index = left  # Update max_index if left child is larger

        right = self.right_child(index)
        if right < len(self.heap) and self.heap[right] > self.heap[max_index]:
            max_index = right  # Update max_index if right child is larger

        if index != max_index:
            # Swap current node with the largest child
            self.heap[index], self.heap[max_index] = self.heap[max_index], self.heap[index]
            self._heapify_down(max_index)  # Recursively heapify down

# Example Usage
def main():
    heap = MaxHeap()

    # Adding tasks to the heap
    heap.insert(Task(task_id=1, priority=5, arrival_time=0, deadline=10))
    heap.insert(Task(task_id=2, priority=3, arrival_time=1, deadline=15))
    heap.insert(Task(task_id=3, priority=8, arrival_time=2, deadline=20))

    print("Heap after insertions:", heap.heap)

    # Extracting the maximum priority task
    max_task = heap.extract_max()
    print("Extracted task with max priority:", max_task)
    print("Heap after extraction:", heap.heap)

    # Increasing priority of a task
    heap.increase_key(task_id=2, new_priority=10)
    print("Heap after increasing priority of task 2:", heap.heap)

    # Decreasing priority of a task
    heap.decrease_key(task_id=2, new_priority=4)
    print("Heap after decreasing priority of task 2:", heap.heap)

    # Check if heap is empty
    print("Is heap empty?:", heap.is_empty())

if __name__ == "__main__":
    main()
