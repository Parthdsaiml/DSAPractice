### **Leetcode 75: Sort Colors (Detailed Explanation)**  

🔗 **Problem Link:** [Leetcode 75 - Sort Colors](https://leetcode.com/problems/sort-colors/)  

### **Problem Statement:**  
You are given an array `nums` containing only `0s`, `1s`, and `2s`. Sort the array **in-place** without using the built-in sort function.

---
### **Example:**  
**Input:** `nums = [2,0,2,1,1,0]`  
**Output:** `[0,0,1,1,2,2]`  

---
### **Approach 1: Counting Sort (Two-Pass Solution)**  
✅ **Steps:**  
1. Count the occurrences of `0s`, `1s`, and `2s` in a `countArray[3]`.  
2. Overwrite `nums` with `0s`, then `1s`, then `2s` based on counts.  

✅ **Time Complexity:** `O(n) + O(n) = O(n)`  
✅ **Space Complexity:** `O(1)` (since `countArray` is fixed size `3`)  

---
### **Java Code (Counting Sort)**
```java
import java.util.Arrays;

class Solution {
    public void sortColors(int[] nums) {
        sortColors_2(nums);
    }

    public static void sortColors_2(int[] arr) {
        int[] countArray = new int[3];

        // Count occurrences of 0, 1, and 2
        for (int i : arr) {
            countArray[i]++;
        }

        // Overwrite original array based on counts
        int i = 0;
        for (; i < countArray[0]; i++) arr[i] = 0;
        for (; i < countArray[0] + countArray[1]; i++) arr[i] = 1;
        for (; i < countArray[0] + countArray[1] + countArray[2]; i++) arr[i] = 2;

        System.out.println(Arrays.toString(arr)); // Optional: Print sorted array
    }
}
```

---
### **Approach 2: Dutch National Flag Algorithm (One-Pass, O(n))**  
✅ **Steps:**  
1. Use three pointers: `low`, `mid`, and `high`.  
2. Move `0s` to the left, `2s` to the right, and keep `1s` in the middle.  
3. **Swap and shift pointers accordingly.**  

✅ **Time Complexity:** `O(n)`  
✅ **Space Complexity:** `O(1)`  

---
### **Java Code (Dutch National Flag Algorithm)**
```java
class Solution {
    public void sortColors(int[] nums) {
        int low = 0, mid = 0, high = nums.length - 1;

        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums, low++, mid++);
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                swap(nums, mid, high--);
            }
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

---
### **Which Approach to Use?**  
1. **Counting Sort (Two-Pass)** – Simple & easy but scans twice.  
2. **Dutch National Flag (One-Pass)** – Optimized for performance (single pass).  

💡 **Best Choice:** **Dutch National Flag Algorithm** for real-world efficiency! 🚀
