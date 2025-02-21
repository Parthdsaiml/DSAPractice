Rerference https://github.com/Parthdsaiml/DSAPractice/blob/main/Mistakes/Learn%20From%20Ur%20Mistakes.md#key-points-to-remember-for-similar-problems-learning-from-mistakes

### 1. **Use Sorting for Pattern Matching:**
   - **Concept:** Sorting strings gives a unique pattern that allows you to group similar strings (like anagrams).
   - **Example:**
     - Strings: `["eat", "tea", "tan", "ate", "nat", "bat"]`
     - Sorted strings:
       - "eat" → "aet"
       - "tea" → "aet"
       - "tan" → "ant"
       - "ate" → "aet"
       - "nat" → "ant"
       - "bat" → "abt"
     - Grouping by sorted keys:
       - `{"aet": ["eat", "tea", "ate"], "ant": ["tan", "nat"], "abt": ["bat"]}`

### 2. **HashMap for Grouping:**
   - **Concept:** Use a HashMap where the key is the sorted string, and the value is a list of strings that are anagrams.
   - **Example:**
     - Using the sorted string as a key:
       - `HashMap<String, List<String>>`
       - Key: `"aet"` → Value: `["eat", "tea", "ate"]`
       - Key: `"ant"` → Value: `["tan", "nat"]`
       - Key: `"abt"` → Value: `["bat"]`

### 3. **`putIfAbsent()` Shortcut:**
   - **Concept:** A shortcut to efficiently add an element to the HashMap, only if the key doesn't already exist.
   - **Example:** 
     - `map.putIfAbsent("aet", new ArrayList<>());`
     - If the key `"aet"` doesn’t exist, a new list will be created and added.

### 4. **Efficient Lookup with Hashing:**
   - **Concept:** HashMaps provide O(1) average-time lookup, making the process of checking and grouping strings fast.
   - **Example:** 
     - When grouping "eat" and "tea", after sorting them both to "aet", the program can check if "aet" exists in the HashMap quickly.

### 5. **Convert Arrays to Strings:**
   - **Concept:** After sorting or counting characters, convert the result into a string to use as a HashMap key.
   - **Example:** 
     - `new String(charArray)` to convert a sorted character array into a string.

---

### 6. **Frequency Counting as a Key (Alternative to Sorting):**
   - **Concept:** Instead of sorting, count the frequency of each character in a string and use that as the key for grouping similar strings.
   - **Example:**
     - String: "eat" → Frequency: `[1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]` (counts of characters 'a', 'e', 't')
     - String: "tea" → Same frequency array as "eat"
     - Grouping by frequency count:
       - `{"[1, 0, 0, ..., 1, 0, 0]": ["eat", "tea", "ate"]}`

### 7. **`int[]` for Frequency:**
   - **Concept:** Use an integer array (of length 26 for the alphabet) to count character frequencies, which is faster than sorting.
   - **Example:** For the string "eat", create an array where each index represents a letter's frequency (index 0 for 'a', index 1 for 'b', etc.).

### 8. **Use `Arrays.toString()` for Key:**
   - **Concept:** Convert the frequency array to a string (or another unique format) to use it as a HashMap key.
   - **Example:** Convert the frequency array `[1, 0, 0, ..., 1, 0, 0]` to `"[1, 0, 0, ..., 1, 0, 0]"` and use this string as the key.

---

### **Rule of Thumb for Pattern Problems:**
- **When order doesn’t matter (like anagrams), use frequency counting as the pattern key.**
  - **Example:** Anagrams "eat", "tea", "ate" all have the same frequency pattern, so they can be grouped together.

By using sorting or frequency counting, you can efficiently group similar strings and patterns, making the solution scalable and faster for larger datasets


Here’s a detailed breakdown of the two questions you provided, in the same structured format:  

---

## **1️⃣ Leetcode 27: Remove Element**  

### **Key Concept: Two-Pointer Technique for In-Place Removal**  
- The **two-pointer** approach efficiently removes elements without using extra space.  
- One pointer (`i`) iterates through the array, while the other (`k`) tracks valid elements.  

### **Example:**  
- **Input:** `nums = [3, 2, 2, 3], val = 3`  
- **Process:**  
  - Iterate through `nums`, moving non-`val` elements to the front.  
  - **Final array:** `[2, 2, _, _]` (Underscores `_` indicate ignored values).  
- **Output:** `2` (new length, elements `[2, 2]`).  

### **Why Two Pointers Work?**  
- **Avoids shifting elements multiple times**, improving efficiency.  
- **Works in O(n) time and O(1) space.**  

---

### **Key Techniques & Mistakes to Avoid:**  

### **1. Use Two Pointers for In-Place Modification**  
- **Concept:** One pointer (`i`) scans elements, another (`k`) places valid ones.  
- **Mistake:** Using `.remove()` or `.pop()` repeatedly increases time complexity.  

### **2. Preserve Order of Remaining Elements**  
- **Concept:** Overwrite `val` occurrences without unnecessary swaps.  
- **Mistake:** If not careful, elements may be swapped incorrectly, breaking order.  

### **3. Return the New Length, Not the Modified Array**  
- **Concept:** The function should return `k`, the count of remaining valid elements.  
- **Mistake:** Modifying and returning the full array instead of the new size.  

---

### **Rule of Thumb for Similar Problems:**  
📌 **"For in-place element removal, use the two-pointer technique to efficiently shift elements."**  

---

## **2️⃣ Leetcode 169: Majority Element**  

### **Key Concept: Boyer-Moore Voting Algorithm**  
- Since the majority element appears **more than `n/2` times**, it must exist.  
- The **Boyer-Moore** algorithm efficiently finds it in **O(n) time and O(1) space.**  

### **Example:**  
- **Input:** `nums = [3, 2, 3]`  
- **Process:**  
  - **Initialize candidate** (`3`), track votes.  
  - If same as candidate → **increase count**.  
  - If different → **decrease count**.  
  - If count reaches `0` → pick a new candidate.  
- **Output:** `3` (majority element).  

---

### **Key Techniques & Mistakes to Avoid:**  

### **1. Boyer-Moore Voting for O(n) Solution**  
- **Concept:** The candidate that survives till the end must be the majority element.  
- **Mistake:** Using sorting (`O(n log n)`) or a HashMap (`O(n)` space) unnecessarily.  

### **2. Candidate Reset Mechanism**  
- **Concept:** If count reaches zero, the next number becomes the new candidate.  
- **Mistake:** Forgetting this step can lead to incorrect results.  

### **3. Single-Pass Determination of Majority**  
- **Concept:** No need for a second pass unless validation is required.  
- **Mistake:** Running additional frequency checks when not needed.  

---

### **Rule of Thumb for Similar Problems:**  
📌 **"When a majority element (> n/2) is guaranteed, use Boyer-Moore Voting for O(n) time and O(1) space."**  

---

# **1. Sort an Array (General Sorting Problem)**  

### **📌 Algorithms to Solve It:**  
1. **Quick Sort** – Best for random arrays, avg **O(n log n)**  
2. **Merge Sort** – Stable, worst-case **O(n log n)**  
3. **Heap Sort** – Efficient for large datasets, **O(n log n)**  
4. **Counting Sort** – Best if values have a small range, **O(n)**  

---

### **📌 Flowchart (QuickSort Example)**
```
      Start
        |
   Check if array 
   has 1 or 0 elem
        |
     No  Yes
    /       \
 Return    Done
    |
 Choose Pivot (middle element)
    |
Partition array:
   - Left side < Pivot
   - Right side > Pivot
    |
Recursively sort left & right parts
    |
Merge sorted parts
    |
      Done!
```

---

### **📌 Time & Space Complexity Analysis**  
| Algorithm  | Best Case | Average Case | Worst Case | Space Complexity |
|------------|-----------|--------------|------------|------------------|
| Quick Sort | O(n log n) | O(n log n)  | O(n²) (rare) | O(log n) (recursion) |
| Merge Sort | O(n log n) | O(n log n)  | O(n log n) | O(n) (extra array) |
| Heap Sort  | O(n log n) | O(n log n)  | O(n log n) | O(1) |
| Counting Sort | O(n) | O(n) | O(n) | O(k) (extra space) |

---

### **📌 Learning from Mistakes (To Improve Further)**
1. **Choosing the Wrong Sorting Algorithm** – Don’t use **QuickSort** if the array is already sorted (worst case **O(n²)**).  
2. **Ignoring Stability** – **Merge Sort** is **stable**, while **QuickSort & HeapSort** are not (important for sorting objects).  
3. **Extra Space Usage** – Merge Sort takes **O(n) space**, while QuickSort (in-place) is **O(log n)** due to recursion.  
4. **For Small Range Values** – Use **Counting Sort** instead of comparison-based sorts like Merge/QuickSort.  

---

# **2. Sort Colors (Sorting 0, 1, 2 Only)**  

### **📌 Algorithms to Solve It:**  
1. **Dutch National Flag Algorithm (Best Approach)** – **O(n) time, O(1) space**  
2. **Counting Sort Approach** – **O(n) time, O(1) space**  

---

### **📌 Flowchart (Dutch National Flag Algorithm)**
```
      Start
        |
   Set three pointers:
   low=0, mid=0, high=n-1
        |
      While mid <= high
        |
      If arr[mid] == 0
         Swap with low
         Move low, mid
        |
      Else if arr[mid] == 1
         Move mid forward
        |
      Else if arr[mid] == 2
         Swap with high
         Move high backward
        |
       Repeat
        |
       Done!
```

---

### **📌 Time & Space Complexity Analysis**  
| Algorithm  | Best Case | Average Case | Worst Case | Space Complexity |
|------------|-----------|--------------|------------|------------------|
| Dutch National Flag | O(n) | O(n)  | O(n) | O(1) |
| Counting Sort | O(n) | O(n) | O(n) | O(1) |

---

### **📌 Learning from Mistakes (To Improve Further)**
1. **Using Sorting Algorithms Like QuickSort** – Overkill for 0, 1, 2; **Dutch National Flag** is faster and in-place.  
2. **Not Using a Single Pass Solution** – Counting Sort is **O(n)** but requires two passes; **Dutch Flag does it in one pass**.  
3. **Swapping Incorrectly** – Always ensure **correct pointer updates** when swapping in Dutch National Flag.  
4. **Overcomplicating Logic** – Don’t use unnecessary comparisons; three simple cases (0,1,2) are enough.  

---

### **📌 Final Takeaway (Pattern for Future Sorting Problems)**
1. **Identify constraints** – Small range? Use **Counting Sort**. Random array? Use **QuickSort**.  
2. **Check stability needs** – If order matters, go with **Merge Sort** over QuickSort.  
3. **Choose in-place sorting if needed** – **Heap Sort or QuickSort** works if space is a concern.  
4. **Always try an O(n) solution for special cases** – Like Dutch National Flag for 0,1,2 sorting.  

---

This **structured pattern** will help us solve more sorting problems **efficiently** in the future! 🚀


# **Top K Frequent Elements**  

### **📌 Algorithms to Solve It:**  
1. **Min Heap (Optimal Approach)** – **O(n log k) time, O(k) space**  
2. **Bucket Sort (Alternative Approach)** – **O(n) time, O(n) space**  

---

### **📌 Flowchart (Min Heap Approach)**
```
      Start
        |
  Count frequency of each element
        |
  Push elements into Min Heap
   (Heap size limited to k)
        |
  If heap size exceeds k
    Remove smallest frequency
        |
  Extract elements from heap
        |
       Done!
```

---

### **📌 Time & Space Complexity Analysis**  
| Algorithm  | Best Case | Average Case | Worst Case | Space Complexity |
|------------|-----------|--------------|------------|------------------|
| Min Heap | O(n log k) | O(n log k) | O(n log k) | O(k) |
| Bucket Sort | O(n) | O(n) | O(n) | O(n) |

---

### **📌 Learning from Mistakes (To Improve Further)**
1. **Sorting the Entire Frequency Map** – Using a **heap** instead of sorting keeps it efficient.  
2. **Not Maintaining Fixed Heap Size** – **Always remove the smallest frequency** when heap size exceeds k.  
3. **Using Max Heap Instead of Min Heap** – **Min Heap** ensures that **least frequent element stays at root**, making replacement efficient.  
4. **Overcomplicating Logic** – If `k` is large, **Bucket Sort can be better** than Min Heap.  

---

### **📌 Final Takeaway (Pattern for Future Frequency-Based Problems)**
1. **Use Min Heap when dealing with "top K" problems** – Keeps memory limited to `k` elements.  
2. **Consider Bucket Sort when dealing with small numbers** – Faster but takes more space.  
3. **Always remove the smallest element when heap exceeds k** – Ensures top k frequent elements remain.  
4. **Hashmaps + Heaps are powerful combos** – Use them whenever frequency counting is needed.  

---

This **structured pattern** will help us solve more **"top K elements"** problems efficiently! 🚀


# **Range Sum Query (Prefix Sum Approach)**  

### **📌 Algorithms to Solve It:**  
1. **Prefix Sum (Optimal for Static Queries)** – **O(1) query time, O(n²) precompute time, O(n²) space**  
2. **Fenwick Tree / Segment Tree (For Dynamic Updates)** – **O(log n) query & update time, O(n) space**  

---

### **📌 Flowchart (Prefix Sum Approach)**
```
      Start
        |
  Compute prefix sum for each row
        |
  For each sumRegion query:
   - Get sum using prefix subtraction
        |
   Return the computed sum
        |
       Done!
```

---

### **📌 Time & Space Complexity Analysis**  
| Algorithm  | Query Time | Precompute Time | Update Time | Space Complexity |
|------------|------------|-----------------|-------------|------------------|
| Prefix Sum | O(1) | O(n²) | O(n²) (Recompute) | O(n²) |
| Fenwick Tree | O(log n) | O(n log n) | O(log n) | O(n) |
| Segment Tree | O(log n) | O(n) | O(log n) | O(n) |

---

### **📌 Learning from Mistakes (To Improve Further)**
1. **Recomputing Sum Every Query** – Instead, **precompute prefix sums** for faster queries.  
2. **Using Naive Nested Loops for Queries** – This takes **O(n²) per query**, too slow for large matrices.  
3. **Ignoring Update Efficiency** – **Prefix sum is bad for updates**, use **Fenwick Tree / Segment Tree** for dynamic queries.  
4. **Choosing Wrong Data Structures** – **Prefix Sum for static queries**, **Fenwick/Segment Tree for updates**.  

---

### **📌 Final Takeaway (Pattern for Future Range Queries)**
1. **If queries are frequent but no updates** – Use **Prefix Sum** for **O(1) queries**.  
2. **If updates are needed** – Use **Fenwick Tree (BIT) or Segment Tree**.  
3. **Precompute smartly** – Avoid recomputation and store cumulative values.  
4. **Use 2D prefix sum for matrices** – Instead of looping over subarrays, **precompute** sums efficiently.  

---

