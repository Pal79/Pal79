
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (atlag_harom)

> Kérj be 3 egész számot, majd írd ki az átlagukat!

> Main:

```java
public static void main(String[] args) {
		
	Scanner input = new Scanner(System.in);
	Integer a,b,c,result;
		
	System.out.println("Adj meg három számot, hogy megtudd az átlagukat:");
	System.out.print("1. szám: ");
	a = input.nextInt();
	System.out.println();
	System.out.print("2. szám: ");
	b = input.nextInt();
	System.out.println();
	System.out.print("3. szám: ");
	c = input.nextInt();
	System.out.println();
		
	result = (a+b+c)/3;
		
	System.out.println("A három szám átlaga: " + result);		
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
