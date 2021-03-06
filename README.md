# Happy Number
## https://leetcode.com/problems/happy-number

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers. Write an algorithm to determine if a number is "happy".

```
Example: 

Input: 19
Output: true
Explanation: 
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

### Implementation

```java
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> set = new HashSet<Integer>();
        boolean isHappy = false;
        while(!isHappy) {
            int sum = sumOfSquares(n);
            if(sum == 1){
                isHappy = true;
                break;
            }
            if(set.contains(n)) 
                break;
            set.add(n);
            n = sum;
        }
        return isHappy;
    }
    
    private int sumOfSquares(int n) {
        int sum = 0;
        while(n > 0) {
            int digit = n % 10;
            int square = digit * digit;
            sum += square;
            n = n / 10;
        }
        return sum;
    }
}

```
