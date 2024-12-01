```java
class Solution {
    public boolean isAnagram(String s, String t) {
        return validAnagrams(s, t);
    }
     public static boolean validAnagrams(String string, String tString){
        int[] charArray = new int[26];
        for (int i = 0; i < string.length(); i++) {
            charArray[(int)(string.charAt(i)) - 97] += 1;
        }
        for (int i = 0; i < tString.length(); i++) {
            charArray[(int)(tString.charAt(i)) - 97] -= 1;
        }
        for (int j : charArray) {
            if (j != 0) {
                return false;
            }

        }
        return true;
    }
}
```


1. **Character Counting:** It uses an array of size 26 to count the frequency of each character in both strings, adjusting the count for each character in the first string and then decrementing it for each character in the second string.

2. **Anagram Check:** After processing both strings, it checks if all values in the array are zero, indicating that both strings have the same character frequencies.

3. **Helper Method:** The `validAnagrams` method is called to encapsulate the logic of checking if two strings are anagrams, and `isAnagram` calls it directly.
