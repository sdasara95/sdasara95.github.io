---
layout: post
title: Leetcode, Data Structures & Algorithms 
subtitle: Quick Refresher 
cover-img: "/assets/img/dsa.jpg"
tags: [personal, ramblings, algorithms, datastructures, leetcode, dsa]
comments: true
---

One very painful aspect of searching for a job as an experienced software engineer is preparing for leetcode datastructures algorithms problems again from scratch. Your 🧠 brain cache can only hold so much information at a particular point of time and if you're actually doing work at your job you'll definitely forget solving DSA problems quickly. The keyword here is **quickly** because you're expected to solve within a 30 minute or 45 minute time window. That's where you need to learn to do pattern matching quickly.

This article refers heavily from these two links : [Leetcode Cheatsheet](https://leetcode.com/explore/interview/card/cheatsheets/720/resources/4725/) and [ByteByteGo Interview Patterns](https://bytebytego.com/courses/coding-patterns/two-pointers/introduction-to-two-pointers)

# Big O Complexity Chart

![](/assets/img/big-o.png)

Remember that n! > 2^n because values > 2 get multiplied n times !

# Problem Patterns

![](/assets/img/leetcode_flowchart.png)

Look at the input and the question asked. Based on that you should be able to detect some pattern. Speak actively with the interviewer and ask questions and seek their confirmation to proceed down particular route. Also think aloud so your interviewer can know what's going on in your mind. For coding assessment rounds, these patterns should give you a pointer in the right direction.

# Code Templates

## Two Pointers : one input, opposite ends

```python
def fn(arr):
    left = ans = 0
    right = len(arr) - 1

    while left < right:
        # do some logic here with left and right
        if CONDITION:
            left += 1
        else:
            right -= 1
        
        # or do both same time: left += 1 and right -= 1
    
    return ans
```

This two pointer opposite end **inward pattern** is useful for comparing elements at opposite ends like **valid palindrome** or **largest container**

## Two Pointers : two inputs from same direction, exhaust both

```python
def fn(arr1, arr2):
    i = j = ans = 0

    while i < len(arr1) and j < len(arr2):
        # do some logic here
        if CONDITION:
            i += 1
        else:
            j += 1
    
    while i < len(arr1):
        # do logic
        i += 1
    
    while j < len(arr2):
        # do logic
        j += 1
    
    return ans
```

**Unidirectional Traversal**

* One pointer finds information and other pointer keeps track of this information.

**Staged Traversal**

* Both pointers start at same end of the data structure i.e. beginning/end. One pointer is used to search for something, and once found, second pointer finds additional information concerning the first pointer. Things happen in stages.

## Sliding Window

```python
left = right = 0
while right < n:
    # If the window has reached the expected fixed length, we slide the window (move both left and right).
    if right - left + 1 == fixed_window_size:
        # Process the current window.
        result = process_current_window()
        left += 1
    right += 1

```

**Dynamic Sliding Window**

* To **expand** the window advance the **right pointer**
* To **shrink** the window advance the **left pointer** 
* To **slide** the window advance **both pointers** 

Eg. Longest substring with unique characters

**Fixed Sliding Window**

* Only slide by advancing both pointers. Use when problem asks **find a subcomponent of a certain length**.

Eg. Substring Anagrams

## Prefix Sums / K Sum Subarrays

```python
from collections import defaultdict

def compute_prefix_sums(nums):
    # Start by adding the first number to the prefix sums array.
    prefix_sum = [nums[0]]
    # For all remaining indexes, add 'nums[i]' to the cumulative sum from the previous index.
    for i in range(1, len(nums)):
        # Running total can be a SUM or PRODUCT depends on problem
        running = nums[i] + prefix[-1]
        prefix_sum.append(running)


def compute_k_subarrays(arr, k):
    counts = defaultdict(int)
    counts[0] = 1
    ans = curr = 0

    for num in arr:
        # do logic to change curr
        ans += counts[curr - k]
        counts[curr] += 1
    
    return ans
```

There could be +ve or -ve values in the array.

Eg. Sum between range, K-Sum Subarrays, Product Array without Current Element

## Linked List : Fast and Slow Pointer

```python
class ListNode:
   def __init__(self, val: int, next: ListNode):
       self.val = val
       self.next = next

def fn(head):
    slow = head
    fast = head
    ans = 0

    while fast and fast.next:
        # do logic
        slow = slow.next
        fast = fast.next.next
    
    return ans
```

This is used to **detect cycles in a linked list.** The distance of fast pointer from slow pointer at every iteration will keep increasing one more step eventually meeting the slow pointer again if there is a cycle.

## Reverse Linked List

```python
def fn(head):
    curr = head
    prev = None
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node 
        
    return prev
```

When you reverse current node you need to store the next node as temp initially so you can reference it later to continue traversal.

## Monotonic Increasing Stack

```python
def monotonic_stack(arr):
    stack = []
    ans = 0

    for num in arr:
        # for monotonic decreasing, just flip the > to <
        while stack and stack[-1] > num:
            # do logic
            stack.pop()
        stack.append(num)
    
    return ans

def basic_sliding_window(arr):
    left = ans = curr = 0

    for right in range(len(arr)):
        # do logic here to add arr[right] to curr

        while WINDOW_CONDITION_BROKEN:
            # remove arr[left] from curr
            left += 1

        # update ans
    return ans
```

**Monotonic Stack** is used to find the break in pattern i.e. pivot point for elements in a stack. This is used to find the largest or smallest index previously.

It's pattern is similar to a basic sliding window where instead of shifting left pointer based on window condition we just pop elements from the stack till it's empty or top of the stack is less than or greater than current element depending on our problem.

For loop -> Traverse the array

While loop inside -> Process logic wrt stack / left pointer

**Largest Rectange/ Square Area in a Histogram** is famous problem for this pattern.

## Heap

```python
import heapq

def fn(arr, k):
    heap = []
    for num in arr:
        # do some logic to push onto heap according to problem's criteria
        heapq.heappush(heap, (CRITERIA, num))
        if len(heap) > k:
            heapq.heappop(heap)
    
    return [num for num in heap]
```

**Min heap** : prioritizes smallest element by keeping it at the top

**Max heap** : prioritizes max element by keeping it at the top

**Insertion** : *O(log(n))*

**Deletion** : *O(log(n))* 

**Peek** : *O(1)* 

**Heapify** : *O(n)* 

If you already have an unsorted array you can convert it into a heap in *O(n)* but adding or removing element will take *O(log(n))* 

A **Priority queue** is a special type of a heap that allows for customizations in how elements are prioritized.

Finding **Median of an Integer Stream or Array** is classic heap problem where you maintain a min heap and a max heap with equal or 1 difference values and get the median by popping the top elements in both heaps. Greater values are stored in min heap to get lowest of greater values. Lesser values are stored in max heap to get greatest of lesser values. Their mean is your median if both heaps equal in size. 

##  

