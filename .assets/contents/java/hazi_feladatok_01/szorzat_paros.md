
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (szorzat_paros)

> Kérj be 2 számot, majd döntsd el, 
> hogy szorzatuk páros vagy páratlan! 

> Main:

```java
public static void main(String[] args) {

	Scanner input = new Scanner(System.in);
	Integer num_1, num_2, result;

	System.out.println("Írj be két egész számot és megtudod, hogy szorzatuk páros e.");
	System.out.print("1. szám: ");
	num_1 = input.nextInt();
	System.out.print("2. szám: ");
	num_2 = input.nextInt();

	result = num_1 * num_2;

	if(result % 2 == 0) {
		System.out.println("A két szám szorzata "  + result + " páros.");
	} else {
		System.out.println("A két szám szorzata " + result + " nem páros.");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
