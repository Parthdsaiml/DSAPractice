### **2D Range Sum Query – Immutable (Leetcode 304)**  

#### **Problem Statement**  
Given a `2D matrix`, multiple queries ask for the sum of elements in a given submatrix `(row1, col1) → (row2, col2)`.  

---

### **Example**  
#### **Input:**  
```plaintext
matrix = [
  [3,  0,  1,  4,  2],
  [5,  6,  3,  2,  1],
  [1,  2,  0,  1,  5],
  [4,  1,  0,  1,  7],
  [1,  0,  3,  0,  5]
]
Query: sumRegion(2, 1, 4, 3)
```
#### **Output:**  
`8`  

**Explanation:** The sum of elements inside the submatrix is:  
```plaintext
  2  0  1  
  1  0  1  
  0  3  0  
```
Sum = `2 + 0 + 1 + 1 + 0 + 1 + 0 + 3 + 0 = 8`  

---

### **Approach: Prefix Sum (O(1) Query, O(m*n) Preprocessing)**  
1. **Precompute a `prefixSum` matrix** where `prefix[i][j]` stores the sum of all elements from `(0,0) → (i,j)`.  
2. **Query in O(1)** using the formula:  

   \[
   \text{sumRegion}(r1, c1, r2, c2) = \text{prefix}[r2][c2] - \text{prefix}[r1-1][c2] - \text{prefix}[r2][c1-1] + \text{prefix}[r1-1][c1-1]
   \]

   - This formula avoids looping by using previously computed sums.

---

### **Code (Java)**
```java
class NumMatrix {
    private int[][] prefixSum;

    public NumMatrix(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        prefixSum = new int[m + 1][n + 1]; // Extra row & col to handle boundaries

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                prefixSum[i + 1][j + 1] = matrix[i][j] 
                                        + prefixSum[i][j + 1] 
                                        + prefixSum[i + 1][j] 
                                        - prefixSum[i][j];
            }
        }
    }

    public int sumRegion(int row1, int col1, int row2, int col2) {
        return prefixSum[row2 + 1][col2 + 1] 
             - prefixSum[row1][col2 + 1] 
             - prefixSum[row2 + 1][col1] 
             + prefixSum[row1][col1];
    }
}
```

---

### **Complexity Analysis**
| Operation     | Time Complexity |
|--------------|----------------|
| Preprocessing | O(m × n)       |
| Query        | O(1)            |
| Space        | O(m × n)        |

---

### **Key Insights**
✅ **Why use an extra row & column?**  
   - It simplifies boundary checks (no need for `if` conditions).  

✅ **Why subtract & add in the formula?**  
   - Prevents double-counting overlapping regions.  

✅ **Best for multiple queries**  
   - Once `prefixSum` is built, each query takes O(1).
