# Algo

### **What is Quick Sort?**

Quick Sort is a **divide-and-conquer** algorithm that sorts an array by partitioning it into smaller subarrays around a pivot element. It recursively applies the same logic to the subarrays until the array is sorted.

---

### **Theory**

### **How Does It Work?**

1. **Divide**:
    - Choose a pivot element from the array.
    - Partition the array into two subarrays:
        - Elements **smaller** than the pivot.
        - Elements **greater** than or **equal to** the pivot.
2. **Conquer**:
    - Recursively apply the same process to the subarrays (left and right).
3. **Combine**:
    - The sorted left subarray, the pivot, and the sorted right subarray are combined to form the final sorted array.

---

### **Steps with an Example**

Input Array: `[10, 7, 8, 9, 1, 5]`

1. **Choose Pivot**: Select the last element as the pivot (e.g., `5`).
2. **Partition**: Rearrange the array such that:
    - Left Subarray: `[1]` (elements smaller than `5`)
    - Pivot: `[5]`
    - Right Subarray: `[10, 7, 8, 9]` (elements greater than `5`)
3. **Recursively Sort**:
    - Apply Quick Sort to `[1]` (left subarray) and `[10, 7, 8, 9]` (right subarray).
4. **Combine**:
    - Combine `[1]`, `[5]`, and the sorted right subarray.

Output: `[1, 5, 7, 8, 9, 10]`

---

### **Characteristics**

- **Best Case Time Complexity**: `O(nlogn)` (when the pivot divides the array evenly).
- **Worst Case Time Complexity**: O(n2) (when the pivot is the smallest or largest element every time).
- **Space Complexity**: `O(logn)` for the recursion stack.

---

### **Code Implementation**

Now, let’s implement the algorithm step by step.

```python

def quick_sort(arr):
    """
    Perform Quick Sort on the given array.

    Args:
    arr (list): The array to be sorted.

    Returns:
    list: The sorted array.
    """
    # Step 1: Base Case - If the array has 0 or 1 element, it's already sorted
    if len(arr) <= 1:
        return arr

    # Step 2: Choose a Pivot - Here, we select the last element as the pivot
    pivot = arr[-1]

    # Step 3: Partition the Array
    smaller, equal, larger = [], [], []  # Initialize three lists
    for num in arr:
        if num < pivot:  # Numbers smaller than the pivot
            smaller.append(num)
        elif num == pivot:  # Numbers equal to the pivot
            equal.append(num)
        else:  # Numbers larger than the pivot
            larger.append(num)

    # Step 4: Recursively Sort the Smaller and Larger Arrays
    # Combine the sorted smaller array, pivot(s), and sorted larger array
    return quick_sort(smaller) + equal + quick_sort(larger)

# Example usage
arr = [10, 7, 8, 9, 1, 5]  # Input array
print("Original Array:", arr)  # Unsorted array
sorted_arr = quick_sort(arr)  # Apply Quick Sort
print("Sorted Array:", sorted_arr)  # Output the sorted array

```

---

### **Step-by-Step Execution of Code**

1. **Input**: `[10, 7, 8, 9, 1, 5]`
2. **Choose Pivot**: `5`
    - Partition into:
        - `smaller = [1]`
        - `equal = [5]`
        - `larger = [10, 7, 8, 9]`
3. **Recursive Call** on `smaller` (`[1]`):
    - Base Case: Array is already sorted.
4. **Recursive Call** on `larger` (`[10, 7, 8, 9]`):
    - Pivot: `9`
    - Partition into:
        - `smaller = [7, 8]`
        - `equal = [9]`
        - `larger = [10]`
5. **Recursive Call** on `smaller` of `[7, 8]`:
    - Pivot: `8`
    - Partition into:
        - `smaller = [7]`
        - `equal = [8]`
        - `larger = []`
6. **Combine Results**:
    - `[1] + [5] + [7, 8] + [9] + [10] = [1, 5, 7, 8, 9, 10]`

---

### **Output**

```jsx

Original Array: [10, 7, 8, 9, 1, 5]
Sorted Array: [1, 5, 7, 8, 9, 10]

```

### **Quick Sort Simplified Summary**

1. **Concept**: Quick Sort is a **divide-and-conquer** sorting algorithm. It works by:
    - Picking a **pivot**.
    - Partitioning the array into:
        - Smaller elements (less than the pivot).
        - Larger elements (greater than or equal to the pivot).
    - Recursively sorting these parts.
2. **Steps**:
    1. Pick a pivot (e.g., last element).
    2. Divide the array into:
        - Smaller elements.
        - Larger elements.
    3. Recursively sort the smaller and larger arrays.
    4. Combine the sorted parts and the pivot.
3. **Code**:

```python

def quick_sort(arr):
    if len(arr) <= 1:  # Base case: already sorted
        return arr
    pivot = arr[-1]  # Choose the last element as pivot
    smaller = [x for x in arr if x < pivot]  # Elements smaller than pivot
    equal = [x for x in arr if x == pivot]  # Elements equal to pivot
    larger = [x for x in arr if x > pivot]  # Elements larger than pivot
    return quick_sort(smaller) + equal + quick_sort(larger)  # Recursive sort

```

1. **Example**:
    - Input: `[10, 7, 8, 9, 1, 5]`
    - Output: `[1, 5, 7, 8, 9, 10]`
2. **Time Complexity**:
    - Best/Average: `O(nlogn)`
    - Worst: `O(n2)` (if pivot selection is poor)

### **What is Merge Sort?**

Merge Sort is a sorting algorithm that splits the array into smaller parts, sorts those parts, and then merges them back into a sorted array.

---

### **How Does It Work?**

1. **Split the Array**:
    - Divide the array into two halves until each part has 1 element (a single element is already sorted).
2. **Merge the Parts**:
    - Compare elements from the two parts and merge them into a sorted array.

---

### **Steps with Example**

### Input: `[10, 7, 8, 9, 1, 5]`

1. **Divide**:
    - Split the array into two halves:
        - Left: `[10, 7, 8]`
        - Right: `[9, 1, 5]`
    - Recursively split each half until you have single elements:
        - `[10]`, `[7]`, `[8]`, `[9]`, `[1]`, `[5]`
2. **Merge**:
    - Compare and combine the single elements into sorted pairs:
        - `[7, 10]` from `[10]` and `[7]`
        - `[8]` remains as is (since it has no pair yet).
        - `[1, 9]` from `[9]` and `[1]`
        - `[5]` remains as is.
    - Merge sorted pairs:
        - `[7, 8, 10]` from `[7, 10]` and `[8]`
        - `[1, 5, 9]` from `[1, 9]` and `[5]`.
    - Merge final halves:
        - `[1, 5, 7, 8, 9, 10]` from `[7, 8, 10]` and `[1, 5, 9]`.

---

### **Python Code**

```python

def merge_sort(arr):
    # Step 1: Base case - If the array has 1 or no elements, it's already sorted
    if len(arr) <= 1:
        return arr

    # Step 2: Split the array into two halves
    mid = len(arr) // 2
    left = arr[:mid]
    right = arr[mid:]

    # Step 3: Recursively sort both halves
    sorted_left = merge_sort(left)
    sorted_right = merge_sort(right)

    # Step 4: Merge the sorted halves
    return merge(sorted_left, sorted_right)

def merge(left, right):
    sorted_array = []  # To store the merged result
    i = j = 0

    # Compare elements from both arrays and merge them in sorted order
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_array.append(left[i])
            i += 1
        else:
            sorted_array.append(right[j])
            j += 1

    # Add any remaining elements from both arrays
    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])

    return sorted_array

# Example Usage
arr = [10, 7, 8, 9, 1, 5]
print("Original Array:", arr)  # Display original unsorted array
sorted_arr = merge_sort(arr)
print("Sorted Array:", sorted_arr)  # Display sorted array

```

---

### **Output**

```jsx

Original Array: [10, 7, 8, 9, 1, 5]
Sorted Array: [1, 5, 7, 8, 9, 10]

```

---

### **Key Points**

1. **Base Case**: If the array has 1 or no elements, it’s already sorted.
2. **Divide**: Split the array into two halves.
3. **Merge**: Combine two sorted halves into a single sorted array.
4. **Recursive Calls**: Repeat the process until every element is individually sorted and merged.