# **Leetcode 682: Baseball Game (Detailed Explanation)**

https://leetcode.com/problems/baseball-game/description/

### **Problem Statement:**  
You are given a list of strings `operations`, where each string is an operation that represents a record in a baseball game. The game’s scoring rules are:  

1. **Integer (e.g., "5")**: Record this number as a new score.  
2. **"C" (Cancel):** Remove the most recent score from the record.  
3. **"D" (Double):** Record double the previous score.  
4. **"+" (Sum):** Record the sum of the previous two scores.  

Finally, return the sum of all scores after performing all operations.

---

### **Example:**  
**Input:** `operations = ["5","2","C","D","+"]`  
**Step-by-step:**  
- **"5"**: Add 5 → Stack: [5]  
- **"2"**: Add 2 → Stack: [5, 2]  
- **"C"**: Remove last score (2) → Stack: [5]  
- **"D"**: Double previous score (5*2=10) → Stack: [5, 10]  
- **"+"**: Add sum of last two (5+10=15) → Stack: [5, 10, 15]  

**Output:** `5 + 10 + 15 = 30`

---

### **Approach (Using Stack):**  
- **Initialize a stack:** Use a stack to store scores.  
- **Loop through operations:**  
  - If an integer, convert it to `int` and `push()` onto the stack.  
  - If `"C"`, `pop()` the last score.  
  - If `"D"`, push `2 * stack.peek()`.  
  - If `"+"`, push `stack[-1] + stack[-2]` (sum of last two).  
- **Calculate the sum:** Use `sum(stack)` at the end.

---

### **Complexity:**  
- **Time:** O(n) - Looping through operations and stack operations are O(1).  
- **Space:** O(n) - Stack can hold all scores.

### Using Stack

```java
class Solution {
    public int calPoints(String[] operations) {
        return getStackSum(operations);
    }
     public static int getStackSum(String[] operations){
        MyStackDSA stack = new MyStackDSA();


        for (String operation : operations) {
            switch (operation) {
                case "+" -> stack.add();
                case "D" -> stack.D();
                case "C" -> stack.C();
                case null, default -> stack.inputNumber(Integer.parseInt(operation));
            }

        }
        return stack.getSum();
    }
}

class MyStackDSA {
    Stack<Integer> stack;

    public MyStackDSA() {
        stack = new Stack<>();
    }

    public void inputNumber(int x) {
        stack.push(x);
    }

    public void add() {
        if (stack.size() < 2) {
            System.out.println("The size is less than 2");
        } else {
            int first = stack.pop();
            int second = stack.peek();
            int sum = first + second;
            stack.push(first);
            stack.push(sum);

        }
    }

    public void D() {
        if (!stack.isEmpty()) {
            stack.push(stack.peek() * 2);
        }
    }

    public void C() {
        if (!stack.isEmpty()) {
            stack.pop();
        }
    }

    public int getSum() {
        int sum = 0;
        while (!stack.isEmpty()) {
            sum += stack.pop();
        }
        return sum;
    }

    public void printStack() {
        System.out.println(stack);
    }
}
```

### Using ArrayList

```java
class Solution {
    public int calPoints(String[] operations) {
        return lc682(operations);
    }
    
    public static int lc682(String[] operations){
        ArrayList<Integer> list = new ArrayList<>();

        for (String operation : operations){
            if (operation.equals("+")){
                list.add(list.getLast() + list.get((list.size() - 2)));
            }
            else if (operation.equals("D")){
                list.add(list.getLast() * 2);
            }
            else if (operation.equals("C")){
                list.removeLast();
            }
            else{
                list.add(Integer.parseInt(operation));
            }

        }
        int sum = 0;
        for (int x : list){
            sum += x;
        }
        return sum;
    }
}

```


