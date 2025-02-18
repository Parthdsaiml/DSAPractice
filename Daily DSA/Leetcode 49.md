### **LeetCode 49: Group Anagrams**

#### **Explanation**
Group anagrams from an array of strings. Two strings are anagrams if they contain the same characters in a different order. Return the grouped anagrams as a list of lists.

---

#### **Test Cases**
1. Input: `["eat", "tea", "tan", "ate", "nat", "bat"]`  
   Output: `[["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]`

2. Input: `[""]`  
   Output: `[[""]]`

3. Input: `["a"]`  
   Output: `[["a"]]`

---

### **Approach 1: Sort Each String**

#### **Algorithm**
1. Use a hash map where:
   - Key: Sorted version of the string.
   - Value: List of strings that match the key.
2. For each string:
   - Sort its characters to form the key.
   - Add the string to the corresponding group in the map.
3. Return all values (groups) from the map.

---

#### **Flowchart**
```
[Start]
   |
   v
Initialize HashMap `map`
   |
   v
For each string `s` in `strs`:
   |
   v
Sort `s` -> `sortedKey`
   |
   v
If `sortedKey` not in `map`:
   |
   v
Add `sortedKey` -> new ArrayList<>() to `map`
   |
   v
Add `s` to `map.get(sortedKey)`
   |
   v
Return `map.values()`
   |
   v
[End]
```

---

#### **Time and Space Complexity**
- **Time Complexity**: $O(n \cdot k \log k)$, where $n$ is the number of strings and $k$ is the average length of each string (due to sorting).
- **Space Complexity**: $O(n \cdot k)$ for storing the hash map and results.

---

### **Approach 2: Character Frequency Count**

#### **Algorithm**
1. Use a hash map where:
   - Key: String representation of character frequency count.
   - Value: List of strings that match the key.
2. For each string:
   - Create a frequency array of size 26.
   - Count occurrences of each character.
   - Convert the array to a string key.
   - Add the string to the corresponding group in the map.
3. Return all values (groups) from the map.

---

#### **Flowchart**
```
[Start]
   |
   v
Initialize HashMap `map`
   |
   v
For each string `s` in `strs`:
   |
   v
Create int[26] `count`
   |
   v
For each char `c` in `s`:
   |
   v
Increment `count[c - 'a']`
   |
   v
Convert `count` to String `key`
   |
   v
If `key` not in `map`:
   |
   v
Add `key` -> new ArrayList<>() to `map`
   |
   v
Add `s` to `map.get(key)`
   |
   v
Return `map.values()`
   |
   v
[End]
```

---

#### **Time and Space Complexity**
- **Time Complexity**: $O(n \cdot k)$, where $n$ is the number of strings and $k$ is the average length of each string (no sorting overhead).
- **Space Complexity**: $O(n \cdot k)$ for storing the hash map and results.

---

### **Comparison**
| **Aspect**              | **Sorting Approach**       | **Frequency Count Approach** |
|--------------------------|----------------------------|------------------------------|
| **Key Generation**       | Sort string               | Use frequency array          |
| **Time Complexity**      | $O(n \cdot k \log k)$    | $O(n \cdot k)$              |
| **Space Complexity**     | $O(n \cdot k)$           | $O(n \cdot k)$              |
| **Best For**             | Simplicity                | Efficiency                   |

---

### **Conclusion**
Use the **sorting approach** for simplicity or small inputs. Prefer the **frequency count approach** for efficiency with larger inputs.
