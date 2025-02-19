
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (paros_hat)

> Kérj be a felhasználótól 6 egész számot, 
> majd írd ki mellé, hogy páros vagy páratlan a megadott szám! 

> Main:

```java
public static void main(String[] args) {

	Scanner input = new Scanner(System.in);
	Integer num_1, num_2, num_3, num_4, num_5, num_6;

	System.out.println("Írj be hat számot.");
	System.out.print("1. szám: ");
	num_1 = input.nextInt();
	IsEven(num_1);
	System.out.print("2. szám: ");
	num_2 = input.nextInt();
	IsEven(num_2);
	System.out.print("3. szám: ");
	num_3 = input.nextInt();
	IsEven(num_3);
	System.out.print("4. szám: ");
	num_4 = input.nextInt();
	IsEven(num_4);
	System.out.print("5. szám: ");
	num_5 = input.nextInt();
	IsEven(num_5);
	System.out.print("6. szám: ");
	num_6 = input.nextInt();
	IsEven(num_6);
		
}
```

> IsEven:

```java
public static void IsEven(Integer num) {
	Integer search = num;
	if(search % 2 == 0) {
		System.out.println("Az adot szám " + search + " páros.");
	} else {
		System.out.println("Az adot szám " + search + " páratlan.");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
