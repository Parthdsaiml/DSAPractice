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
