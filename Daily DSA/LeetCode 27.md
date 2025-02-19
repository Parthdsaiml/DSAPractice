## **Leetcode 27: Remove Element**  

### **Problem Statement:**  
Given an array `nums` and an integer `val`, remove all occurrences of `val` **in-place** and return the number of remaining elements. The order of the elements may change.

---

### **Test Cases for Leetcode 27: Remove Element**  

#### **Test Case 1: Basic Example**  
**Input:**  
```java
nums = [3, 2, 2, 3], val = 3
```
**Expected Output:**  
```java
New length = 2, Modified array = [2, 2, _, _]  (Underscores represent ignored values)
```

---

#### **Test Case 2: No Occurrence of `val`**  
**Input:**  
```java
nums = [1, 2, 3, 4], val = 5
```
**Expected Output:**  
```java
New length = 4, Modified array = [1, 2, 3, 4]
```

---

#### **Test Case 3: All Elements Are `val`**  
**Input:**  
```java
nums = [2, 2, 2, 2], val = 2
```
**Expected Output:**  
```java
New length = 0, Modified array = [_, _, _, _]
```

---

#### **Test Case 4: `val` Appears in the Middle**  
**Input:**  
```java
nums = [0, 1, 2, 2, 3, 0, 4, 2], val = 2
```
**Expected Output:**  
```java
New length = 5, Modified array = [0, 1, 4, 0, 3, _, _, _]
```

---

#### **Test Case 5: Empty Array**  
**Input:**  
```java
nums = [], val = 1
```
**Expected Output:**  
```java
New length = 0, Modified array = []
```

---

### **Algorithm:**
1. **Two Pointers Approach**  
   - Use two pointers: `start` (beginning) and `end` (end of array).  
   - If `nums[start]` matches `val`, swap it with `nums[end]` and decrease `end`.  
   - If `nums[start]` doesn't match `val`, move `start` forward.  
   - Repeat until `start` crosses `end`.  
   - Return `start` as the new length.

---

### **Flowchart:**  
```
[Start]
   |
   v
Set `start = 0`, `end = nums.length - 1`
   |
   v
While `start <= end`:
   |
   v
If `nums[start] == val`:
   |
   v
    If `nums[end] != val`:
       Swap `nums[start]` and `nums[end]`
    Else:
       Decrement `end`
   |
   v
Else:
   Increment `start`
   |
   v
Return `start`
   |
   v
[End]
```

---

### **Time & Space Complexity:**  
- **Time Complexity:** **O(n)** (Each element is checked once)  
- **Space Complexity:** **O(1)** (In-place modification, no extra space)
