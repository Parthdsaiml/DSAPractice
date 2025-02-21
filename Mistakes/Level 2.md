### Key Points to Remember for Similar Problems (Learning from Mistakes):  

- **Use Sorting for Pattern Matching:** Sorting strings creates a unique key for grouping patterns.  
- **HashMap for Grouping:** Store sorted strings as keys and group anagrams in lists.  
- **`putIfAbsent()` Shortcut:** Quickly initialize a list for new keys.  
- **Efficient Lookup with Hashing:** Use HashMaps for O(1) average-time lookups.  
- **Convert Arrays to Strings:** Use `new String(charArray)` after sorting.  
- **Common Signature Trick:** Reduce inputs to a pattern (sorted or frequency-based) to group similar items.  

**Tip:** For pattern-matching problems, **"Common pattern → HashMap grouping"** is the go-to approach! 💡


### Key Points to Remember from This Solution:  

- **Frequency Counting as a Key:** Instead of sorting, use character counts to represent patterns.  
- **`int[]` for Frequency:** Create an integer array of length 26 to track character frequencies (faster than sorting).  
- **Use `Arrays.toString()` for Key:** Convert the frequency array to a string to use as a HashMap key.  
- **`putIfAbsent()` for Quick Initialization:** Efficiently create a new list if the key doesn't exist.  
- **Pattern-Based Grouping:** Focus on creating a unique signature for similar patterns (like anagrams).  
- **Better for Large Inputs:** Frequency counting is faster than sorting for very large arrays of strings.  

### **Rule of Thumb for Pattern Problems:**  
**"When the order of characters doesn’t matter, use frequency counting as the pattern key."** 💡


### **Key Points to Remember for Similar Problems (Learning from Mistakes)**  

#### **Leetcode 27 (Remove Element) - Key Takeaways**  
- **Two-Pointer Approach for In-Place Modifications:** Using a **start-end pointer** method efficiently moves unwanted elements to the end while keeping necessary elements at the beginning.  
- **Avoid Extra Space:** The solution modifies the array in-place, preventing the need for additional storage.  
- **Swapping Instead of Shifting:** Instead of shifting elements one-by-one (O(n²) in worst cases), **swapping minimizes operations** and runs in **O(n)** time.  
- **Edge Case Handling:** Always check cases like **empty arrays, all elements being the target, or no target present** to ensure robustness.  
- **Return the New Length Instead of a New Array:** When asked to modify in place, return the count of valid elements rather than creating a new array.  

**Tip:**  
✅ **For problems where elements must be removed in-place, two-pointer swapping is often the best approach!**  

---

#### **Leetcode 169 (Majority Element) - Key Takeaways**  
- **Boyer-Moore Voting Algorithm:** A powerful trick when the majority element is **guaranteed to exist** in the array.  
- **Count-Based Elimination:** Increment when the candidate appears, decrement when a different number appears. If count hits 0, choose a new candidate.  
- **Single Pass Solution (O(n) Time, O(1) Space):** Unlike sorting (O(n log n)) or hash maps (O(n) space), Boyer-Moore achieves O(n) time with **constant space**.  
- **Works Only When Majority Exists:** If the problem statement doesn’t guarantee a majority element, this method may fail. Use **sorting or hash maps instead.**  
- **Alternative Approaches:**  
  - **Sorting:** Middle element is always the majority element (O(n log n)).  
  - **HashMap Frequency Counting:** Good for cases where majority isn't guaranteed (O(n) time, O(n) space).  

**Tip:**  
✅ **For problems where an element appears more than ⌊n/2⌋ times, Boyer-Moore is the best approach!**  

---

### **General Lessons for Future Problems**  
✅ **For in-place modifications, always consider a two-pointer technique to reduce space usage.**  
✅ **When searching for a dominant element (appearing > n/2 times), Boyer-Moore Voting is optimal.**  
✅ **Sorting can simplify problems but is often slower than direct counting techniques.**  
✅ **For problems with guarantees (e.g., a majority element always exists), optimize for O(n) solutions.**  
✅ **Always check for edge cases: empty arrays, all identical elements, and elements appearing only once.**  

**Rule of Thumb:**  
📌 **"When removing elements in-place, use two-pointer swapping. When finding majority elements, Boyer-Moore is king!"** 🚀

### **Key Points to Remember for Similar Problems (Learning from Mistakes)**  

#### **Leetcode 912 (Sort an Array) - Key Takeaways**  
- **Merge Sort & QuickSort for Large Inputs:** Merge Sort (O(n log n)) ensures stable sorting, while QuickSort offers in-place efficiency.  
- **Built-in Sorting (Timsort in Java/Python):** Always consider `Arrays.sort()` (Java) or `sorted()` (Python), as they use Timsort, an optimized O(n log n) approach.  
- **Avoid Bubble Sort & Insertion Sort for Large Inputs:** These methods work in O(n²) time, making them impractical for large arrays.  
- **Radix Sort for Integers:** When sorting only non-negative integers, Radix Sort (O(n)) can be faster than comparison-based sorts.  
- **Edge Case Handling:**  
  - Empty array or single-element array.  
  - Already sorted or reverse sorted inputs.  
  - Large datasets (consider heap sort for stability in memory).  

**Tip:**  
✅ **Use built-in sorting unless optimizing for memory. For integer sorting, consider Radix Sort for better performance!**  

---

#### **Leetcode 75 (Sort Colors) - Key Takeaways**  
- **Dutch National Flag Algorithm:** Uses a three-way partitioning approach (O(n) time, O(1) space).  
- **Three Pointers (`low`, `mid`, `high`):**  
  - `low`: Separates 0s (left side).  
  - `mid`: Moves through the array.  
  - `high`: Separates 2s (right side).  
- **Swap-Based Sorting:** Instead of using sorting algorithms, we swap elements in-place for efficiency.  
- **Avoid Extra Space:** Sorting in-place without using extra memory is key for space-constrained problems.  
- **Alternative Approaches:**  
  - **Counting Sort:** Count occurrences of 0s, 1s, and 2s, then overwrite the array.  
  - **Built-in Sort:** Works but isn’t optimal (O(n log n)).  

**Tip:**  
✅ **For sorting 3 distinct values (like 0,1,2), the Dutch National Flag algorithm is the best approach!** 🚀

---

### **Key Points to Remember for Similar Problems (Learning from Mistakes)**  

#### **Leetcode 347 (Top K Frequent Elements) - Key Takeaways**  
- **Heap (Priority Queue) for Efficient Top-K Selection:**  
  - Use a **min-heap** of size **K** to maintain the top K frequent elements in O(n log k) time.  
  - Instead of sorting the entire list, keep only K elements in the heap for efficiency.  
- **HashMap for Frequency Counting:**  
  - Store the frequency of each number in a **HashMap (O(n) time complexity)**.  
- **Bucket Sort for Optimal Performance (O(n)):**  
  - Store numbers in buckets based on frequency (`index = frequency count`).  
  - Flatten the buckets to extract the top K elements efficiently.  
- **Alternative Approach: QuickSelect (O(n) average time)**  
  - QuickSelect can find the Kth largest element efficiently but is tricky to implement.  
- **Edge Cases to Handle:**  
  - K = 1 (return the most frequent element).  
  - All elements have the same frequency.  
  - Large K values close to array length.  

**Tip:**  
✅ **When asked for “Top K” elements, use Heap for efficiency and Bucket Sort for an O(n) alternative!**  

---

#### **Range Query (Sum or Min/Max over a Range) - Key Takeaways**  
- **Segment Tree (O(log n) per query, O(n) build time):**  
  - Best for **dynamic** range queries (sum, min, max, GCD, etc.).  
  - Supports updates in **O(log n)**, making it better than brute force.  
- **Fenwick Tree (Binary Indexed Tree, O(log n) per query & update):**  
  - Simpler than segment trees but supports **prefix sum updates efficiently**.  
  - Ideal when updates and queries are both needed.  
- **Prefix Sum (O(1) query, O(n) precompute):**  
  - Fastest for **static** sum queries (cumulative sum array).  
  - Works only when the array **doesn’t change** after precomputing.  
- **Mo’s Algorithm (O(√n) per query):**  
  - Optimized for offline queries when updates are not needed.  
  - Great when the number of queries is large compared to updates.  
- **Edge Cases to Handle:**  
  - Query range beyond array bounds.  
  - Large input sizes (use **efficient data structures** like segment trees).  
  - Array with duplicate values affecting min/max queries.  

**Tip:**  
✅ **For dynamic updates, use Segment Trees. For static range sums, Prefix Sum is the fastest!** 🚀  


