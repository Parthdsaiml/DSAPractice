### **Range Query (Sum, Minimum, Maximum, etc.)**  

#### **Problem Statement**  
Given an array, efficiently process multiple queries to find the sum, minimum, or maximum in a given range `[L, R]`.  

---  

#### **Test Cases**  
1. **Sum Query**  
   - Input: `arr = [1, 3, 5, 7, 9, 11]`, Query: `(1, 3)`  
   - Output: `3 + 5 + 7 = 15`  

2. **Minimum Query**  
   - Input: `arr = [2, 6, 1, 8, 3, 5]`, Query: `(2, 5)`  
   - Output: `1`  

3. **Maximum Query**  
   - Input: `arr = [4, 7, 2, 9, 5, 1]`, Query: `(1, 4)`  
   - Output: `9`  

---  

### **Approach 1: Brute Force (O(N) per Query)**  
#### **Algorithm**  
1. Loop through the array from index `L` to `R`.  
2. Compute the sum, min, or max.  
3. Return the result.  

🔴 **Inefficient for multiple queries on large arrays.**  

---  

### **Approach 2: Prefix Sum (O(1) per Sum Query, O(N) for Min/Max)**  
#### **Algorithm for Sum Queries**  
1. **Precompute a Prefix Sum Array:** `prefix[i] = sum(arr[0] to arr[i])`.  
2. **Query in O(1):**  
   - Sum of range `[L, R] = prefix[R] - prefix[L-1]`.  

🔵 **Efficient for sum queries but not for min/max.**  

---  

### **Approach 3: Segment Tree (O(log N) per Query, O(N) Build)**  
#### **Algorithm**  
1. **Build a Segment Tree** in `O(N)`.  
2. **Answer Queries in O(log N)** using a divide-and-conquer approach.  
3. **Supports updates in O(log N)**.  

✅ **Efficient for sum, min, and max queries, even with updates.**  

---

### **Flowchart for Segment Tree Query**
```
[Start]
   |
   v
If query range is completely inside node range:
   |
   v
Return stored value
   |
   v
If query range is outside node range:
   |
   v
Return identity value (0 for sum, ∞ for min, -∞ for max)
   |
   v
Otherwise, split into left and right children
   |
   v
Recursively compute results
   |
   v
Merge results and return
   |
   v
[End]
```

---

### **Code Implementation (Segment Tree - Sum Query)**
```java
class SegmentTree {
    int[] segTree;
    int n;

    public SegmentTree(int[] arr) {
        n = arr.length;
        segTree = new int[4 * n];
        build(arr, 0, 0, n - 1);
    }

    private void build(int[] arr, int node, int left, int right) {
        if (left == right) {
            segTree[node] = arr[left];
            return;
        }
        int mid = (left + right) / 2;
        build(arr, 2 * node + 1, left, mid);
        build(arr, 2 * node + 2, mid + 1, right);
        segTree[node] = segTree[2 * node + 1] + segTree[2 * node + 2]; // Sum
    }

    public int query(int l, int r) {
        return queryUtil(0, 0, n - 1, l, r);
    }

    private int queryUtil(int node, int left, int right, int ql, int qr) {
        if (ql > right || qr < left) return 0;
        if (ql <= left && qr >= right) return segTree[node];
        int mid = (left + right) / 2;
        return queryUtil(2 * node + 1, left, mid, ql, qr) + queryUtil(2 * node + 2, mid + 1, right, ql, qr);
    }
}
```

---

### **Time and Space Complexity**
| Approach       | Build Time | Query Time | Update Time | Space Complexity |
|---------------|------------|------------|------------|------------------|
| Brute Force   | O(1)       | O(N)       | O(1)       | O(1)             |
| Prefix Sum    | O(N)       | O(1)       | O(N)       | O(N)             |
| Segment Tree  | O(N)       | O(log N)   | O(log N)   | O(4N)            |

---

### **Conclusion**
- **Prefix Sum:** Best for sum queries when updates are rare.  
- **Segment Tree:** Best when queries and updates are frequent.  
- **Fenwick Tree:** Alternative to Segment Tree with simpler implementation.  

💡 **Use Segment Tree for real-time updates and frequent range queries.**
