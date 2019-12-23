# Happy Number

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
import java.util.HashSet;
import java.util.Set;

public class App {
	public static void main(String[] args) {
		System.out.println(isHappyNumber(19));
	}

	private static boolean isHappyNumber(int number) {
		Set<Integer> set = new HashSet<Integer>();
		int sum = 0;
		while(sum != 1) {
			sum = getSum(number);
			number = sum;
			if(set.contains(number)) {
				return false;
			}
			set.add(number);
		}

		return true;
	}

	private static int getSum(int n) {
		int sum = 0;
		while (n > 0) {
			sum += (n % 10) * (n % 10);
			n = n / 10;
		}
		return sum;
	}
}

```
