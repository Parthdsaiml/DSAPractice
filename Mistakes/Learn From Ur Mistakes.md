### Key Points to Remember for Similar Problems (Learning from Mistakes):  

1. **Use Sorting for Pattern Matching:**  
   - When dealing with anagrams or similar pattern-based problems, sorting strings is a quick way to create a unique key.  
   - Example: "eat" → "aet", "tea" → "aet" (same key for anagrams).  

2. **HashMap for Grouping Similar Patterns:**  
   - Use a HashMap with the sorted string as the key.  
   - Collect all strings with the same sorted key into a list (grouping).  

3. **`putIfAbsent()` Shortcut:**  
   - `res.putIfAbsent(key, new ArrayList<>())` is a concise way to initialize a list if the key doesn’t exist.  

4. **Efficient Lookup with Hashing:**  
   - HashMaps allow quick lookups, making them perfect for grouping problems.  

5. **Convert Arrays to Strings:**  
   - Use `String sortedS = new String(charArray);` after sorting a character array to store it as a key.  

### **Rule of Thumb for Pattern Problems:**  
**"If you can reduce multiple inputs to a common 'signature' (like sorted letters or frequency counts), use a HashMap to group results."**  

Remember this logic for problems like:  
- **Group Anagrams**  
- **Find Duplicate Files**  
- **Group Shifted Strings**  

