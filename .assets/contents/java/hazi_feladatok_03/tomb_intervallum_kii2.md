
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# tomb_intervallum_kiir2

---

> Előző feladatot egészítsd ki: 
> a 3 és 7 helyett legyen megadható ez a két paraméter is, 
> tetszőleges egész szám!
>
> (tomb_intervallum_kiir2)

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Add meg az első számot: ");
		int num1 = Integer.parseInt(br.readLine());
		System.out.print("Add meg a második számot: ");
		int num2 = Integer.parseInt(br.readLine());

		System.out.println("Adj meg két osztót:");
		System.out.print("1. osztó: ");
		int division1 = Integer.parseInt(br.readLine());
		System.out.print("2. osztó: ");
		int division2 = Integer.parseInt(br.readLine());

		System.out.print("A " + division1 + " és " + division2 + " osztható számok " + num1 + " és " + num2 + " között: ");
		twoIntervallBetweenTwoNumbers(num1, num2, division1, division2);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nA megadott szám csak egész szám lehet.");
	}
}
```

> két szám közötti intervallum kiírás:

```java
private static void twoIntervallBetweenTwoNumbers(int num1, int num2, int division1, int division2) {
	for(int i = num1; i < num2; i++) {
		if(i % division1 == 0 && i % division2 == 0) {
			System.out.print(i + " ");
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
