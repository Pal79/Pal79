
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# tomb_intervallum_kiir

---

> Készíts metódust, amely két egész szám közötti intervallumon belül kiírja 
> a 3-mal és 7-tel is maradék nélkül osztható számokat! 
> A két bemenő paramétert a felhasználótól érkező adatokkal adjuk meg.
>
> (tomb_intervallum_kiir)

> Main:

```java
public static void main(String[] args) {

    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Add meg az első számot: ");
		int num1 = Integer.parseInt(br.readLine());
		System.out.print("Add meg a második számot: ");
		int num2 = Integer.parseInt(br.readLine());

		System.out.print("A két megadott szám közötti 3-al és 7-el osztható számok: ");
		twoIntervallBetweenTwoNumbers(num1, num2);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nA megadott szám csak egész szám lehet.");
	}
}
```

> két szám közötti intervallum kiírás:

```java
private static void twoIntervallBetweenTwoNumbers(int num1, int num2) {
	for(int i = num1; i < num2; i++) {
		if(i % 7 == 0 && i % 3 == 0) {
			System.out.print(i + " ");
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---