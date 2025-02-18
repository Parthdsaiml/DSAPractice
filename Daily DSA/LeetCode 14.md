### **LeetCode 14: Longest Common Prefix**

#### **Explanation**
Find the longest common prefix string among an array of strings. If there is no common prefix, return an empty string `""`.

---

#### **Test Cases**
1. Input: `["flower", "flow", "flight"]`  
   Output: `"fl"`

2. Input: `["dog", "racecar", "car"]`  
   Output: `""`  
   Explanation: No common prefix exists.

3. Input: `["interspecies", "interstellar", "interstate"]`  
   Output: `"inters"`

4. Input: `["a"]`  
   Output: `"a"`

5. Input: `[""]`  
   Output: `""`

---

### **Approach: Sort and Compare First and Last Strings**

#### **Algorithm**
1. **Sort the Array**:
   - Sorting the array lexicographically ensures that the strings with the most differences are at the extremes.
   - The first and last strings in the sorted array will have the smallest overlap (common prefix).
2. **Compare Characters**:
   - Compare characters of the first and last strings one by one.
   - Stop when a mismatch occurs or when you reach the end of either string.
3. **Return the Common Prefix**:
   - The matched characters form the longest common prefix.

---

#### **Flowchart**
```
[Start]
   |
   v
If `strs` is empty:
   |
   v
Return ""
   |
   v
Sort `strs` lexicographically
   |
   v
Set `first = strs[0]`, `last = strs[strs.length - 1]`
   |
   v
Initialize `i = 0`
   |
   v
While `i < length of first` and `i < length of last`:
   |
   v
If `first[i] != last[i]`:
   |
   v
Break the loop
   |
   v
Increment `i`
   |
   v
Return `first.substring(0, i)`
   |
   v
[End]
```

---

#### **Code Implementation**
```java
import java.util.Arrays;

public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        
        // Step 1: Sort the array lexicographically
        Arrays.sort(strs);
        
        // Step 2: Compare the first and last strings
        String first = strs[0];
        String last = strs[strs.length - 1];
        
        // Step 3: Find the common prefix between first and last
        int i = 0;
        while (i < first.length() && i < last.length() && first.charAt(i) == last.charAt(i)) {
            i++;
        }
        
        // Step 4: Return the common prefix
        return first.substring(0, i);
    }
}
```

---

#### **Time and Space Complexity**
- **Time Complexity**:  
  - Sorting the array takes $O(n \cdot m \log n)$, where $n$ is the number of strings and $m$ is the average length of each string.  
  - Comparing the first and last strings takes $O(m)$.  
  - Overall: $O(n \cdot m \log n)$.
  
- **Space Complexity**:  
  - Sorting requires $O(n \cdot m)$ space for temporary storage.  
  - Overall: $O(n \cdot m)$.

---

### **Why This Approach Works**
- After sorting, the first and last strings will have the smallest overlap because they are the most different in lexicographical order.  
- By comparing only these two strings, we can efficiently determine the longest common prefix without checking every pair of strings.

---

### **Conclusion**
This approach leverages sorting to reduce the problem to comparing just two strings (the first and last). It is simple and efficient for small to medium-sized inputs. However, the sorting step makes it less efficient for very large inputs compared to other methods like vertical or horizontal scanning.
