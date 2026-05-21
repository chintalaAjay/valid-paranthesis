# Valid Parentheses

## Problem Link
https://leetcode.com/problems/valid-parentheses/

## Description
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

A string is valid if:
- Open brackets are closed by the same type of brackets.
- Open brackets are closed in the correct order.
- Every closing bracket has a corresponding opening bracket.

---

## Approach

I used a **Stack** to keep track of opening brackets.

- Traverse each character in the string.
- If the character is an opening bracket (`(`, `{`, `[`), push it into the stack.
- If it is a closing bracket:
  - Check whether the stack is empty.
  - Pop the top element from the stack.
  - Verify that the popped opening bracket matches the current closing bracket.
- If any mismatch occurs, return `false`.
- After processing all characters, the stack should be empty for the string to be valid.

---

## Algorithm

1. Create an empty stack.
2. Iterate through each character of the string.
3. Push opening brackets into the stack.
4. For closing brackets:
   - If the stack is empty, return `false`.
   - Pop the top element.
   - Check if it matches the current closing bracket.
5. After traversal, return `true` if the stack is empty; otherwise return `false`.

---

## Complexity Analysis

- **Time Complexity:** O(n)
- **Space Complexity:** O(n)

where `n` is the length of the string.

---

## Java Solution

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char x : s.toCharArray()) {
            if (x == '(' || x == '{' || x == '[') {
                stack.push(x);
            } else {
                if (stack.isEmpty()) return false;

                char pop = stack.pop();

                if ((pop == '(' && x != ')') ||
                    (pop == '{' && x != '}') ||
                    (pop == '[' && x != ']')) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
```

---

## Example

### Input
```
()[]{}
```

### Output
```
true
```

### Input
```
(]
```

### Output
```
false
```

---

## Concepts Used

- Stack
- Character Traversal
- Conditional Statements
- Parentheses Matching

---

## Author

Ajay Chintala

GitHub: https://github.com/chintalaAjay
