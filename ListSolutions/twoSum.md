```java
class Solution {
    public int[] twoSum(int[] arr, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < arr.length; i++) {
            int complement = target - arr[i];
            if (hashMap.containsKey(complement)){
                return new int[] {hashMap.get(complement), i};
            }
            else{
                hashMap.put(arr[i], i);
            }
        }
        return new int[] {-1, -1};
    }
      
}
```

1. Use HashMaps to update continously instead of adding all the values at once
2. Return index instead of Values
3. Add arr[i], i if not found else return i of complement, and current i
