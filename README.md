# Happy Number

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers. Write an algorithm to determine if a number is "happy".

```
Example: 

Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

### Implementation

```java
import java.util.HashSet;
import java.util.Set;

public class App {
	public static void main(String[] args) {
		System.out.println(isHappyNumber(1));
	}

	private static boolean isHappyNumber(int number) {
		Set<Integer> set = new HashSet<Integer>();
		while (!set.contains(number)) {
			set.add(number);
			number = getSum(number);
			if (number == 1) {
				return true;
			}
		}

		return false;
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
