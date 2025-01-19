# Notes - Basic : Code only

### Problem: Sort by Frequency and Value

Write a function that takes a list of integers and sorts it in descending order by frequency. If two numbers have the same frequency, the larger number comes first.

### Example

Input: `[4, 5, 6, 5, 4, 3]`

Output: `[5, 5, 4, 4, 6, 3]`

### Solution and Code

To solve this problem, you can use Python’s `collections.Counter` to count the occurrences of each integer, then sort by frequency and value.

```python
from collections import Counter

def sort_by_frequency(arr):
    # Step 1: Count frequencies of elements in the array
    frequency_count = Counter(arr)
    
    # Step 2: Sort based on frequency, and by value when frequencies are equal
    sorted_arr = sorted(arr, key=lambda x: (-frequency_count[x], -x))
    
    return sorted_arr

# Test with the example
input_list = [4, 5, 6, 5, 4, 3]
output = sort_by_frequency(input_list)
print("Sorted by frequency and value:", output)

Output: Sorted by frequency and value: [5, 5, 4, 4, 6, 3]

```

### Explanation of the Code

1. **Counting Frequencies**:
    - We use `Counter(arr)` to get a dictionary with numbers as keys and their frequencies as values.
    - For example, `Counter([4, 5, 6, 5, 4, 3])` returns `Counter({4: 2, 5: 2, 6: 1, 3: 1})`.
2. **Sorting Logic**:
    - The `sorted` function takes a custom `key` argument. We sort by two criteria:
        - `frequency_count[x]`: Sort by descending frequency.
        - `x`: For numbers with the same frequency, the negative sign ensures larger numbers come first.
    - For `[4, 5, 6, 5, 4, 3]`, the function first checks frequency, then value, resulting in `[5, 5, 4, 4, 6, 3]`.
3. **Return the Result**:
    - We return the sorted list and print the output.

### Detailed Explanation of the Output

- `5` and `4` appear twice each, so they come first.
- Since `5` is larger than `4`, it appears before `4`.
- `6` and `3` each appear once. `6` appears before `3` because it's larger.

### **Two Sum Problem**

**Problem**: Given a list of integers and a target integer, return the indices of the two numbers that add up to the target.

**Example**

Input: `nums = [2, 7, 11, 15]`, `target = 9`

Output: `[0, 1]` (since `2 + 7 = 9`)

```python
def two_sum(nums, target):
    # Dictionary to store the index of each element
    indices = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in indices:
            return [indices[diff], i]
        indices[num] = i
    return None

# Testing the function
nums = [2, 7, 11, 15]
target = 9
output = two_sum(nums, target)
print("Output:", output)

Output: [0, 1]

```

**Explanation**:

1. Create a dictionary `indices` to store elements and their indices.
2. For each element `num`, calculate `diff = target - num`.
3. If `diff` exists in `indices`, it means we found two numbers (`diff` and `num`) that add up to the target.
4. Return their indices `[indices[diff], i]`.

### **Palindrome Check**

**Problem**: Check if a given string reads the same forward and backward.

**Example**

```python
def is_palindrome(s):
    return s == s[::-1]

# Testing the function
s = "racecar"
output = is_palindrome(s)
print("Output:", output)

Output: True

```

Input: `"racecar"`

Output: `True` (since "racecar" reads the same backward)

### **Anagram Check**

**Problem**: Check if two strings are anagrams (contain the same characters with the same frequency).

**Example**

Input: `"listen"`, `"silent"`

Output: `True`

**Solution Code**:

```python
def are_anagrams(s1, s2):
    return sorted(s1) == sorted(s2)

# Testing the function
s1 = "listen"
s2 = "silent"
output = are_anagrams(s1, s2)
print("Output:", output)

Output: True

```

**Explanation**:

1. Sort both strings and compare them.
2. If they are equal, they contain the same characters with the same frequency.

### **Find Duplicates in a List**

**Problem**: Identify all duplicate elements in a list.

**Example**

Input: `[1, 2, 3, 4, 4, 5, 6, 6]`

Output: `[4, 6]`

```python
def find_duplicates(nums):
    seen = set()
    duplicates = set()
    for num in nums:
        if num in seen:
            duplicates.add(num)
        else:
            seen.add(num)
    return list(duplicates)

# Testing the function
nums = [1, 2, 3, 4, 4, 5, 6, 6]
output = find_duplicates(nums)
print("Output:", output)

Output: [4, 6]
```

**Explanation**:

1. Use two sets: `seen` for elements we’ve encountered and `duplicates` for duplicate entries.
2. For each `num` in the list, check if it's in `seen`. If yes, it’s a duplicate; add it to `duplicates`. If not, add it to `seen`.

### **Reverse a List**

**Problem**: Reverse the elements of a list.

**Example**

Input: `[1, 2, 3, 4]`

Output: `[4, 3, 2, 1]`

```python
def reverse_list(lst):
    return lst[::-1]

# Testing the function
lst = [1, 2, 3, 4]
output = reverse_list(lst)
print("Output:", output)

Output: [4, 3, 2, 1]

```

**Explanation**:

1. Use slicing `lst[::-1]` to reverse the list.

### **String Permutations**

**Problem**: Generate all possible permutations of a given string.

**Example**

Input: `"abc"`

Output: `['abc', 'acb', 'bac', 'bca', 'cab', 'cba']`

```python
from itertools import permutations

def string_permutations(s):
    # Generate permutations and join each tuple to form strings
    return [''.join(p) for p in permutations(s)]

# Testing the function
s = "abc"
output = string_permutations(s)
print("Output:", output)

Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']

```

**Explanation**:

1. Use `itertools.permutations` to generate all unique arrangements of the characters in the string.
2. Each permutation is a tuple, so we join the tuple elements to form strings.

### **Remove Vowels**

**Problem**: Remove all vowels from a given string.

**Example**

Input: `"hello world"`

Output: `"hll wrld"`

```python
def remove_vowels(s):
    vowels = "aeiouAEIOU"
    return ''.join([char for char in s if char not in vowels])

# Testing the function
s = "hello world"
output = remove_vowels(s)
print("Output:", output)

Output: "hll wrld"

```

**Explanation**:

1. Define a string of vowels, `vowels`.
2. Use a list comprehension to filter out any character in `s` that is in `vowels`.
3. Join the list to form the final string without vowels.

### **Sort List of Tuples by Second Element**

**Problem**: Given a list of tuples, sort the list based on the second element of each tuple.

**Example**

Input: `[(1, 3), (3, 2), (2, 1)]`

Output: `[(2, 1), (3, 2), (1, 3)]`

```python
def sort_by_second_element(tuples_list):
    return sorted(tuples_list, key=lambda x: x[1])

# Testing the function
tuples_list = [(1, 3), (3, 2), (2, 1)]
output = sort_by_second_element(tuples_list)
print("Output:", output)

Output: [(2, 1), (3, 2), (1, 3)]
 
```

**Explanation**:

1. Use `sorted` with `key=lambda x: x[1]`, sorting by the second element in each tuple.
2. This sorts in ascending order by default.

### **Factorial of a Number**

**Problem**: Calculate the factorial of a given number nnn, defined as n!=n×(n−1)×⋯×1n! = n \times (n-1) \times \dots \times 1n!=n×(n−1)×⋯×1.

**Example**

Input: `5`

Output: `120` (since `5 * 4 * 3 * 2 * 1 = 120`)

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

# Testing the function
n = 5
output = factorial(n)
print("Output:", output)

Output: 120

```

**Explanation**:

1. Use recursion: if `n` is `0`, return `1` (base case).
2. Otherwise, multiply `n` by `factorial(n - 1)`, which continues until reaching the base case.

### **Fibonacci Sequence**

**Problem**: Generate the first nnn numbers in the Fibonacci sequence, where each number is the sum of the two preceding ones, starting with `0` and `1`.

**Example**

Input: `n = 5`

Output: `[0, 1, 1, 2, 3]`

```python
def fibonacci(n):
    fib_seq = [0, 1]
    for i in range(2, n):
        next_value = fib_seq[-1] + fib_seq[-2]
        fib_seq.append(next_value)
    return fib_seq[:n]

# Testing the function
n = 5
output = fibonacci(n)
print("Output:", output)

Output: [0, 1, 1, 2, 3]

```

**Explanation**:

1. Start with the list `[0, 1]` for the first two Fibonacci numbers.
2. Use a loop to calculate each new term as the sum of the last two terms in `fib_seq`.
3. Append the result until we have `n` terms, then return the list.

### **Flatten a List of Lists**

**Problem**: Convert a list of lists into a single flat list.

**Example**

Input: `[[1, 2, 3], [4, 5], [6, 7]]`

Output: `[1, 2, 3, 4, 5, 6, 7]`

```python
def flatten_list(nested_list):
    return [item for sublist in nested_list for item in sublist]

# Testing the function
nested_list = [[1, 2, 3], [4, 5], [6, 7]]
output = flatten_list(nested_list)
print("Output:", output)

Output: [1, 2, 3, 4, 5, 6, 7]

```

**Explanation**:

1. Use a nested list comprehension to access each `item` in each `sublist` of `nested_list`.
2. This creates a new list with all elements in a single level.

### **Find GCD (Greatest Common Divisor)**

**Problem**: Compute the Greatest Common Divisor of two integers.

**Example**

Input: `a = 48`, `b = 18`

Output: `6` (since 6 is the largest number that divides both 48 and 18)

```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# Testing the function
a, b = 48, 18
output = gcd(a, b)
print("Output:", output)

**Output: 6**

```

**Explanation**:

1. Use the Euclidean algorithm: while `b` is not zero, repeatedly replace `a` with `b` and `b` with `a % b`.
2. When `b` becomes zero, `a` is the GCD.

### **Find LCM (Least Common Multiple)**

**Problem**: Compute the Least Common Multiple of two integers.

**Example**

Input: `a = 4`, `b = 5`

Output: `20` (since 20 is the smallest number divisible by both 4 and 5)

```python
def lcm(a, b):
    return abs(a * b) // gcd(a, b)

# Testing the function
a, b = 4, 5
output = lcm(a, b)
print("Output:", output)

Output: 20

```

**Explanation**:

1. Calculate the LCM using the formula `|a * b| // gcd(a, b)`.
2. This uses the `gcd` function from the previous example to find the LCM efficiently.

### **Prime Number Check**

**Problem**: Check if a given number is prime.

**Example**

Input: `n = 7`

Output: `True` (since 7 is only divisible by 1 and itself)

```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Testing the function
n = 7
output = is_prime(n)
print("Output:", output)

Output: True

```

**Explanation**:

1. A number `n` is prime if it’s greater than 1 and has no divisors other than 1 and itself.
2. Check divisors up to the square root of `n` (for efficiency). If any divisor divides `n` evenly, return `False`.
3. If no divisors are found, return `True`.

### **Longest Common Prefix**

**Problem**: Find the longest common prefix string amongst a list of strings.

**Example**

Input: `["flower", "flow", "flight"]`

Output: `"fl"`

```python
def longest_common_prefix(strs):
    if not strs:
        return ""
    prefix = strs[0]
    for s in strs[1:]:
        while s[:len(prefix)] != prefix and prefix:
            prefix = prefix[:-1]
    return prefix

# Testing the function
strs = ["flower", "flow", "flight"]
output = longest_common_prefix(strs)
print("Output:", output)

Output: "fl"

```

**Explanation**:

1. Start with the first string as the `prefix`.
2. Compare each string with `prefix`. If `prefix` is not a substring, reduce it one character at a time until it matches or becomes empty.
3. Continue until the longest common prefix is identified.

### **Count Vowels and Consonants**

**Problem**: Count the number of vowels and consonants in a given string.

**Example**

Input: `"hello world"`

Output: `Vowels: 3, Consonants: 7`

```python
def count_vowels_consonants(s):
    vowels = "aeiouAEIOU"
    vowel_count = 0
    consonant_count = 0
    for char in s:
        if char.isalpha():
            if char in vowels:
                vowel_count += 1
            else:
                consonant_count += 1
    return vowel_count, consonant_count

# Testing the function
s = "hello world"
vowels, consonants = count_vowels_consonants(s)
print("Vowels:", vowels, "Consonants:", consonants)

Vowels: 3 Consonants: 7

```

**Explanation**:

1. Loop through each character, checking if it’s alphabetic with `char.isalpha()`.
2. If it’s a vowel, increment `vowel_count`; otherwise, increment `consonant_count`.

### **Sum of Digits**

**Problem**: Calculate the sum of digits of a given number.

**Example**

Input: `12345`

Output: `15` (since `1 + 2 + 3 + 4 + 5 = 15`)

```python
def sum_of_digits(n):
    return sum(int(digit) for digit in str(n))

# Testing the function
n = 12345
output = sum_of_digits(n)
print("Output:", output)

Output: 15

```

**Explanation**:

1. Convert the number `n` to a string to iterate over each digit.
2. Convert each character back to an integer and sum them up.

### **Remove Duplicates from a List**

**Problem**: Remove duplicate elements from a list while maintaining the original order.

**Example**

Input: `[1, 2, 2, 3, 4, 4, 5]`

Output: `[1, 2, 3, 4, 5]`

```python
def remove_duplicates(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# Testing the function
lst = [1, 2, 2, 3, 4, 4, 5]
output = remove_duplicates(lst)
print("Output:", output)

Output: [1, 2, 3, 4, 5]

```

**Explanation**:

1. Use a `set` called `seen` to track elements already encountered.
2. Append items to `result` only if they aren’t in `seen`.

### **Binary Search**

**Problem**: Implement a binary search algorithm to find an element in a sorted list.

**Example**

Input: `lst = [1, 2, 3, 4, 5]`, `target = 4`

Output: `3` (since `4` is at index `3`)

```python
def binary_search(lst, target):
    left, right = 0, len(lst) - 1
    while left <= right:
        mid = (left + right) // 2
        if lst[mid] == target:
            return mid
        elif lst[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1  # Element not found

# Testing the function
lst = [1, 2, 3, 4, 5]
target = 4
output = binary_search(lst, target)
print("Output:", output)

Output: 3

```

**Explanation**:

1. Start with pointers `left` and `right` at the beginning and end of `lst`.
2. Calculate `mid` as the midpoint, then compare `lst[mid]` with `target`.
3. If they match, return `mid`. If `target` is greater, adjust `left`; if smaller, adjust `right`.

### **Merge Sorted Lists**

**Problem**: Merge two sorted lists into one sorted list.

**Example**

Input: `list1 = [1, 3, 5]`, `list2 = [2, 4, 6]`

Output: `[1, 2, 3, 4, 5, 6]`

```python
def merge_sorted_lists(list1, list2):
    result = []
    i, j = 0, 0
    while i < len(list1) and j < len(list2):
        if list1[i] < list2[j]:
            result.append(list1[i])
            i += 1
        else:
            result.append(list2[j])
            j += 1
    # Add remaining elements
    result.extend(list1[i:])
    result.extend(list2[j:])
    return result

# Testing the function
list1 = [1, 3, 5]
list2 = [2, 4, 6]
output = merge_sorted_lists(list1, list2)
print("Output:", output)

Output: [1, 2, 3, 4, 5, 6]

```

**Explanation**:

1. Initialize pointers `i` and `j` for `list1` and `list2`.
2. Compare elements and append the smaller one to `result`.
3. Once one list is exhausted, append the remaining elements from the other list.

### **Most Frequent Element**

**Problem**: Find the most frequent element in a list.

**Example**

Input: `[1, 2, 2, 3, 3, 3, 4]`

Output: `3` (since `3` appears most frequently)

```python
from collections import Counter

def most_frequent(lst):
    count = Counter(lst)
    return count.most_common(1)[0][0]

# Testing the function
lst = [1, 2, 2, 3, 3, 3, 4]
output = most_frequent(lst)
print("Output:", output)

Output: 3

```

**Explanation**:

1. Use `Counter` from `collections` to count occurrences of each element in `lst`.
2. `most_common(1)` returns a list with the most common element and its count. We access the element with `[0][0]`.

### **Merge Overlapping Intervals**

**Problem**: Given a list of intervals, merge all overlapping intervals.

**Example**

Input: `[[1, 3], [2, 6], [8, 10], [15, 18]]`

Output: `[[1, 6], [8, 10], [15, 18]]`

```python
def merge_intervals(intervals):
    intervals.sort(key=lambda x: x[0])  # Sort by the start time
    merged = []
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    return merged

# Testing the function
intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]
output = merge_intervals(intervals)
print("Output:", output)

Output: [[1, 6], [8, 10], [15, 18]]

```

**Explanation**:

1. Sort `intervals` by the start times.
2. For each interval, check if it overlaps with the last merged interval.
3. If it does, merge them by updating the end time; otherwise, add it as a new interval.

### **Subset Check**

**Problem**: Check if one list is a subset of another list.

**Example**

Input: `list1 = [1, 2, 3]`, `list2 = [1, 2, 3, 4, 5]`

Output: `True` (since all elements of `list1` are in `list2`)

```python
def is_subset(list1, list2):
    return set(list1).issubset(set(list2))

# Testing the function
list1 = [1, 2, 3]
list2 = [1, 2, 3, 4, 5]
output = is_subset(list1, list2)
print("Output:", output)

Output: True

```

**Explanation**:

1. Convert `list1` and `list2` to sets.
2. Use `issubset()` to check if all elements of `list1` are in `list2`.

### **Transpose Matrix**

**Problem**: Given a 2D matrix, return its transpose.

**Example**

Input: `matrix = [[1, 2, 3], [4, 5, 6]]`

Output: `[[1, 4], [2, 5], [3, 6]]`

```python
def transpose(matrix):
    return [list(row) for row in zip(*matrix)]

# Testing the function
matrix = [[1, 2, 3], [4, 5, 6]]
output = transpose(matrix)
print("Output:", output)

Output: [[1, 4], [2, 5], [3, 6]]

```

**Explanation**:

1. Use `zip(*matrix)` to group elements by column instead of row.
2. Convert each grouped tuple to a list for a clean output.

### **Rotate Matrix by 90 Degrees**

**Problem**: Given an n×nn \times nn×n matrix, rotate it by 90 degrees clockwise.

**Example**

Input: `matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`

Output: `[[7, 4, 1], [8, 5, 2], [9, 6, 3]]`

```python
def rotate_matrix(matrix):
    return [list(row) for row in zip(*matrix[::-1])]

# Testing the function
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
output = rotate_matrix(matrix)
print("Output:", output)

Output: [[7, 4, 1], [8, 5, 2], [9, 6, 3]]

```

**Explanation**:

1. Reverse the matrix to get a rotated perspective.
2. Use `zip(*matrix[::-1])` to transpose the reversed rows.

### **Balanced Brackets**

**Problem**: Check if a string of brackets (`{}`, `[]`, `()`) is balanced.

**Example**

Input: `"{[()]}"`

Output: `True`

```python
def is_balanced(s):
    stack = []
    brackets = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in brackets.values():
            stack.append(char)
        elif char in brackets:
            if not stack or stack.pop() != brackets[char]:
                return False
    return not stack

# Testing the function
s = "{[()]}"
output = is_balanced(s)
print("Output:", output)

Output: True

```

**Explanation**:

1. Use a `stack` to manage opening brackets.
2. For closing brackets, check if they match the last item in `stack`.
3. If they don’t, return `False`; if `stack` is empty at the end, return `True`.

### **Count Words in a Sentence**

**Problem**: Count the number of words in a given sentence.

**Example**

Input: `"Hello, world!"`

Output: `2`

```python
def count_words(sentence):
    words = sentence.split()
    return len(words)

# Testing the function
sentence = "Hello, world!"
output = count_words(sentence)
print("Output:", output)

Output: 2

```

**Explanation**:

1. Use `split()` to break the sentence into words based on whitespace.
2. Count the number of elements in the list.

### **Generate a Random Password**

**Problem**: Generate a random password containing uppercase letters, lowercase letters, digits, and special characters, with a specified length.

**Example**

Input: `length = 8`

Output: `"A9f$k2R1"` (Randomly generated)

```python
import random
import string

def generate_password(length):
    characters = string.ascii_letters + string.digits + string.punctuation
    return ''.join(random.choice(characters) for _ in range(length))

# Testing the function
length = 8
output = generate_password(length)
print("Output:", output)

Output: (Randomly generated, e.g., "A9f$k2R1")

```

**Explanation**:

1. Combine all possible characters (letters, digits, special characters).
2. Use `random.choice` to randomly select characters for the specified `length`.

### **Check Armstrong Number**

**Problem**: An Armstrong number (or narcissistic number) is a number that is equal to the sum of its digits each raised to the power of the number of digits. For example, `153 = 1^3 + 5^3 + 3^3`.

**Example**

Input: `153`

Output: `True`

```python
def is_armstrong(n):
    digits = str(n)
    power = len(digits)
    return n == sum(int(d) ** power for d in digits)

# Testing the function
n = 153
output = is_armstrong(n)
print("Output:", output)

Output: True

```

**Explanation**:

1. Convert the number to a string to access each digit.
2. Calculate `sum(int(d) ** power for d in digits)`, where `power` is the number of digits.
3. If the sum equals `n`, it’s an Armstrong number.

### **Find All Unique Triplets That Sum to Zero**

**Problem**: Given an array of integers, find all unique triplets (a,b,c)(a, b, c)(a,b,c) such that a+b+c=0a + b + c = 0a+b+c=0. The solution set must not contain duplicate triplets.

**Example**

Input: `nums = [-1, 0, 1, 2, -1, -4]`

Output: `[[-1, -1, 2], [-1, 0, 1]]`

```python
def three_sum(nums):
    nums.sort()
    result = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue
        left, right = i + 1, len(nums) - 1
        while left < right:
            s = nums[i] + nums[left] + nums[right]
            if s == 0:
                result.append([nums[i], nums[left], nums[right]])
                while left < right and nums[left] == nums[left + 1]:
                    left += 1
                while left < right and nums[right] == nums[right - 1]:
                    right -= 1
                left += 1
                right -= 1
            elif s < 0:
                left += 1
            else:
                right -= 1
    return result

# Testing the function
nums = [-1, 0, 1, 2, -1, -4]
output = three_sum(nums)
print("Output:", output)

Output: [[-1, -1, 2], [-1, 0, 1]]

```

**Explanation**:

1. Sort `nums` to facilitate the two-pointer approach and easy duplicate handling.
2. For each element in `nums`, use two pointers (`left`, `right`) to find pairs that sum to the negative of the current element.
3. If a triplet sums to zero, add it to `result` and skip duplicates.

### **Container With Most Water**

**Problem**: Given an array `height` representing the height of vertical lines drawn at each index, find two lines that together with the x-axis form a container, such that the container holds the most water.

**Example**

Input: `height = [1,8,6,2,5,4,8,3,7]`

Output: `49`

```python
def max_area(height):
    left, right = 0, len(height) - 1
    max_water = 0
    while left < right:
        width = right - left
        current_water = min(height[left], height[right]) * width
        max_water = max(max_water, current_water)
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_water

# Testing the function
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
output = max_area(height)
print("Output:", output)

Output: 49

```

**Explanation**:

1. Use a two-pointer approach, starting at both ends of the `height` list.
2. Calculate the area for each pair and update `max_water`.
3. Move the pointer at the shorter line inwards to potentially increase the container’s height.

### **Longest Substring Without Repeating Characters**

**Problem**: Given a string, find the length of the longest substring without repeating characters.

**Example**

Input: `"abcabcbb"`

Output: `3` (substring `"abc"`)

```python
def length_of_longest_substring(s):
    char_index = {}
    start = max_length = 0
    for i, char in enumerate(s):
        if char in char_index and char_index[char] >= start:
            start = char_index[char] + 1
        max_length = max(max_length, i - start + 1)
        char_index[char] = i
    return max_length

# Testing the function
s = "abcabcbb"
output = length_of_longest_substring(s)
print("Output:", output)

Output: 3

```

**Explanation**:

1. Use a sliding window with `start` and keep track of the last index of each character in `char_index`.
2. When a duplicate is found, update `start` to avoid repeats.
3. Calculate `max_length` by comparing current window length with `max_length`.

### **Find Kth Largest Element in an Array**

**Problem**: Find the kkk-th largest element in an unsorted array. Note that it is the kkk-th largest element in sorted order, not the kkk-th unique element.

**Example**

Input: `nums = [3, 2, 1, 5, 6, 4], k = 2`

Output: `5`

```python
import heapq

def find_kth_largest(nums, k):
    return heapq.nlargest(k, nums)[-1]

# Testing the function
nums = [3, 2, 1, 5, 6, 4]
k = 2
output = find_kth_largest(nums, k)
print("Output:", output)

Output: 5

```

**Explanation**:

1. Use `heapq.nlargest` to get the largest `k` elements in descending order.
2. The last element in this list is the k-th largest element.
    
    ### **Find Minimum in Rotated Sorted Array**
    
    **Problem**: Given a sorted array that’s been rotated, find the minimum element. You may assume no duplicates exist in the array.
    
    **Example**
    
    Input: `nums = [3, 4, 5, 1, 2]`
    
    Output: `1`
    

```python
def find_min(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]

# Testing the function
nums = [3, 4, 5, 1, 2]
output = find_min(nums)
print("Output:", output)

Output: 1

```

**Explanation**:

1. Use a binary search approach.
2. If `nums[mid] > nums[right]`, the minimum must be to the right of `mid`, so adjust `left`.
3. Otherwise, adjust `right` to `mid` to narrow down the search space.

# Write a function `find_unique_numbers(nums)` that takes a list of integers and returns a list containing all the unique elements in the order they appeared in the original list. A unique element is defined as one that appears only once in the list.

```python
# Input
nums = [4, 3, 2, 4, 1, 3, 2, 5]

# Output
[1, 5]

from collections import Counter

def find_unique_numbers(nums):
    # Count occurrences of each number
    num_counts = Counter(nums)
    # Filter numbers that appear only once and preserve the order
    unique_nums = [num for num in nums if num_counts[num] == 1]
    return unique_nums

# Test example
nums = [4, 3, 2, 4, 1, 3, 2, 5]
print(find_unique_numbers(nums))  # Output: [1, 5]

```

### **Find Duplicates in a List**

- **Question**: Write a function to find duplicates in a list.

```python
def find_duplicates(lst):
    return [x for x in set(lst) if lst.count(x) > 1]

print(find_duplicates([1, 2, 3, 2, 4, 5, 5]))  # Output: [2, 5]

```

### **Factorial of a Number**

- **Question**: Write a recursive function to calculate the factorial of a number

```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)

print(factorial(5))  # Output: 120

```

### **Generate Fibonacci Sequence**

- **Question**: Write a function to generate Fibonacci sequence up to `n` terms

```python
def fibonacci(n):
    fib_sequence = [0, 1]
    while len(fib_sequence) < n:
        fib_sequence.append(fib_sequence[-1] + fib_sequence[-2])
    return fib_sequence[:n]

print(fibonacci(7))  # Output: [0, 1, 1, 2, 3, 5, 8]

```

**Find the Largest and Smallest in a List Without Built-ins**

```python
def find_min_max(lst):
    min_val, max_val = lst[0], lst[0]
    for num in lst:
        if num < min_val:
            min_val = num
        if num > max_val:
            max_val = num
    return min_val, max_val

print(find_min_max([5, 1, 8, -3, 7]))  # Output: (-3, 8)

```

**Implement Binary Search**

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

print(binary_search([1, 2, 3, 4, 5], 3))  # Output: 2

```

**Check if a List is Sorted**

```python
def is_sorted(lst):
    return all(lst[i] <= lst[i + 1] for i in range(len(lst) - 1))

print(is_sorted([1, 2, 2, 3, 5]))  # Output: True

```

**Find the Intersection of Two Arrays**

```python
def intersect(arr1, arr2):
    return list(set(arr1) & set(arr2))

print(intersect([1, 2, 3, 4], [3, 4, 5, 6]))  # Output: [3, 4]

```

**Implement Quick Sort**

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

print(quick_sort([3, 6, 8, 10, 1, 2, 1]))  # Output: [1, 1, 2, 3, 6, 8, 10]

```

**Find the Second Largest Number in a List**

```python
def second_largest(lst):
    unique_lst = list(set(lst))
    unique_lst.sort(reverse=True)
    return unique_lst[1] if len(unique_lst) > 1 else None

print(second_largest([3, 2, 1, 4, 4]))  # Output: 3

```

**Remove Consecutive Duplicates from a String**

```python
def remove_consecutive_duplicates(s):
    result = [s[0]]
    for char in s[1:]:
        if char != result[-1]:
            result.append(char)
    return ''.join(result)

print(remove_consecutive_duplicates("aaabbcaaa"))  # Output: "abca"

```

**Generate a List of Prime Numbers up to `n`**

```python
def generate_primes(n):
    primes = []
    for num in range(2, n + 1):
        is_prime = all(num % i != 0 for i in range(2, int(num ** 0.5) + 1))
        if is_prime:
            primes.append(num)
    return primes

print(generate_primes(10))  # Output: [2, 3, 5, 7]

```

**Transpose a Matrix**

```python
def transpose(matrix):
    return [[matrix[j][i] for j in range(len(matrix))] for i in range(len(matrix[0]))]

print(transpose([[1, 2, 3], [4, 5, 6]]))  # Output: [[1, 4], [2, 5], [3, 6]]

```

**Implement a Stack with `push`, `pop`, and `get_min`**

```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, x):
        self.stack.append(x)
        if not self.min_stack or x <= self.min_stack[-1]:
            self.min_stack.append(x)

    def pop(self):
        if self.stack:
            if self.stack.pop() == self.min_stack[-1]:
                self.min_stack.pop()

    def get_min(self):
        return self.min_stack[-1] if self.min_stack else None

stack = MinStack()
stack.push(5)
stack.push(3)
stack.push(7)
stack.pop()
print(stack.get_min())  # Output: 3

```

**Find All Permutations of a String**

```python
from itertools import permutations

def all_permutations(s):
    return [''.join(p) for p in permutations(s)]

print(all_permutations("abc"))  # Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']

```

**Validate if a Binary Tree is a Binary Search Tree**

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def is_bst(node, left=float('-inf'), right=float('inf')):
    if not node:
        return True
    if not (left < node.val < right):
        return False
    return is_bst(node.left, left, node.val) and is_bst(node.right, node.val, right)

root = TreeNode(2, TreeNode(1), TreeNode(3))
print(is_bst(root))  # Output: True

```

**Find the Longest Common Prefix in a List of Strings**

```python
def longest_common_prefix(strs):
    if not strs:
        return ""
    prefix = strs[0]
    for s in strs[1:]:
        while s[:len(prefix)] != prefix:
            prefix = prefix[:-1]
            if not prefix:
                return ""
    return prefix

print(longest_common_prefix(["flower", "flow", "flight"]))  # Output: "fl"

```

**Maximum Product Subarray**

```python
def max_product_subarray(nums):
    max_prod = min_prod = result = nums[0]
    for num in nums[1:]:
        if num < 0:
            max_prod, min_prod = min_prod, max_prod
        max_prod = max(num, max_prod * num)
        min_prod = min(num, min_prod * num)
        result = max(result, max_prod)
    return result

print(max_product_subarray([2, 3, -2, 4]))  # Output: 6

```

# **`RegEx`**

Here's an expanded table with detailed explanations and examples of each regex symbol in Python:

| Symbol | Description | Example Pattern | Example String | Matches |
| --- | --- | --- | --- | --- |
| `\d` | Matches any digit from 0 to 9. | `\d` | `"age 30"` | `"3"`, `"0"` |
| `\D` | Matches any character that is not a digit. | `\D` | `"Room #21!"` | `"R"`, `"o"`, `"m"`, `"#"`, `"!"` |
| `\w` | Matches any "word character": alphanumeric (a-z, A-Z, 0-9) and underscore `_`. | `\w+` | `"Name_123"` | `"Name_123"` (entire word) |
| `\W` | Matches any "non-word" character (anything not a-z, A-Z, 0-9, or `_`). | `\W` | `"Hello, world!"` | `","`, `" "`, `"!"` |
| `\s` | Matches any whitespace character (spaces, tabs, newlines). | `\s` | `"Hello world"` | `" "` (space) |
| `\S` | Matches any character that is not whitespace. | `\S+` | `"One two"` | `"One"`, `"two"` |
| `.` | Matches any single character except newline `\n`. | `H..o` | `"Hello"` | `"Hell"` |
| `^` | Asserts the start of a string. Used for patterns that should only match if at the beginning of the string. | `^Hello` | `"Hello World"` | `"Hello"` (if it starts the string) |
| `$` | Asserts the end of a string. Used for patterns that should only match if at the end of the string. | `world$` | `"Hello world"` | `"world"` (if it ends the string) |
| `\b` | Asserts a word boundary (e.g., start or end of a word). Useful for matching whole words. | `\bcat\b` | `"the cat sat"` | `"cat"` (isolated word) |
| `\B` | Asserts a non-word boundary, meaning it will not match at the start or end of a word. | `\Bcat\B` | `"scattered"` | `"cat"` (inside word) |
| `[]` | Matches any one character within the brackets. It can define a character class, such as `[a-z]` for lowercase letters. | `[aeiou]` | `"apple"` | `"a"`, `"e"` |
| `[^]` | Matches any character not in the brackets (negation). | `[^aeiou]` | `"apple"` | `"p"`, `"p"`, `"l"` |
| ` | ` | OR operator, matches either the pattern on the left or right. | `cat | dog` |
| `()` | Groups patterns together and captures them. Allows for sub-pattern extraction or repeated matching of complex patterns. | `(cat | dog)` | `"dog"` |
| `*` | Matches 0 or more repetitions of the preceding character or group. | `a*` | `"aaa"` | `"aaa"` |
| `+` | Matches 1 or more repetitions of the preceding character or group. | `a+` | `"aaa"` | `"aaa"` |
| `?` | Matches 0 or 1 instance of the preceding character or group (makes it optional). | `a?` | `"b"` | `""` (no match), `"a"` |
| `{n}` | Matches exactly `n` repetitions of the preceding character or group. | `a{3}` | `"aaaaa"` | `"aaa"` (first three) |
| `{n,}` | Matches `n` or more repetitions of the preceding character or group. | `a{2,}` | `"aaaa"` | `"aaaa"` |
| `{n,m}` | Matches between `n` and `m` repetitions of the preceding character or group. | `a{2,4}` | `"aaaaa"` | `"aaaa"` (up to four) |
| `(?i)` | Enables case-insensitive matching for the entire pattern that follows. | `(?i)hello` | `"HELLO"` | `"HELLO"` |
| `(?<=...)` | Positive lookbehind assertion; matches only if preceded by the specified pattern. | `(?<=\$)\d+` | `"$100"` | `"100"` |
| `(?<!...)` | Negative lookbehind assertion; matches only if not preceded by the specified pattern. | `(?<!\$)\d+` | `"100"` | `"100"` (only if not `$` before) |
| `(?=...)` | Positive lookahead assertion; matches only if followed by the specified pattern. | `\d+(?=%)` | `"50%"` | `"50"` |
| `(?!...)` | Negative lookahead assertion; matches only if not followed by the specified pattern. | `\d+(?!%)` | `"50 dollars"` | `"50"` (if not `%` after) |

Let me know if you’d like to see more complex examples or specific uses of these regex elements!

```python
# 1. Validate Email Address
import re
def is_valid_email(email):
    # Pattern explanation:
    # ^       : Start of the string
    # [\w\.-] : Matches any word character (a-z, A-Z, 0-9, _) or '.' or '-'
    # +       : One or more of the preceding character class
    # @       : Matches the '@' symbol
    # [\w\.-] : Matches any word character, '.', or '-'
    # \.      : Escapes '.' to match it literally
    # \w+     : Matches one or more word characters (domain)
    # $       : End of the string
    pattern = r"^[\w\.-]+@[\w\.-]+\.\w+$"
    return bool(re.match(pattern, email))

# Example
print(is_valid_email("test@example.com"))  # Output: True
print(is_valid_email("invalid-email"))     # Output: False

===============================================================================

# 2. Check for Valid Phone Number
def is_valid_phone(phone):
    # Pattern explanation:
    # ^         : Start of the string
    # \d{3}     : Matches exactly three digits
    # -         : Matches a literal hyphen
    # \d{3}     : Matches exactly three digits
    # -         : Matches a literal hyphen
    # \d{4}     : Matches exactly four digits
    # $         : End of the string
    pattern = r"^\d{3}-\d{3}-\d{4}$"
    return bool(re.match(pattern, phone))

# Example
print(is_valid_phone("123-456-7890"))  # Output: True
print(is_valid_phone("1234567890"))    # Output: False

========================================================================

# 3. Extract Domain from URL
def extract_domain(url):
    # Pattern explanation:
    # https?    : Matches 'http' or 'https' (optional 's')
    # ://       : Matches '://'
    # (www\.)?  : Matches 'www.' optionally (grouped)
    # [\w.-]+   : Matches domain part (letters, numbers, '.', '-')
    pattern = r"https?://(www\.)?([\w.-]+)"
    match = re.search(pattern, url)
    return match.group(2) if match else None

# Example
print(extract_domain("https://www.example.com/path"))  # Output: example.com
print(extract_domain("http://openai.com"))             # Output: openai.com

====================================================================================

# 4. Find All Numbers in a String
def find_all_numbers(s):
    # Pattern explanation:
    # \d+ : Matches one or more digits in a row
    pattern = r"\d+"
    return re.findall(pattern, s)

# Example
print(find_all_numbers("There are 3 apples and 7 bananas"))  # Output: ['3', '7']

===================================================================================

# 5. Validate a Password
def is_valid_password(password):
    # Pattern explanation:
    # ^           : Start of the string
    # (?=.*[a-z]) : Positive lookahead for at least one lowercase letter
    # (?=.*[A-Z]) : Positive lookahead for at least one uppercase letter
    # (?=.*\d)    : Positive lookahead for at least one digit
    # .{8,}       : Matches any character (min length 8)
    # $           : End of the string
    pattern = r"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$"
    return bool(re.match(pattern, password))

# Example
print(is_valid_password("StrongP@ss1"))  # Output: True
print(is_valid_password("weakpass"))     # Output: False

=======================================================================================

# 6. Extract Hashtags from a Tweet
def extract_hashtags(tweet):
    # Pattern explanation:
    # #    : Matches the literal hashtag symbol '#'
    # \w+  : Matches one or more word characters (letters, numbers, _)
    pattern = r"#\w+"
    return re.findall(pattern, tweet)

# Example
print(extract_hashtags("Loving the weather! #sunny #happy"))  # Output: ['#sunny', '#happy']

======================================================================================

# 7. Check if String is a Hexadecimal Number
def is_hexadecimal(s):
    # Pattern explanation:
    # ^          : Start of the string
    # 0x         : Matches the literal '0x' prefix
    # [0-9A-Fa-f]+ : Matches one or more hexadecimal digits
    # $          : End of the string
    pattern = r"^0x[0-9A-Fa-f]+$"
    return bool(re.match(pattern, s))

# Example
print(is_hexadecimal("0x1A3F"))  # Output: True
print(is_hexadecimal("1234"))    # Output: False

=====================================================================================

# 8. Validate Date Format
def is_valid_date(date):
    # Pattern explanation:
    # ^       : Start of the string
    # \d{2}   : Matches exactly two digits (day)
    # /       : Matches a literal slash
    # \d{2}   : Matches exactly two digits (month)
    # /       : Matches a literal slash
    # \d{4}   : Matches exactly four digits (year)
    # $       : End of the string
    pattern = r"^\d{2}/\d{2}/\d{4}$"
    return bool(re.match(pattern, date))

# Example
print(is_valid_date("31/12/2023"))  # Output: True
print(is_valid_date("2023-12-31"))  # Output: False

======================================================================================

# 9. Find All Words in CamelCase
def find_camelcase_words(s):
    # Pattern explanation:
    # \b        : Word boundary
    # [A-Z]     : Matches an uppercase letter
    # [a-z]*    : Matches zero or more lowercase letters
    # [A-Z]     : Another uppercase letter to define CamelCase
    # [a-z]*    : Matches zero or more lowercase letters after the uppercase
    # \b        : Word boundary
    pattern = r"\b[A-Z][a-z]*[A-Z][a-z]*\b"
    return re.findall(pattern, s)

# Example
print(find_camelcase_words("This is CamelCase and MixedCaseWords."))  # Output: ['CamelCase', 'MixedCaseWords']

========================================================================================

# 10. Validate Credit Card Number
def is_valid_credit_card(number):
    # Pattern explanation:
    # ^         : Start of the string
    # \d{4}     : Matches exactly four digits
    # -         : Matches a literal hyphen
    # \d{4}     : Matches four digits
    # -         : Matches a literal hyphen
    # \d{4}     : Matches four digits
    # -         : Matches a literal hyphen
    # \d{4}     : Matches four digits
    # $         : End of the string
    pattern = r"^\d{4}-\d{4}-\d{4}-\d{4}$"
    return bool(re.match(pattern, number))

# Example
print(is_valid_credit_card("1234-5678-9876-5432"))  # Output: True
print(is_valid_credit_card("1234567898765432"))     # Output: False

=====================================================================================

# 11. Validate MAC Address
def is_valid_mac(mac):
    # Pattern explanation:
    # ^            : Start of the string
    # ([0-9A-Fa-f]{2}) : Matches exactly two hexadecimal characters (grouped)
    # (:([0-9A-Fa-f]{2})){5} : Repeats ':XX' (where XX is two hexadecimal digits) five times
    # $            : End of the string
    pattern = r"^([0-9A-Fa-f]{2}(:[0-9A-Fa-f]{2}){5})$"
    return bool(re.match(pattern, mac))

# Example
print(is_valid_mac("01:23:45:67:89:AB"))  # Output: True
print(is_valid_mac("0123.4567.89AB"))     # Output: False

=======================================================================================

# 12. Extract File Extensions
def extract_file_extensions(files):
    # Pattern explanation:
    # \.         : Matches a literal period
    # [A-Za-z0-9]+ : Matches one or more alphanumeric characters for the file extension
    pattern = r"\.[A-Za-z0-9]+"
    return re.findall(pattern, files)

# Example
print(extract_file_extensions("report.pdf, image.png, archive.zip"))  # Output: ['.pdf', '.png', '.zip']

========================================================================================

# 13. Validate Floating Point Number
def is_valid_float(number):
    # Pattern explanation:
    # ^        : Start of the string
    # -?       : Matches an optional negative sign
    # \d+      : Matches one or more digits (integer part)
    # (\.\d+)? : Optionally matches a decimal point followed by one or more digits (fractional part)
    # $        : End of the string
    pattern = r"^-?\d+(\.\d+)?$"
    return bool(re.match(pattern, number))

# Example
print(is_valid_float("123.45"))  # Output: True
print(is_valid_float("123"))     # Output: True
print(is_valid_float("-0.456"))  # Output: True
print(is_valid_float("123abc"))  # Output: False

======================================================================================

# 14. Validate US Phone Number with Optional Country Code
def is_valid_us_phone(phone):
    # Pattern explanation:
    # ^(\+1\s?)? : Matches optional country code '+1' followed by an optional space
    # \d{3}      : Matches exactly three digits (area code)
    # [-\s]?     : Matches an optional hyphen or space
    # \d{3}      : Matches exactly three digits
    # [-\s]?     : Matches an optional hyphen or space
    # \d{4}      : Matches exactly four digits
    # $          : End of the string
    pattern = r"^(\+1\s?)?\d{3}[-\s]?\d{3}[-\s]?\d{4}$"
    return bool(re.match(pattern, phone))

# Example
print(is_valid_us_phone("+1 123-456-7890"))  # Output: True
print(is_valid_us_phone("123 456 7890"))     # Output: True
print(is_valid_us_phone("456-7890"))         # Output: False

=====================================================================================

# 15. Extract URLs from Text
def extract_urls(text):
    # Pattern explanation:
    # http[s]? : Matches 'http' or 'https'
    # ://      : Matches '://'
    # \S+      : Matches one or more non-whitespace characters for the URL path
    pattern = r"http[s]?://\S+"
    return re.findall(pattern, text)

# Example
print(extract_urls("Visit https://example.com and http://test.org"))  # Output: ['https://example.com', 'http://test.org']

```

```python

# 16. Validate HTML Tag
def is_valid_html_tag(tag):
    # Pattern explanation:
    # ^<         : Start with a literal '<'
    # /?         : Matches an optional '/' for closing tags
    # [A-Za-z]+  : Matches one or more letters (tag name)
    # >$         : Ends with a literal '>'
    pattern = r"^<\/?[A-Za-z]+>$"
    return bool(re.match(pattern, tag))

# Example
print(is_valid_html_tag("<div>"))  # Output: True
print(is_valid_html_tag("</span>"))  # Output: True
print(is_valid_html_tag("<1invalid>"))  # Output: False

=====================================================================================
# 17. Validate Credit Card Number (No Separators)
def is_valid_credit_card_no_sep(number):
    # Pattern explanation:
    # ^\d{16}$ : Matches exactly 16 digits
    pattern = r"^\d{16}$"
    return bool(re.match(pattern, number))

# Example
print(is_valid_credit_card_no_sep("1234567812345678"))  # Output: True
print(is_valid_credit_card_no_sep("1234 5678 1234 5678"))  # Output: False

=====================================================================================

# 18. Validate License Plate Format
def is_valid_license_plate(plate):
    # Pattern explanation:
    # ^        : Start of the string
    # [A-Z]{2} : Matches exactly two uppercase letters (state code)
    # \d{2}    : Matches exactly two digits
    # [A-Z]{1,2} : Matches one or two uppercase letters (region code)
    # \d{1,4}  : Matches between one and four digits (unique identifier)
    # $        : End of the string
    pattern = r"^[A-Z]{2}\d{2}[A-Z]{1,2}\d{1,4}$"
    return bool(re.match(pattern, plate))

# Example
print(is_valid_license_plate("AB12CD1234"))  # Output: True
print(is_valid_license_plate("A123BC"))      # Output: False

=====================================================================================

# 19. Extract Sentences Ending with Exclamation Marks
def extract_exclamation_sentences(text):
    # Pattern explanation:
    # [^.?!]* : Matches any sequence of characters not containing '.', '?', or '!'
    # !       : Matches an exclamation mark
    pattern = r"[^.?!]*!"
    return re.findall(pattern, text)

# Example
print(extract_exclamation_sentences("Wow! What a game! Incredible experience."))  # Output: ['Wow!', ' What a game!']

=====================================================================================

# 20. Validate IPv6 Address
def is_valid_ipv6(ipv6):
    # Pattern explanation:
    # ^             : Start of the string
    # ([0-9a-fA-F]{1,4}:){7} : Matches seven blocks of 1 to 4 hex digits followed by colons
    # [0-9a-fA-F]{1,4} : Matches the final block of 1 to 4 hex digits
    # $             : End of the string
    pattern = r"^([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}$"
    return bool(re.match(pattern, ipv6))

# Example
print(is_valid_ipv6("2001:0db8:85a3:0000:0000:8a2e:0370:7334"))  # Output: True
print(is_valid_ipv6("1234:5678:9abc:def::abcd"))  # Output: False

=====================================================================================
# 21. Extract All Words Containing 'ing'
def extract_ing_words(text):
    # Pattern explanation:
    # \b       : Word boundary
    # \w*ing   : Matches any word ending with 'ing'
    # \b       : Word boundary
    pattern = r"\b\w*ing\b"
    return re.findall(pattern, text)

# Example
print(extract_ing_words("I am running, singing, and dancing in the rain."))  # Output: ['running', 'singing', 'dancing']

=====================================================================================
# 22. Validate Hexadecimal Color Code (With Optional Alpha Channel)
def is_valid_hex_color_alpha(color):
    # Pattern explanation:
    # ^        : Start of the string
    # #        : Matches the literal '#'
    # [0-9A-Fa-f]{6} : Matches exactly six hexadecimal digits
    # ([0-9A-Fa-f]{2})? : Optionally matches two additional hexadecimal digits (alpha channel)
    # $        : End of the string
    pattern = r"^#[0-9A-Fa-f]{6}([0-9A-Fa-f]{2})?$"
    return bool(re.match(pattern, color))

# Example
print(is_valid_hex_color_alpha("#1A2B3C"))     # Output: True
print(is_valid_hex_color_alpha("#1A2B3CFF"))   # Output: True
print(is_valid_hex_color_alpha("#1A2B3"))      # Output: False

=====================================================================================
# 23. Extract All Non-Alphanumeric Characters
def extract_non_alphanumeric(text):
    # Pattern explanation:
    # [^\w\s] : Matches any character that is not a word character or whitespace
    pattern = r"[^\w\s]"
    return re.findall(pattern, text)

# Example
print(extract_non_alphanumeric("Hello, world! #Python3"))  # Output: [',', '!', '#']

=====================================================================================
# 24. Extract All Words Containing Numbers
def extract_words_with_numbers(text):
    # Pattern explanation:
    # \b        : Word boundary
    # \w*\d\w*  : Matches any word containing at least one digit
    # \b        : Word boundary
    pattern = r"\b\w*\d\w*\b"
    return re.findall(pattern, text)

# Example
print(extract_words_with_numbers("My email is user123 and code is ABC4567."))  # Output: ['user123', 'ABC4567']

=====================================================================================

# 25. Validate Hexadecimal Color Code with Alpha (e.g., #A1B2C3 or #A1B2C3FF)
def is_valid_hex_alpha(color):
    # Pattern explanation:
    # ^         : Start of the string
    # #         : Matches the literal '#'
    # [0-9A-Fa-f]{6} : Matches six hexadecimal digits (RGB)
    # ([0-9A-Fa-f]{2})? : Optionally matches two more hexadecimal digits (Alpha)
    # $         : End of the string
    pattern = r"^#[0-9A-Fa-f]{6}([0-9A-Fa-f]{2})?$"
    return bool(re.match(pattern, color))

# Example
print(is_valid_hex_alpha("#A1B2C3"))      # Output: True
print(is_valid_hex_alpha("#A1B2C3FF"))    # Output: True
print(is_valid_hex_alpha("#A1B2C3FFF"))   # Output: False

=====================================================================================
# 26. Extract All Quoted Strings (Single or Double Quotes)
def extract_quoted_strings(text):
    # Pattern explanation:
    # ['"]     : Matches a single or double quote
    # .*?      : Non-greedy match for any characters inside quotes
    # ['"]     : Matches the closing quote
    pattern = r"['\"].*?['\"]"
    return re.findall(pattern, text)

# Example
print(extract_quoted_strings('He said, "Hello!" and then replied with, \'Hi!\''))  
# Output: ['"Hello!"', "'Hi!'"]

=====================================================================================
# 27. Validate Canadian Postal Code (Format: A1A 1A1)
def is_valid_canadian_postal_code(code):
    # Pattern explanation:
    # ^         : Start of the string
    # [A-Za-z]  : Matches a single letter
    # \d        : Matches a single digit
    # [A-Za-z]  : Matches a single letter
    # \s        : Matches a space
    # \d        : Matches a single digit
    # [A-Za-z]  : Matches a single letter
    # \d        : Matches a single digit
    # $         : End of the string
    pattern = r"^[A-Za-z]\d[A-Za-z] \d[A-Za-z]\d$"
    return bool(re.match(pattern, code))

# Example
print(is_valid_canadian_postal_code("K1A 0B1"))  # Output: True
print(is_valid_canadian_postal_code("123 ABC"))  # Output: False

=====================================================================================
# 28. Extract IPv6 Addresses
def extract_ipv6_addresses(text):
    # Pattern explanation:
    # (?:[A-Fa-f0-9]{1,4}:){7} : Matches 7 groups of 1 to 4 hex digits followed by a colon
    # [A-Fa-f0-9]{1,4}         : Matches a final group of 1 to 4 hex digits
    pattern = r"(?:[A-Fa-f0-9]{1,4}:){7}[A-Fa-f0-9]{1,4}"
    return re.findall(pattern, text)

# Example
print(extract_ipv6_addresses("Connected via 2001:0db8:85a3:0000:0000:8a2e:0370:7334 and fe80::1"))  
# Output: ['2001:0db8:85a3:0000:0000:8a2e:0370:7334']

=====================================================================================
# 29. Validate File Path (Windows Style, e.g., C:\Folder\File.txt)
def is_valid_windows_path(path):
    # Pattern explanation:
    # ^[A-Z]:\\      : Matches a drive letter (A-Z) followed by ":\"
    # ([\w\s]+\\)*   : Matches folder names and spaces, ending with "\"
    # [\w\s]+\.\w+   : Matches a filename with extension
    # $              : End of the string
    pattern = r"^[A-Z]:\\([\w\s]+\\)*[\w\s]+\.\w+$"
    return bool(re.match(pattern, path))

# Example
print(is_valid_windows_path("C:\\Users\\Documents\\file.txt"))  # Output: True
print(is_valid_windows_path("C:/Users/Documents/file.txt"))     # Output: False

=====================================================================================
# 30. Extract Words Containing Only Vowels
def extract_vowel_only_words(text):
    # Pattern explanation:
    # \b       : Word boundary
    # [AEIOUaeiou]+ : Matches one or more vowels
    # \b       : Word boundary
    pattern = r"\b[AEIOUaeiou]+\b"
    return re.findall(pattern, text)

# Example
print(extract_vowel_only_words("I am an AI enthusiast"))  # Output: ['I', 'AI']

```