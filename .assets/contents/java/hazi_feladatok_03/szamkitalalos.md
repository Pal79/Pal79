
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# szamkitalalos

> Készíts számkitalálós programot! 
> A gép hozzon létre egy véletlen számot, majd a felhasználó tippel. 
> A gép csak annyit közöl, hogy kisebb-nagyobb vagy eltaláltad! 
> Továbbfejleszthető pénzegységekkel 
> (minden tipp X költség, helyes tipp Y bevétel). 
>
> (szamkitalalos)

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	Random r = new Random();

	boolean is_on = true;

	System.out.println("Üdvözöllek a számkitalálós játékban.");
	System.out.println("A számok 0-tól addig a számig lesznek amit beállítasz.");
	System.out.print("0-tól meddig szeretnél játszani? ");
	try {
		int up_to = Integer.parseInt(br.readLine());
		int num = r.nextInt(up_to - 0 + 1) + 0;

		//System.out.println(num);

		while(is_on) {

			System.out.print("Adj meg egy egész számot: ");
			int tipp = Integer.parseInt(br.readLine());

			if(tipp < num) {
				System.out.println("A megadott szám kisebb, mint a kitalálandó szám.");
			} else if(tipp > num) {
				System.out.println("A megadott szám nagyobb. mint a kitalálandó szám.");
			} else {
				System.out.println("Nyertél!");
				is_on = false;
			}
		}
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

---

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---