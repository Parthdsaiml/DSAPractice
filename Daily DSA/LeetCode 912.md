

# **Leetcode 912: Sort an Array (Detailed Explanation)**  

[Leetcode Link](https://leetcode.com/problems/sort-an-array/)  

### **Problem Statement:**  
Given an integer array `nums`, return the array sorted in ascending order.  

---

### **Example:**  
**Input:** `nums = [5,2,3,1]`  
**Step-by-step (Merge Sort Example):**  
1. Divide `[5,2,3,1]` → `[5,2]` & `[3,1]`  
2. Further divide `[5,2]` → `[5]` & `[2]`, `[3,1]` → `[3]` & `[1]`  
3. Merge `[5]` & `[2]` → `[2,5]`, Merge `[3]` & `[1]` → `[1,3]`  
4. Merge `[2,5]` & `[1,3]` → `[1,2,3,5]`  

**Output:** `[1,2,3,5]`  

---

### **Approach (Merge Sort - Divide & Conquer)**  
- **Divide:** Split the array into two halves recursively.  
- **Conquer:** Sort the smaller arrays.  
- **Combine:** Merge two sorted halves.  

---

### **Complexity:**  
- **Time:** O(n log n) - Efficient for large arrays.  
- **Space:** O(n) - Extra space for merging.  

### **Code (Java - Merge Sort Implementation)**  

```java
class Solution {
    public int[] sortArray(int[] nums) {
        if (nums.length <= 1) return nums;
        mergeSort(nums, 0, nums.length - 1);
        return nums;
    }

    private void mergeSort(int[] arr, int left, int right) {
        if (left >= right) return;
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }

    private void merge(int[] arr, int left, int mid, int right) {
        int[] temp = new int[right - left + 1];
        int i = left, j = mid + 1, k = 0;
        
        while (i <= mid && j <= right) {
            temp[k++] = (arr[i] <= arr[j]) ? arr[i++] : arr[j++];
        }
        
        while (i <= mid) temp[k++] = arr[i++];
        while (j <= right) temp[k++] = arr[j++];
        
        System.arraycopy(temp, 0, arr, left, temp.length);
    }
}
```


### **Key Takeaways:**  
📌 **Sort Array:** Use Merge Sort (or Quick Sort) for general sorting problems.  
