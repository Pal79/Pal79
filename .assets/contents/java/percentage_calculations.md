
---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---

> Calculate a percentage of a number:

```java
public static void main(String[] args) {
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.println("Egy szám százalékának kiszámítása:");

		System.out.print("Szám: ");
		double num = Double.parseDouble(br.readLine());

		System.out.println("Százalékláb:");
		double percentage_foot = Double.parseDouble(br.readLine());

		double result = num * percentage_foot / 100;

		System.out.println("A " + num + " " + percentage_foot + "%-a:  " + result);

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> What is the percentage difference between two numbers:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Mekkora a százalékos különbség két szám között?");
	try {
		System.out.print("1. szám: ");
		double num1 = Double.parseDouble(br.readLine());
		System.out.print("2. szám: ");
		double num2 = Double.parseDouble(br.readLine());

		double result = (num2 - num1) / ((num1 + num2) / 2) * 100;

		System.out.println("A két szám közötti százalékos különbség: " + result);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> What is the percentage increase or decrease between two numbers:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Mekkora a százalékos növekedés vagy csökkenés két szám között?");

	try {
		System.out.print("1. szám: ");
		double num1 = Double.parseDouble(br.readLine());
		System.out.print("2. szám: ");
		double num2 = Double.parseDouble(br.readLine());

		double result = (num2 - num1) / num1 * 100;

		System.out.println("A százalékos növekedés vagy csökkenés a két szám között: " + result);

	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> What percentage of a given number is of another number:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Egy adott szám hány százaléka egy másik számnak?");

	try {
		System.out.print("1. szám: ");
		double num1 = Double.parseDouble(br.readLine());
		System.out.print("2. szám: ");
		double num2 = Double.parseDouble(br.readLine());

		double result = num1 / num2 * 100;

		System.out.println("A(z) " + num1 + " " + result + "%-a " + num2 + "-nak/nek");

	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---