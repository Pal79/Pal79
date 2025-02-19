
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (telepules)

> Írj programot, amely bekér a felhasználótól egy helységnevet, 
> valamint ennek a helységnek a lélekszámát, 
> és a megadott lélekszámtól függően kiírja, 
> hogy az adott helység milyen településtípusba tartozik. 
>
>
> - ha a lélekszám kevesebb, mint 5000, akkor község
> - ha a lélekszám legalább 5000, de kevesebb, mint 20 000, akkor kisváros
> - ha a lélekszám legalább 20 000, de kevesebb, mint 100 000, akkor középváros
> - ha a lélekszám legalább 100 000, de kevesebb, mint 1 000 000, akkor nagyváros
> - ha a lélekszám legalább 1 000 000, akkor metropolis
> - ha a felhasználó 0 vagy annál kisebb számot ad meg, a program írja ki, hogy "Hibás adatbevitel"!

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Add meg település nevet: ");
		String telepules = br.readLine();
		System.out.print("Add meg a település létszámát: ");
		Integer lelekszam = Integer.parseInt(br.readLine());

		if(lelekszam <= 0) {
			System.out.println("Hibás adatbevitel!");
		} else if(lelekszam < 5000) {
			System.out.println("A megadott település " + telepules + ", lélekszáma alapján község.");
		} else if(lelekszam == 5000 || lelekszam < 20000) {
			System.out.println("A megadott település " + telepules + ", lélekszáma alapján kisváros.");
		} else if(lelekszam == 20000 || lelekszam < 100000) {
			System.out.println("A megadott település " + telepules + ", lélekszáma alapján középváros.");
		} else if(lelekszam == 100000 || lelekszam < 1000000) {
			System.out.println("A megadott település " + telepules + ", lélekszáma alapján nagyváros.");
		} else {
			System.out.println("A megadott település " + telepules + ", lélekszáma alapján metropolis.");
		}

	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
