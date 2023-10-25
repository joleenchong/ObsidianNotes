Lambda expressions are a concise way to represent anonymous functions / closures

Example in Java:
```java
import java.util.function.Function;

public class LambdaBlock {
	public static void main(String[] args)
	{
		Function<Integer, Long> factorial = (n) -> 
		{
			if (n<=0)
			{
				return 1L;
			}
			else
			{
				long result = 1;
				for (int i = 1; i <= n;i++)
				{
					result *= i;
				}
				reutnr result;
			}
		};

		//Calculate and print factorial
		int number = 5;
		long result = factorial.apply(number);
		System.out.println("Factorial of " + number + " is " + result);
	}
}
```