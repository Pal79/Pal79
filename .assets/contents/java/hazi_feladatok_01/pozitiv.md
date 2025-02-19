
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (pozitiv)

> Kérjünk be 5 darab egész számot a felhasználótól, 
> mindegyikről döntsük el, 
> hogy negatív vagy pozitív, esetleg nulla! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	int num1, num2, num3, num4, num5;

	// (x >= 0) ? x : -x;
	try {
		System.out.println("Add meg a számokat.");
		System.out.print("1. szám: ");
		num1 = Integer.parseInt(br.readLine());
		PositiveOrNegativeMaybeZero(num1);
		System.out.print("2. szám: ");
		num2 = Integer.parseInt(br.readLine());
		PositiveOrNegativeMaybeZero(num2);
		System.out.print("3. szám: ");
		num3 = Integer.parseInt(br.readLine());
		PositiveOrNegativeMaybeZero(num3);
		System.out.print("4. szám: ");
		num4 = Integer.parseInt(br.readLine());
		PositiveOrNegativeMaybeZero(num4);
		System.out.print("5. szám: ");
		num5 = Integer.parseInt(br.readLine());
		PositiveOrNegativeMaybeZero(num5);

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> Pozitív, negatív és nulla vizsgálata:

```java
public static void PositiveOrNegativeMaybeZero(int num) {
	if(num == 0) {
		System.out.println("Az adott szám \" " + num + "\" nulla.");
	} else if(num < 0) {
		System.out.println("Az adott szám \"" + num + "\" negatív szám.");
	} else {
		System.out.println("Az adott szám \"" + num + "\" pozitív szám.");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
