### **LeetCode 347: Top K Frequent Elements**  

#### **Explanation**  
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements.  
You may return the answer in any order.  

---

#### **Test Cases**  
1. **Input**: `nums = [1,1,1,2,2,3], k = 2`  
   **Output**: `[1,2]`  
   **Explanation**: The most frequent elements are `1` (appears 3 times) and `2` (appears 2 times).  

2. **Input**: `nums = [1], k = 1`  
   **Output**: `[1]`  
   **Explanation**: The only element is `1`, so it's the most frequent.  

3. **Input**: `nums = [4,4,4,6,6,7,7,7,7], k = 2`  
   **Output**: `[7,4]`  
   **Explanation**: `7` appears 4 times, `4` appears 3 times, `6` appears 2 times. The top `2` are `[7,4]`.  

---

### **Approach: Min-Heap (Priority Queue)**
  
#### **Algorithm**
1. **Count Frequencies**  
   - Use a HashMap to store the frequency of each number.  

2. **Use a Min-Heap to Store Top `K` Elements**  
   - A Min-Heap keeps the smallest element at the top.  
   - Insert elements in the heap based on frequency.  
   - If the heap size exceeds `k`, remove the smallest frequency element.  

3. **Extract Elements from Heap**  
   - Since we stored the `k` most frequent elements, extract and return them.  

---

#### **Flowchart**
```
[Start]
   |
   v
Create a frequency map using HashMap
   |
   v
Initialize a Min-Heap (PriorityQueue)
   |
   v
For each (number, frequency) in HashMap:
   |
   v
Push (frequency, number) into Min-Heap
   |
   v
If heap size > k, remove the smallest frequency element
   |
   v
Extract the elements from the heap
   |
   v
Return the top k frequent elements
   |
   v
[End]
```

---

#### **Code Implementation**
```java
import java.util.*;

public class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // Step 1: Count frequencies
        Map<Integer, Integer> freqMap = new HashMap<>();
        for (int num : nums) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        // Step 2: Use a Min-Heap (size k)
        PriorityQueue<Map.Entry<Integer, Integer>> minHeap = new PriorityQueue<>(
            (a, b) -> a.getValue() - b.getValue()
        );

        for (Map.Entry<Integer, Integer> entry : freqMap.entrySet()) {
            minHeap.add(entry);
            if (minHeap.size() > k) {
                minHeap.poll();  // Remove the element with the lowest frequency
            }
        }

        // Step 3: Extract elements from the heap
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = minHeap.poll().getKey();
        }
        return result;
    }
}
```

---

#### **Time and Space Complexity**
- **Time Complexity**:  
  - **Building the frequency map**: `O(n)`.  
  - **Pushing into heap**: `O(n log k)`, since each insertion/removal in a heap takes `O(log k)`.  
  - **Extracting results**: `O(k log k)`.  
  - **Overall**: `O(n log k)`.  

- **Space Complexity**:  
  - **HashMap storage**: `O(n)`.  
  - **Heap storage**: `O(k)`.  
  - **Overall**: `O(n)`.  

---

### **Why This Approach Works**
- The **Min-Heap** ensures we only keep `k` most frequent elements while discarding the less frequent ones.  
- This is more efficient than sorting (`O(n log n)`) for large datasets.  
- Using a **HashMap** makes frequency counting `O(n)`.  

---

### **Alternative Approach: Bucket Sort (`O(n)`)**
- Instead of a heap, use an **array of lists** indexed by frequency.  
- **Steps**:
  1. Count frequencies (`O(n)`).  
  2. Use an array where index = frequency, store numbers in lists.  
  3. Collect the last `k` elements from this array.  
- **Time Complexity**: `O(n)`.  
- **Better when `n` is large and `k` is small**.  

---

### **Conclusion**
- **Min-Heap (`O(n log k)`)** is best when `k` is much smaller than `n`.  
- **Bucket Sort (`O(n)`)** is useful when `n` is large, and we need linear time.  
- The heap method is **widely applicable** and easy to implement. 🚀
