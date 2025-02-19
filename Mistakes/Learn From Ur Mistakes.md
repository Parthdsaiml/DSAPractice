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
