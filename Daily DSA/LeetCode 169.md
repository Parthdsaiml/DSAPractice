## **Leetcode 169: Majority Element**  

### **Problem Statement:**  
Given an array `nums` of size `n`, return the **majority element**.  
- The majority element appears **more than ⌊n/2⌋ times**.  
- Assume that a majority element **always exists**.  

---

### **Algorithm (Boyer-Moore Voting Algorithm):**
1. **Initialize variables:**  
   - `majorityElement = 0`, `count = 0`
2. **Iterate through the array:**  
   - If `count == 0`, assign `majorityElement = nums[j]`.  
   - If `nums[j]` matches `majorityElement`, increase `count`.  
   - Else, decrease `count`.  
3. **Return `majorityElement`** (Guaranteed to be correct).  

---

### **Flowchart:**  
```
[Start]
   |
   v
Set `majorityElement = 0`, `count = 0`
   |
   v
For each element `nums[j]`:
   |
   v
If `count == 0`:
   |
   v
Set `majorityElement = nums[j]`
   |
   v
If `nums[j] == majorityElement`:
   |
   v
Increment `count`
   |
   v
Else:
   |
   v
Decrement `count`
   |
   v
Return `majorityElement`
   |
   v
[End]
```

---

### **Time & Space Complexity:**  
- **Time Complexity:** **O(n)** (Single pass through the array)  
- **Space Complexity:** **O(1)** (Uses only constant space)  

---

### **Test Cases:**  

#### **Test Case 1: Basic Example**  
**Input:**  
```java
nums = [3, 2, 3]
```
**Expected Output:**  
```java
Majority Element = 3
```

---

#### **Test Case 2: Majority Element at the Start**  
**Input:**  
```java
nums = [2, 2, 1, 1, 1, 2, 2]
```
**Expected Output:**  
```java
Majority Element = 2
```

---

#### **Test Case 3: All Elements Same**  
**Input:**  
```java
nums = [7, 7, 7, 7]
```
**Expected Output:**  
```java
Majority Element = 7
```

---

#### **Test Case 4: Large Input with Majority in Middle**  
**Input:**  
```java
nums = [1, 1, 2, 2, 2, 2, 2, 3, 3]
```
**Expected Output:**  
```java
Majority Element = 2
```

---

#### **Test Case 5: Single Element Array**  
**Input:**  
```java
nums = [5]
```
**Expected Output:**  
```java
Majority Element = 5
```

---

