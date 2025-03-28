
---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---

# Négyzetszámok

---

> ## Manuális keresés:
>
> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	boolean is_on = true;

	try {
		while (is_on) {
			System.out.println("Válassz az alábbi lehetőségek közül: ");
			System.out.println(" - Számok megadása (1): ");
			System.out.println(" - Kilépés (0): ");
			int choose = Integer.parseInt(br.readLine());

			if(choose == 0) {
				is_on = false;
				System.out.println("A program kilépett!");
			} else {
				System.out.print("Add meg az első számot: ");
				int num1 = Integer.parseInt(br.readLine());
				System.out.print("Add meg a második számot: ");
				int num2 = Integer.parseInt(br.readLine());

				OperationDisplay(num1, num2);
				System.out.print("tehát a kapott eredméy: ");
				if(IsDoubleOrIsInteger(num1, num2) == true) {
					System.out.println("négyzetszám.");
				} else {
					System.out.println("nem négyzetszám.");
				}
				is_on = true;
			}
			System.out.println();
		}
		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}		
}
```

> megtalált számok kiírása:

```java
private static void OperationDisplay(double num1, double num2) {
	double addition = Math.pow(num1, 2) + Math.pow(num2, 2);
	double result = Math.sqrt(Math.pow(num1, 2) + Math.pow(num2, 2));

	System.out.println(Math.pow(num1, 2) + " + " + Math.pow(num2, 2) + " = " + addition);
	System.out.println("Az eredmény gyök alatt: " + result);
}
```

> számok ellenőrzése:

```java
private static boolean IsDoubleOrIsInteger(double num1, double num2) {
	double result = Math.sqrt((Math.pow(num1, 2) + Math.pow(num2, 2)));

	if(result % 1 == 0) {
		return true;
	} else {
		return false;
	}
}
```

> ## négyzetszámok keresése, megadott intervallumok között
>
> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Kérlek add meg az intervallumot.");
	try {
		System.out.print(" - intervallum kezdete: ");
		int start = Integer.parseInt(br.readLine());
		System.out.print(" - vége: ");
		int end = Integer.parseInt(br.readLine());

		System.out.println();
		System.out.println("Négyzetszámok " + start + " és " + end + " között:");
		System.out.println();

		FindNumbers(start, end);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> számok keresése:

```java
private static void FindNumbers(int min, int max) {

	int count = 2;
	for(int i = min; i < max; i++) {
		for(int j = count; j < max+1; j++) {
			if(IsDoubleOrIsInteger(i, j)) {
				System.out.println("--------------------");
				System.out.println(i + " ; " + j);
				double num1 = i;
				double num2 = j;
				OperationDisplay(num1, num2);
				System.out.println("--------------------");
			}
		}
		count = 2;
	}
}
```

> megtalált számok kiírása:

```java
private static void OperationDisplay(double num1, double num2) {
	double addition = Math.pow(num1, 2) + Math.pow(num2, 2);
	double result = Math.sqrt(Math.pow(num1, 2) + Math.pow(num2, 2));

	System.out.println(Math.pow(num1, 2) + " + " + Math.pow(num2, 2) + " = " + addition);
	System.out.println("Az eredmény gyök alatt: " + result);
}
```

> számok ellenőrzése:

```java
private static boolean IsDoubleOrIsInteger(double num1, double num2) {
	double result = Math.sqrt((Math.pow(num1, 2) + Math.pow(num2, 2)));

	if(result % 1 == 0) {
		return true;
	} else {
		return false;
	}
}
```

---

- [Back to Java](../java.md)
- [Back to main](../../../README.md)

---