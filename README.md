Valid Parentheses
Problem Statement

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

A string is valid if:

Open brackets are closed by the same type of brackets.
Open brackets are closed in the correct order.
Every closing bracket has a corresponding opening bracket.

LeetCode Problem:
https://leetcode.com/problems/valid-parentheses/

Approach
Using Stack
Traverse each character in the string.
If the character is an opening bracket ((, {, [), push it onto the stack.
If it is a closing bracket:
Check if the stack is empty. If yes, return false.
Pop the top element from the stack.
Verify that the popped opening bracket matches the current closing bracket.
If it does not match, return false.
After processing all characters:
If the stack is empty, return true.
Otherwise, return false.
Algorithm
Create an empty stack.
Iterate through each character in the string.
Push opening brackets onto the stack.
For closing brackets:
If stack is empty → return false.
Pop the top bracket.
Check whether it forms a valid pair.
After traversal:
If stack is empty → return true.
Else → return false.
Complexity Analysis
Time Complexity: O(n)
Each character is pushed and popped at most once.
Space Complexity: O(n)
In the worst case, all opening brackets are stored in the stack.
Java Solution
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
Example
Input
s = "()[]{}"
Output
true
Input
s = "(]"
Output
false
Key Concepts Learned
Stack Data Structure
Push and Pop Operations
Bracket Matching
String Traversal
Conditional Validation Logic
Author

Ajay Chintala
