
---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---

Fibonacci.java

```java
public class Fibonacci {
	
	private int fibonacci(int num) {
		// basic situation
		if (num <= 1) {
			return num;
		}
		// recursive call
		return fibonacci(num - 1) + fibonacci(num - 2);
	}
	
	public void fibonacciWriteConsole() {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		System.out.print("Enter a whole number (how long do you write it out): ");
		try {
			Integer number = Integer.parseInt(br.readLine());
			
			if(number <= 0) {
				System.out.println("The specified number cannot be zero or minus.");
			} else {
				for(int i = 0; i < number; i++) {
						System.out.print(fibonacci(i) + " ");
				}
			}
			
			br.close();
		} catch (NumberFormatException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}

}
```

Main.java

```java
public class Main {

	private static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	public static void main(String[] args) {
		
		Fibonacci fibo = new Fibonacci();
		
		fibo.fibonacciWriteConsole();
	}

}
```

---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---