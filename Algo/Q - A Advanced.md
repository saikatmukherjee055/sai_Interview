# Q - A : Advanced

### **1. Reverse a String Without Using `[::-1]`**

### **Question:**

Write a Python function to reverse a string without using slicing (`[::-1]`).

### **Solution:**

```python
python
CopyEdit
def reverse_string(s):
    reversed_s = "".join(reversed(s))
    return reversed_s

# Test
print(reverse_string("Deloitte"))  # Output: "ettieloD"

```

### **Explanation:**

- We use Python's built-in `reversed()` function, which returns an iterator.
- `"".join(reversed(s))` joins the characters to form the reversed string.

---

### **2. Count the Frequency of Words in a Sentence**

### **Question:**

Write a Python function to count the frequency of words in a given sentence.

### **Solution:**

```python
python
CopyEdit
from collections import Counter

def word_count(sentence):
    words = sentence.split()
    return dict(Counter(words))

# Test
print(word_count("Deloitte is hiring Python developers Deloitte"))
# Output: {'Deloitte': 2, 'is': 1, 'hiring': 1, 'Python': 1, 'developers': 1}

```

### **Explanation:**

- `split()` splits the sentence into words.
- `Counter(words)` counts the occurrences of each word.
- `dict()` converts the result into a dictionary.

---

### **3. Find the Missing Number in a Given List**

### **Question:**

Given a list containing `n` unique numbers in the range 1 to `n+1`, find the missing number.

### **Solution:**

```python
python
CopyEdit
def find_missing_number(nums):
    n = len(nums) + 1
    expected_sum = n * (n + 1) // 2
    actual_sum = sum(nums)
    return expected_sum - actual_sum

# Test
print(find_missing_number([1, 2, 4, 5, 6]))  # Output: 3

```

### **Explanation:**

- The sum of the first `n` numbers is calculated using `n(n+1)/2`.
- The difference between the expected and actual sum gives the missing number.

---

### **4. Check if a String is a Palindrome**

### **Question:**

Write a function to check if a given string is a palindrome.

### **Solution:**

```python
python
CopyEdit
def is_palindrome(s):
    return s == s[::-1]

# Test
print(is_palindrome("madam"))  # Output: True
print(is_palindrome("Deloitte"))  # Output: False

```

### **Explanation:**

- `s[::-1]` reverses the string and compares it with the original.

---

### **5. Find Duplicates in a List**

### **Question:**

Write a function to find duplicate elements in a list.

### **Solution:**

```python
python
CopyEdit
def find_duplicates(lst):
    seen = set()
    duplicates = set()
    for num in lst:
        if num in seen:
            duplicates.add(num)
        seen.add(num)
    return list(duplicates)

# Test
print(find_duplicates([1, 2, 3, 4, 5, 3, 2, 6]))  # Output: [2, 3]

```

### **Explanation:**

- We use a `set` to store seen elements.
- If an element is found again, it is added to the duplicates set.

---

### **6. Reverse a Linked List**

### **Question:**

Write a function to reverse a linked list.

### **Solution:**

```python
python
CopyEdit
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_linked_list(head):
    prev = None
    current = head
    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
    return prev

# Example usage
node1 = ListNode(1)
node2 = ListNode(2)
node3 = ListNode(3)
node1.next = node2
node2.next = node3

reversed_head = reverse_linked_list(node1)
while reversed_head:
    print(reversed_head.val, end=" ")  # Output: 3 2 1
    reversed_head = reversed_head.next

```

### **Explanation:**

- We iterate through the linked list, reversing the `next` pointers one by one.

---

### **7. Find the First Non-Repeating Character in a String**

### **Question**

Write a function to find the first non-repeating character in a given string.

### **Solution:**

```python

from collections import Counter

def first_non_repeating_char(s):
    freq = Counter(s)
    for char in s:
        if freq[char] == 1:
            return char
    return None

# Test
print(first_non_repeating_char("Deloitte"))  # Output: "D"
print(first_non_repeating_char("aabbcc"))    # Output: None

```

### **Explanation:**

- We use `Counter` to count character frequencies.
- We iterate through the string to find the first character with a count of 1.

---

### **8. Two Sum Problem**

### **Question:**

Given an array of numbers, find two numbers that add up to a target sum.

### **Solution:**

```python

def two_sum(nums, target):
    num_map = {}
    for index, num in enumerate(nums):
        diff = target - num
        if diff in num_map:
            return [num_map[diff], index]
        num_map[num] = index
    return []

# Test
print(two_sum([2, 7, 11, 15], 9))  # Output: [0, 1]

```

### **Explanation:**

- We use a dictionary to store numbers and their indices.
- We check if `target - num` exists in the dictionary.

---

### **9. Find the Longest Substring Without Repeating Characters**

### **Question:**

Write a function to find the length of the longest substring without repeating characters.

### **Solution:**

```python

def longest_unique_substring(s):
    char_index = {}
    left = max_length = 0
    for right in range(len(s)):
        if s[right] in char_index:
            left = max(left, char_index[s[right]] + 1)
        char_index[s[right]] = right
        max_length = max(max_length, right - left + 1)
    return max_length

# Test
print(longest_unique_substring("abcabcbb"))  # Output: 3

```

### **Explanation:**

- We use a sliding window approach.
- We store the index of each character and adjust the window when a duplicate is found.

---

### **10. Implement a Simple Cache Using LRU**

### **Question:**

Implement a Least Recently Used (LRU) cache.

### **Solution:**

```python

from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity: int):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key: int) -> int:
        if key in self.cache:
            self.cache.move_to_end(key)
            return self.cache[key]
        return -1

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)

# Test
lru = LRUCache(2)
lru.put(1, 1)
lru.put(2, 2)
print(lru.get(1))  # Output: 1
lru.put(3, 3)
print(lru.get(2))  # Output: -1 (evicted)

```

### **Explanation:**

- `OrderedDict` maintains insertion order.
- When the cache exceeds capacity, the least recently used item is removed.

---

### **Final Thoughts**

These questions cover **Python basics, data structures, algorithms, and system design**. Deloitte often focuses on **problem-solving, efficiency, and real-world applications** of Python.

4o

### You said:

More

### ChatGPT said:

ChatGPT

Here are **10 more Deloitte Python Developer interview questions** with **solutions and explanations**:

---

### **11. Merge Two Sorted Lists**

### **Question:**

Write a function to merge two sorted lists into one sorted list.

### **Solution:**

```python

def merge_sorted_lists(l1, l2):
    i, j = 0, 0
    merged = []
    while i < len(l1) and j < len(l2):
        if l1[i] < l2[j]:
            merged.append(l1[i])
            i += 1
        else:
            merged.append(l2[j])
            j += 1
    merged.extend(l1[i:])
    merged.extend(l2[j:])
    return merged

# Test
print(merge_sorted_lists([1, 3, 5], [2, 4, 6]))  # Output: [1, 2, 3, 4, 5, 6]

```

### **Explanation:**

- We use two pointers to merge the lists in order.
- If one list is exhausted, the remaining elements are added.

---

### **12. Find the Second Largest Number in a List**

### **Question:**

Write a function to find the second largest number in a list.

### **Solution:**

```python

def second_largest(nums):
    first, second = float('-inf'), float('-inf')
    for num in nums:
        if num > first:
            second, first = first, num
        elif first > num > second:
            second = num
    return second if second != float('-inf') else None

# Test
print(second_largest([10, 20, 4, 45, 99]))  # Output: 45

```

### **Explanation:**

- We track the largest and second-largest numbers using two variables.

---

### **13. Find the Intersection of Two Lists**

### **Question:**

Write a function to find the common elements between two lists.

### **Solution:**

```python

def intersection(lst1, lst2):
    return list(set(lst1) & set(lst2))

# Test
print(intersection([1, 2, 3, 4], [2, 3, 5]))  # Output: [2, 3]

```

### **Explanation:**

- We use set intersection (`&`) to find common elements.

---

### **14. Flatten a Nested List**

### **Question:**

Write a function to flatten a nested list.

### **Solution:**

```python

def flatten_list(nested_list):
    flat_list = []
    for item in nested_list:
        if isinstance(item, list):
            flat_list.extend(flatten_list(item))
        else:
            flat_list.append(item)
    return flat_list

# Test
print(flatten_list([1, [2, [3, 4], 5], 6]))  # Output: [1, 2, 3, 4, 5, 6]

```

### **Explanation:**

- We use recursion to iterate over the nested list and extract elements.

---

### **15. Find the Maximum Subarray Sum (Kadane's Algorithm)**

### **Question:**

Find the contiguous subarray with the largest sum.

### **Solution:**

```python

def max_subarray_sum(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum

# Test
print(max_subarray_sum([-2, 1, -3, 4, -1, 2, 1, -5, 4]))  # Output: 6

```

### **Explanation:**

- Kadane’s algorithm keeps track of the current subarray sum and updates the maximum.

---

### **16. Find All Pairs With a Given Sum**

### **Question:**

Write a function to find all pairs in a list that sum to a target value.

### **Solution:**

```python

def find_pairs(nums, target):
    seen = set()
    pairs = []
    for num in nums:
        diff = target - num
        if diff in seen:
            pairs.append((diff, num))
        seen.add(num)
    return pairs

# Test
print(find_pairs([1, 2, 3, 4, 5, 6], 7))  # Output: [(3, 4), (2, 5), (1, 6)]

```

### **Explanation:**

- We use a set to store seen numbers and check if their complement exists.

---

### **17. Rotate an Array by `k` Positions**

### **Question:**

Rotate an array to the right by `k` positions.

### **Solution:**

```python

def rotate_array(nums, k):
    k %= len(nums)
    return nums[-k:] + nums[:-k]

# Test
print(rotate_array([1, 2, 3, 4, 5], 2))  # Output: [4, 5, 1, 2, 3]

```

### **Explanation:**

- We split the list into two parts and swap them.

---

### **18. Generate Fibonacci Sequence Up to `n`**

### **Question:**

Generate a Fibonacci sequence up to `n` terms.

### **Solution:**

```python

def fibonacci(n):
    fib = [0, 1]
    for _ in range(n - 2):
        fib.append(fib[-1] + fib[-2])
    return fib[:n]

# Test
print(fibonacci(7))  # Output: [0, 1, 1, 2, 3, 5, 8]

```

### **Explanation:**

- We use a list to store the sequence and generate new numbers iteratively.

---

### **19. Find the Prime Numbers in a Range**

### **Question:**

Find all prime numbers between `1` and `n`.

### **Solution:**

```python

def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

def prime_numbers(n):
    return [i for i in range(2, n + 1) if is_prime(i)]

# Test
print(prime_numbers(20))  # Output: [2, 3, 5, 7, 11, 13, 17, 19]

```

### **Explanation:**

- We check divisibility up to `sqrt(n)` for efficiency.

---

### **20. Implement a Queue Using Two Stacks**

### **Question:**

Implement a queue using two stacks.

### **Solution:**

```python

class QueueUsingStacks:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []

    def enqueue(self, item):
        self.stack1.append(item)

    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop() if self.stack2 else None

# Test
q = QueueUsingStacks()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
print(q.dequeue())  # Output: 1
print(q.dequeue())  # Output: 2

```

### **Explanation:**

- `stack1` stores elements in push order.
- When dequeuing, elements are moved to `stack2` and removed in FIFO order.

---

---

### **21. Check if a Linked List has a Cycle**

### **Question:**

Write a function to detect if a linked list has a cycle.

### **Solution:**

```python

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def has_cycle(head):
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False

# Test
node1 = ListNode(1)
node2 = ListNode(2)
node3 = ListNode(3)
node1.next = node2
node2.next = node3
node3.next = node1  # Creating a cycle

print(has_cycle(node1))  # Output: True

```

### **Explanation:**

- The Floyd’s Cycle Detection Algorithm (tortoise and hare) is used.
- If `fast` meets `slow`, a cycle exists.

---

### **22. Find the Majority Element**

### **Question:**

Given an array, find the majority element (element appearing more than `n/2` times).

### **Solution:**

```python

from collections import Counter

def majority_element(nums):
    counts = Counter(nums)
    return max(counts, key=counts.get)

# Test
print(majority_element([3, 3, 4, 2, 3, 3, 3, 2]))  # Output: 3

```

### **Explanation:**

- We count occurrences and return the most frequent element.

---

### **23. Implement Binary Search**

### **Question:**

Write a function to implement binary search.

### **Solution:**

```python

def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Test
print(binary_search([1, 2, 3, 4, 5, 6], 4))  # Output: 3

```

### **Explanation:**

- We repeatedly divide the array in half to find the target.

---

### **24. Check If Two Strings Are Anagrams**

### **Question:**

Write a function to check if two strings are anagrams.

### **Solution:**

```python

from collections import Counter

def is_anagram(s1, s2):
    return Counter(s1) == Counter(s2)

# Test
print(is_anagram("listen", "silent"))  # Output: True

```

### **Explanation:**

- We compare character counts of both strings.

---

### **25. Merge Intervals**

### **Question:**

Given a list of intervals, merge overlapping ones.

### **Solution:**

```python

def merge_intervals(intervals):
    intervals.sort()
    merged = [intervals[0]]
    for start, end in intervals[1:]:
        if start <= merged[-1][1]:
            merged[-1][1] = max(merged[-1][1], end)
        else:
            merged.append([start, end])
    return merged

# Test
print(merge_intervals([[1, 3], [2, 6], [8, 10], [15, 18]]))
# Output: [[1, 6], [8, 10], [15, 18]]

```

### **Explanation:**

- We sort the intervals and merge overlapping ones.

---

### **26. Find the Median of Two Sorted Arrays**

### **Question:**

Given two sorted arrays, find their median.

### **Solution:**

```python

def find_median_sorted_arrays(nums1, nums2):
    merged = sorted(nums1 + nums2)
    mid = len(merged) // 2
    return (merged[mid] + merged[mid - 1]) / 2 if len(merged) % 2 == 0 else merged[mid]

# Test
print(find_median_sorted_arrays([1, 3], [2]))  # Output: 2
print(find_median_sorted_arrays([1, 2], [3, 4]))  # Output: 2.5

```

### **Explanation:**

- We merge the arrays and find the median.

---

### **27. Serialize and Deserialize a Binary Tree**

### **Question:**

Implement a function to serialize and deserialize a binary tree.

### **Solution:**

```python

import json

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def serialize(root):
    def dfs(node):
        if not node:
            return "null"
        return [node.val, dfs(node.left), dfs(node.right)]
    return json.dumps(dfs(root))

def deserialize(data):
    def dfs(nodes):
        val = nodes.pop(0)
        if val == "null":
            return None
        node = TreeNode(val)
        node.left = dfs(nodes)
        node.right = dfs(nodes)
        return node
    return dfs(json.loads(data))

# Test
root = TreeNode(1, TreeNode(2), TreeNode(3, TreeNode(4), TreeNode(5)))
data = serialize(root)
print(data)
deserialized_tree = deserialize(data)

```

### **Explanation:**

- We use DFS for tree traversal and JSON for serialization.

---

### **28. Implement a Min Stack**

### **Question:**

Implement a stack that supports `push()`, `pop()`, `top()`, and `getMin()` in O(1).

### **Solution:**

```python

class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, val):
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)

    def pop(self):
        if self.stack.pop() == self.min_stack[-1]:
            self.min_stack.pop()

    def top(self):
        return self.stack[-1]

    def getMin(self):
        return self.min_stack[-1]

# Test
ms = MinStack()
ms.push(3)
ms.push(5)
ms.push(2)
print(ms.getMin())  # Output: 2
ms.pop()
print(ms.getMin())  # Output: 3

```

### **Explanation:**

- We maintain a secondary stack to track the minimum values.

---

### **29. Generate All Permutations of a String**

### **Question:**

Generate all permutations of a string.

### **Solution:**

```python

from itertools import permutations

def string_permutations(s):
    return ["".join(p) for p in permutations(s)]

# Test
print(string_permutations("abc"))
# Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']

```

### **Explanation:**

- We use `itertools.permutations()` to generate all possible arrangements.

---

### **30. Find the Longest Palindromic Substring**

### **Question:**

Find the longest palindromic substring in a string.

### **Solution:**

```python

def longest_palindrome(s):
    res = ""
    for i in range(len(s)):
        for j in range(i, len(s)):
            sub = s[i:j+1]
            if sub == sub[::-1] and len(sub) > len(res):
                res = sub
    return res

# Test
print(longest_palindrome("babad"))  # Output: "bab" or "aba"

```

### **Explanation:**

- We generate all substrings and check if they are palindromes.

---

---

### **31. Find the Kth Largest Element in an Array**

### **Question:**

Write a function to find the `k`th largest element in an array.

### **Solution:**

```python

import heapq

def kth_largest(nums, k):
    return heapq.nlargest(k, nums)[-1]

# Test
print(kth_largest([3, 2, 1, 5, 6, 4], 2))  # Output: 5

```

### **Explanation:**

- We use `heapq.nlargest()` to find the `k` largest elements and return the last one.

---

### **32. Find the Longest Consecutive Sequence**

### **Question:**

Given an unsorted array, find the length of the longest consecutive elements sequence.

### **Solution:**

```python

def longest_consecutive(nums):
    num_set = set(nums)
    longest = 0
    for num in num_set:
        if num - 1 not in num_set:
            length = 1
            while num + length in num_set:
                length += 1
            longest = max(longest, length)
    return longest

# Test
print(longest_consecutive([100, 4, 200, 1, 3, 2]))  # Output: 4

```

### **Explanation:**

- We use a `set` for fast lookups and check consecutive numbers.

---

### **33. Implement a Trie (Prefix Tree)**

### **Question:**

Implement a Trie data structure for efficient word storage.

### **Solution:**

```python

class TrieNode:
    def __init__(self):
        self.children = {}
        self.end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.end_of_word = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.end_of_word

# Test
trie = Trie()
trie.insert("deloitte")
print(trie.search("deloitte"))  # Output: True
print(trie.search("del"))       # Output: False

```

### **Explanation:**

- We use a dictionary to store child nodes for fast lookups.

---

### **34. Validate a Balanced Parentheses String**

### **Question:**

Write a function to check if a given string has balanced parentheses.

### **Solution:**

```python

def is_valid_parentheses(s):
    stack = []
    mapping = {")": "(", "}": "{", "]": "["}
    for char in s:
        if char in mapping:
            top_element = stack.pop() if stack else "#"
            if mapping[char] != top_element:
                return False
        else:
            stack.append(char)
    return not stack

# Test
print(is_valid_parentheses("()[]{}"))  # Output: True
print(is_valid_parentheses("(]"))      # Output: False

```

### **Explanation:**

- We use a stack to track opening parentheses.

---

### **35. Implement Depth-First Search (DFS) in a Graph**

### **Question:**

Implement DFS for a graph.

### **Solution:**

```python

def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node not in visited:
        print(node, end=" ")
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)

# Test
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
dfs(graph, 'A')  # Output: A B D E F C

```

### **Explanation:**

- We use recursion to explore nodes in depth-first order.

---

### **36. Find the Shortest Path in a Graph (BFS)**

### **Question:**

Find the shortest path in an unweighted graph using BFS.

### **Solution:**

```python

from collections import deque

def shortest_path(graph, start, target):
    queue = deque([(start, [start])])
    while queue:
        node, path = queue.popleft()
        for neighbor in graph[node]:
            if neighbor == target:
                return path + [neighbor]
            queue.append((neighbor, path + [neighbor]))
    return None

# Test
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
print(shortest_path(graph, 'A', 'F'))  # Output: ['A', 'C', 'F']

```

### **Explanation:**

- We use BFS to explore nodes level by level.

---

### **37. Detect a Cycle in a Graph (DFS)**

### **Question:**

Detect if a directed graph contains a cycle.

### **Solution:**

```python

def has_cycle(graph):
    visited = set()
    rec_stack = set()

    def dfs(node):
        if node in rec_stack:
            return True
        if node in visited:
            return False
        visited.add(node)
        rec_stack.add(node)
        for neighbor in graph[node]:
            if dfs(neighbor):
                return True
        rec_stack.remove(node)
        return False

    return any(dfs(node) for node in graph)

# Test
graph = {
    'A': ['B'],
    'B': ['C'],
    'C': ['A']
}
print(has_cycle(graph))  # Output: True

```

### **Explanation:**

- We use DFS with recursion tracking to detect cycles.

---

### **38. Find the Lowest Common Ancestor (LCA) in a Binary Tree**

### **Question:**

Find the lowest common ancestor of two nodes in a binary tree.

### **Solution:**

```python

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def lowest_common_ancestor(root, p, q):
    if not root or root == p or root == q:
        return root
    left = lowest_common_ancestor(root.left, p, q)
    right = lowest_common_ancestor(root.right, p, q)
    return root if left and right else left or right

# Test
root = TreeNode(3, TreeNode(5, TreeNode(6), TreeNode(2)), TreeNode(1))
p, q = root.left, root.right  # Nodes 5 and 1
print(lowest_common_ancestor(root, p, q).val)  # Output: 3

```

### **Explanation:**

- We use recursion to traverse the tree and find the LCA.

---

### **39. Implement a Max Heap**

### **Question:**

Implement a Max Heap data structure.

### **Solution:**

```python

import heapq

class MaxHeap:
    def __init__(self):
        self.heap = []

    def push(self, val):
        heapq.heappush(self.heap, -val)

    def pop(self):
        return -heapq.heappop(self.heap)

# Test
heap = MaxHeap()
heap.push(10)
heap.push(20)
heap.push(5)
print(heap.pop())  # Output: 20

```

### **Explanation:**

- We use a min heap with negation to implement a max heap.

---

### **40. Find the Diameter of a Binary Tree**

### **Question:**

Find the longest path between two nodes in a binary tree.

### **Solution:**

```python

def diameter_of_binary_tree(root):
    def depth(node):
        nonlocal diameter
        if not node:
            return 0
        left = depth(node.left)
        right = depth(node.right)
        diameter = max(diameter, left + right)
        return 1 + max(left, right)

    diameter = 0
    depth(root)
    return diameter

# Test
root = TreeNode(1, TreeNode(2, TreeNode(4), TreeNode(5)), TreeNode(3))
print(diameter_of_binary_tree(root))  # Output: 3

```

### **Explanation:**

- We use DFS to find the longest path.

---

---

## **41. Find All Subsets of a Given Set**

### **Question:**

Generate all possible subsets (power set) of a given list of numbers.

### **Solution:**

```python

def subsets(nums):
    result = [[]]
    for num in nums:
        result += [curr + [num] for curr in result]
    return result

# Test
print(subsets([1, 2, 3]))
# Output: [[], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]]

```

### **Explanation:**

- Start with an empty list `result = [[]]`.
- For each number, generate new subsets by adding it to existing subsets.

---

## **42. Find the Intersection of Two Sorted Arrays**

### **Question:**

Given two sorted arrays, find their intersection.

### **Solution:**

```python

def intersect(arr1, arr2):
    i, j = 0, 0
    result = []
    while i < len(arr1) and j < len(arr2):
        if arr1[i] < arr2[j]:
            i += 1
        elif arr1[i] > arr2[j]:
            j += 1
        else:
            result.append(arr1[i])
            i += 1
            j += 1
    return result

# Test
print(intersect([1, 2, 2, 3], [2, 2, 3, 4]))  # Output: [2, 2, 3]

```

### **Explanation:**

- Use two pointers to traverse both arrays and find common elements.

---

## **43. Implement a Stack Using a Queue**

### **Question:**

Implement a stack using a queue.

### **Solution:**

```python

from collections import deque

class StackUsingQueue:
    def __init__(self):
        self.queue = deque()

    def push(self, x):
        self.queue.append(x)
        for _ in range(len(self.queue) - 1):
            self.queue.append(self.queue.popleft())

    def pop(self):
        return self.queue.popleft() if self.queue else None

    def top(self):
        return self.queue[0] if self.queue else None

# Test
stack = StackUsingQueue()
stack.push(1)
stack.push(2)
stack.push(3)
print(stack.pop())  # Output: 3

```

### **Explanation:**

- We rotate elements to simulate stack behavior using a queue.

---

## **44. Find the Maximum Product of Three Numbers**

### **Question:**

Find the maximum product of three numbers in an array.

### **Solution:**

```python

def max_product(nums):
    nums.sort()
    return max(nums[-1] * nums[-2] * nums[-3], nums[0] * nums[1] * nums[-1])

# Test
print(max_product([-10, -10, 1, 3, 2]))  # Output: 300

```

### **Explanation:**

- Consider two cases:
    - The product of the three largest numbers.
    - The product of the two smallest negative numbers and the largest number.

---

## **45. Find the GCD of Two Numbers**

### **Question:**

Write a function to find the greatest common divisor (GCD) of two numbers.

### **Solution:**

```python

import math

def gcd(a, b):
    return math.gcd(a, b)

# Test
print(gcd(48, 18))  # Output: 6

```

### **Explanation:**

- Uses Euclidean algorithm via `math.gcd()`.

---

## **46. Find the Peak Element in an Array**

### **Question:**

Find an element in an array that is greater than its neighbors.

### **Solution:**

```python

def find_peak(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[mid + 1]:
            right = mid
        else:
            left = mid + 1
    return nums[left]

# Test
print(find_peak([1, 2, 3, 1]))  # Output: 3

```

### **Explanation:**

- Binary search is used to efficiently locate the peak.

---

## **47. Find the First Missing Positive Integer**

### **Question:**

Find the smallest missing positive integer in an unsorted array.

### **Solution:**

```python

def first_missing_positive(nums):
    nums = set(nums)
    i = 1
    while i in nums:
        i += 1
    return i

# Test
print(first_missing_positive([3, 4, -1, 1]))  # Output: 2

```

### **Explanation:**

- Store numbers in a set for O(1) lookups.
- Find the first missing positive by iterating from `1`.

---

## **48. Find the Celebrity in a Party (Graph Problem)**

### **Question:**

A celebrity is a person who is known by everyone but knows no one. Find the celebrity in O(n).

### **Solution:**

```python

def knows(a, b):
    """Returns True if person a knows person b."""
    return relationships[a][b]

def find_celebrity(n):
    candidate = 0
    for i in range(1, n):
        if knows(candidate, i):
            candidate = i

    for i in range(n):
        if i != candidate and (knows(candidate, i) or not knows(i, candidate)):
            return -1
    return candidate

# Example: 0 knows 1, 1 knows 2, 2 knows no one (Celebrity)
relationships = [
    [0, 1, 1],
    [0, 0, 1],
    [0, 0, 0]
]
print(find_celebrity(3))  # Output: 2

```

### **Explanation:**

- A two-pass algorithm eliminates non-celebrities in O(n).

---

## **49. Find the Single Number (Appears Once)**

### **Question:**

Find the element that appears only once in an array where every other element appears twice.

### **Solution:**

```python

def single_number(nums):
    result = 0
    for num in nums:
        result ^= num
    return result

# Test
print(single_number([4, 1, 2, 1, 2]))  # Output: 4

```

### **Explanation:**

- XOR cancels out duplicate numbers, leaving the unique one.

---

## **50. Find the Number of Islands (Matrix Traversal)**

### **Question:**

Given a 2D grid of `'1'` (land) and `'0'` (water), find the number of islands.

### **Solution:**

```python

def num_islands(grid):
    if not grid:
        return 0

    rows, cols = len(grid), len(grid[0])
    visited = set()

    def dfs(r, c):
        if (r, c) in visited or r < 0 or c < 0 or r >= rows or c >= cols or grid[r][c] == '0':
            return
        visited.add((r, c))
        dfs(r+1, c)
        dfs(r-1, c)
        dfs(r, c+1)
        dfs(r, c-1)

    count = 0
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == '1' and (r, c) not in visited:
                dfs(r, c)
                count += 1
    return count

# Test
grid = [
    ["1", "1", "0", "0", "0"],
    ["1", "1", "0", "0", "0"],
    ["0", "0", "1", "0", "0"],
    ["0", "0", "0", "1", "1"]
]
print(num_islands(grid))  # Output: 3

```

### **Explanation:**

- DFS is used to traverse and mark visited land cells.

## **51. Implement an LFU (Least Frequently Used) Cache**

### **Question:**

Design an LFU (Least Frequently Used) Cache with O(1) time complexity for `get()` and `put()` operations.

### **Solution:**

```python

import collections

class LFUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.min_freq = 0
        self.node_map = {}
        self.freq_map = collections.defaultdict(collections.OrderedDict)

    def _update_freq(self, key):
        freq = self.node_map[key][1]
        value = self.node_map[key][0]
        del self.freq_map[freq][key]

        if not self.freq_map[freq]:
            del self.freq_map[freq]
            if self.min_freq == freq:
                self.min_freq += 1

        self.node_map[key] = (value, freq + 1)
        self.freq_map[freq + 1][key] = None

    def get(self, key: int) -> int:
        if key not in self.node_map:
            return -1
        self._update_freq(key)
        return self.node_map[key][0]

    def put(self, key: int, value: int) -> None:
        if self.capacity == 0:
            return

        if key in self.node_map:
            self.node_map[key] = (value, self.node_map[key][1])
            self._update_freq(key)
            return

        if len(self.node_map) >= self.capacity:
            evict_key, _ = self.freq_map[self.min_freq].popitem(last=False)
            del self.node_map[evict_key]

        self.node_map[key] = (value, 1)
        self.freq_map[1][key] = None
        self.min_freq = 1

# Test
lfu = LFUCache(2)
lfu.put(1, 10)
lfu.put(2, 20)
print(lfu.get(1))  # Output: 10
lfu.put(3, 30)     # Removes key 2 (least frequently used)
print(lfu.get(2))  # Output: -1

```

### **Explanation:**

- Uses a **dictionary + frequency map** to efficiently track least-used items.
- Supports O(1) operations using **OrderedDict** and frequency tracking.

---

## **52. Implement a Multithreaded File Reader**

### **Question:**

Design a multithreaded Python program to read large files in parallel.

### **Solution:**

```python

import threading

def read_chunk(file_name, start, end):
    with open(file_name, "r") as f:
        f.seek(start)
        while f.tell() < end:
            print(f.readline().strip())

def parallel_file_read(file_name, num_threads=4):
    with open(file_name, "r") as f:
        f.seek(0, 2)
        file_size = f.tell()
        chunk_size = file_size // num_threads

    threads = []
    for i in range(num_threads):
        start = i * chunk_size
        end = file_size if i == num_threads - 1 else (i + 1) * chunk_size
        t = threading.Thread(target=read_chunk, args=(file_name, start, end))
        threads.append(t)
        t.start()

    for t in threads:
        t.join()

# Test
parallel_file_read("large_file.txt")

```

### **Explanation:**

- Uses Python’s `threading` module to read chunks of a file in parallel.
- `seek()` allows for efficient file access.

---

## **53. Design a Web Crawler**

### **Question:**

Implement a Python web crawler that collects all links from a given URL.

### **Solution:**

```python

import requests
from bs4 import BeautifulSoup
from queue import Queue

def web_crawler(start_url, max_depth=2):
    visited = set()
    queue = Queue()
    queue.put((start_url, 0))

    while not queue.empty():
        url, depth = queue.get()
        if depth > max_depth or url in visited:
            continue

        try:
            response = requests.get(url, timeout=5)
            soup = BeautifulSoup(response.text, "html.parser")
            print("Crawled:", url)

            for link in soup.find_all("a", href=True):
                next_url = link['href']
                if next_url.startswith("http"):
                    queue.put((next_url, depth + 1))
        except Exception:
            pass

        visited.add(url)

# Test
web_crawler("https://example.com")

```

### **Explanation:**

- Uses `requests` + `BeautifulSoup` to extract links.
- `Queue` maintains BFS-based crawling.

---

## **54. Implement a Distributed Task Queue Using Celery**

### **Question:**

Create a task queue using Celery for parallel execution.

### **Solution:**

```python

from celery import Celery

app = Celery('tasks', broker='redis://localhost:6379/0')

@app.task
def add(x, y):
    return x + y

# Running Tasks
result = add.delay(4, 5)
print(result.get())  # Output: 9

```

### **Explanation:**

- Uses **Celery + Redis** to handle distributed task execution.

---

## **55. Implement a Rate Limiter**

### **Question:**

Create a rate limiter to allow `N` requests per second.

### **Solution:**

```python

import time
from collections import deque

class RateLimiter:
    def __init__(self, max_requests, time_window):
        self.queue = deque()
        self.max_requests = max_requests
        self.time_window = time_window

    def allow_request(self):
        current_time = time.time()
        while self.queue and self.queue[0] < current_time - self.time_window:
            self.queue.popleft()

        if len(self.queue) < self.max_requests:
            self.queue.append(current_time)
            return True
        return False

# Test
limiter = RateLimiter(3, 1)  # Allow 3 requests per second
for _ in range(5):
    print(limiter.allow_request())  # Output: True, True, True, False, False

```

### **Explanation:**

- Uses a **deque** to track timestamps of requests.

---

## **56. Implement Dijkstra’s Algorithm for Shortest Path**

### **Solution:**

```python

import heapq

def dijkstra(graph, start):
    min_heap = [(0, start)]
    distances = {node: float('inf') for node in graph}
    distances[start] = 0

    while min_heap:
        current_dist, current_node = heapq.heappop(min_heap)
        if current_dist > distances[current_node]:
            continue

        for neighbor, weight in graph[current_node].items():
            distance = current_dist + weight
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(min_heap, (distance, neighbor))

    return distances

# Test
graph = {
    'A': {'B': 1, 'C': 4},
    'B': {'C': 2, 'D': 5},
    'C': {'D': 1},
    'D': {}
}
print(dijkstra(graph, 'A'))  # Output: {'A': 0, 'B': 1, 'C': 3, 'D': 4}

```

### **Explanation:**

- Uses a **priority queue (`heapq`)** for efficient shortest path calculation.

---

## **58. Implement Consistent Hashing for Load Balancing**

### **Question:**

Design a **consistent hashing algorithm** for distributed systems.

### **Solution:**

```python

import hashlib
import bisect

class ConsistentHashing:
    def __init__(self, nodes=None):
        self.ring = []
        self.node_map = {}
        if nodes:
            for node in nodes:
                self.add_node(node)

    def _hash(self, key):
        return int(hashlib.md5(key.encode()).hexdigest(), 16)

    def add_node(self, node):
        hash_val = self._hash(node)
        self.ring.append(hash_val)
        self.node_map[hash_val] = node
        self.ring.sort()

    def remove_node(self, node):
        hash_val = self._hash(node)
        self.ring.remove(hash_val)
        del self.node_map[hash_val]

    def get_node(self, key):
        if not self.ring:
            return None
        hash_val = self._hash(key)
        idx = bisect.bisect(self.ring, hash_val) % len(self.ring)
        return self.node_map[self.ring[idx]]

# Test
ch = ConsistentHashing(["Node1", "Node2", "Node3"])
print(ch.get_node("user1"))  # Output: Node2 (Example)
print(ch.get_node("user2"))  # Output: Node1 (Example)

```

### **Explanation:**

- Uses **MD5 hashing** to distribute keys across servers.
- **Bisect module** helps in efficiently locating the responsible node.

---

## **59. Implement a URL Shortener (Like Bitly)**

### **Solution:**

```python

import hashlib

class URLShortener:
    def __init__(self):
        self.url_map = {}

    def shorten_url(self, long_url):
        short_hash = hashlib.md5(long_url.encode()).hexdigest()[:6]
        self.url_map[short_hash] = long_url
        return f"https://short.ly/{short_hash}"

    def expand_url(self, short_url):
        key = short_url.split("/")[-1]
        return self.url_map.get(key, None)

# Test
shortener = URLShortener()
short_url = shortener.shorten_url("https://www.deloitte.com/careers")
print(short_url)  # Output: https://short.ly/a1b2c3
print(shortener.expand_url(short_url))  # Output: https://www.deloitte.com/careers

```

### **Explanation:**

- Uses **MD5 hashing** to generate unique short URLs.
- Stores mappings in a dictionary.

---

## **60. Implement an Asynchronous Web Scraper Using `asyncio`**

### **Solution:**

```python

import asyncio
import aiohttp

async def fetch(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.text()

async def main():
    urls = ["https://example.com", "https://google.com"]
    tasks = [fetch(url) for url in urls]
    results = await asyncio.gather(*tasks)
    for result in results:
        print(result[:100])  # Print first 100 characters

# Run Async Scraper
# asyncio.run(main())

```

### **Explanation:**

- Uses **`asyncio` and `aiohttp`** for high-performance scraping.

---

## **61. Design a Distributed Logging System**

### **Solution:**

```python

import logging
import logging.handlers

logger = logging.getLogger("DistributedLogger")
handler = logging.handlers.SysLogHandler(address=('localhost', 514))
logger.addHandler(handler)
logger.setLevel(logging.INFO)

# Log an event
logger.info("This is a distributed log message")

```

### **Explanation:**

- Uses **Syslog Server** for centralized logging.

## **65. Implement a Parallel Merge Sort Using Multiprocessing**

### **Question:**

Implement **Merge Sort** using Python’s `multiprocessing` module to sort large datasets in parallel.

### **Solution:**

```python

import multiprocessing

def merge(left, right):
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result

def parallel_merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left_half = arr[:mid]
    right_half = arr[mid:]

    with multiprocessing.Pool(processes=2) as pool:
        left_sorted, right_sorted = pool.map(parallel_merge_sort, [left_half, right_half])

    return merge(left_sorted, right_sorted)

# Test
arr = [38, 27, 43, 3, 9, 82, 10]
print(parallel_merge_sort(arr))  # Output: [3, 9, 10, 27, 38, 43, 82]

```

### **Explanation:**

- Uses **process-based parallelism** to sort large datasets.
- Divides the array, sorts in parallel, then merges results.

---

## **66. Implement an In-Memory Key-Value Store with TTL**

### **Question:**

Design a **key-value store** with an **expiration time (TTL)**.

### **Solution:**

```python

import time
import threading

class KeyValueStore:
    def __init__(self):
        self.store = {}
        self.lock = threading.Lock()

    def set(self, key, value, ttl=None):
        expiry_time = time.time() + ttl if ttl else None
        with self.lock:
            self.store[key] = (value, expiry_time)

    def get(self, key):
        with self.lock:
            if key not in self.store:
                return None
            value, expiry_time = self.store[key]
            if expiry_time and expiry_time < time.time():
                del self.store[key]
                return None
            return value

# Test
store = KeyValueStore()
store.set("name", "Deloitte", ttl=5)
print(store.get("name"))  # Output: "Deloitte"
time.sleep(6)
print(store.get("name"))  # Output: None (Expired)

```

### **Explanation:**

- Uses **thread-safe TTL management** to delete expired keys.

---

## **67. Implement a File Deduplication System Using Hashing**

### **Question:**

Remove duplicate files in a directory by using **SHA-256 hashing**.

### **Solution:**

```python

import os
import hashlib

def hash_file(filepath):
    hasher = hashlib.sha256()
    with open(filepath, "rb") as f:
        while chunk := f.read(4096):
            hasher.update(chunk)
    return hasher.hexdigest()

def remove_duplicates(directory):
    seen_files = {}
    for root, _, files in os.walk(directory):
        for file in files:
            path = os.path.join(root, file)
            file_hash = hash_file(path)
            if file_hash in seen_files:
                os.remove(path)  # Delete duplicate
            else:
                seen_files[file_hash] = path

# Test (Run this in a directory with duplicate files)
# remove_duplicates("/path/to/folder")

```

### **Explanation:**

- Uses **SHA-256** hashing to detect and remove duplicate files.

---

## **68. Implement a Scalable Web Crawler with Threading**

### **Solution:**

```python

import threading
import requests
from bs4 import BeautifulSoup

class WebCrawler:
    def __init__(self, base_url, max_depth=2):
        self.base_url = base_url
        self.visited = set()
        self.lock = threading.Lock()
        self.max_depth = max_depth

    def crawl(self, url, depth):
        if depth > self.max_depth or url in self.visited:
            return

        self.lock.acquire()
        self.visited.add(url)
        self.lock.release()

        try:
            response = requests.get(url)
            soup = BeautifulSoup(response.text, "html.parser")
            print("Crawled:", url)

            threads = []
            for link in soup.find_all("a", href=True):
                full_url = link["href"]
                if full_url.startswith("http"):
                    t = threading.Thread(target=self.crawl, args=(full_url, depth + 1))
                    threads.append(t)
                    t.start()

            for t in threads:
                t.join()
        except Exception as e:
            pass

# Test
crawler = WebCrawler("https://example.com")
crawler.crawl("https://example.com", 0)

```

### **Explanation:**

- Uses **multithreading** to perform **efficient web crawling**.

---

## **69. Implement a Bloom Filter for Fast Membership Testing**

### **Solution:**

```python

import mmh3
from bitarray import bitarray

class BloomFilter:
    def __init__(self, size, hash_count):
        self.size = size
        self.hash_count = hash_count
        self.bit_array = bitarray(size)
        self.bit_array.setall(0)

    def add(self, item):
        for i in range(self.hash_count):
            digest = mmh3.hash(item, i) % self.size
            self.bit_array[digest] = 1

    def check(self, item):
        for i in range(self.hash_count):
            digest = mmh3.hash(item, i) % self.size
            if self.bit_array[digest] == 0:
                return False
        return True

# Test
bloom = BloomFilter(5000, 3)
bloom.add("Deloitte")
print(bloom.check("Deloitte"))  # Output: True
print(bloom.check("Google"))    # Output: False (Mostly)

```

### **Explanation:**

- **Bloom filters** are probabilistic data structures that **reduce memory usage**.

## **71. Implement a Custom LRU Cache**

### **Solution:**

```python

from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity: int):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key: int):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key: int, value: int):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)

# Test
cache = LRUCache(2)
cache.put(1, 10)
cache.put(2, 20)
print(cache.get(1))  # Output: 10
cache.put(3, 30)     # Removes key 2
print(cache.get(2))  # Output: -1

```

### **Explanation:**

- Uses **OrderedDict** to maintain **LRU eviction** efficiently.