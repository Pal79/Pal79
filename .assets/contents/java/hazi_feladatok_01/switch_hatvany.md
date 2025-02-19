
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (switch_hatvany)

> Switch-case szerkezettel készítsünk hatványozó alkalmazást! 
> Kérjünk be 2 pozitív egész számot:
> az első szám, amit hatványozni szeretnénk, 
> a második megadott szám pedig a menüpont, 
> amit leütve írja ki a 2. 3. vagy a 4. hatványát az első számnak! 
> Ha más értéket adok meg, írja ki, hogy hibás adat! 

> Main:

```java
public static void main(String[] args) {

	Integer hatvanyalap, hatvanykitevo;

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Kérlek adj meg egy számot: ");
		hatvanyalap = Integer.parseInt(br.readLine());
		System.out.print("Add meg a hatványát (2-4): ");
		hatvanykitevo = Integer.parseInt(br.readLine());

		switch(hatvanykitevo) {
			case 2:
				System.out.println((int)Math.pow(hatvanyalap, hatvanykitevo));
			break;
			case 3:
				System.out.println((int)Math.pow(hatvanyalap, hatvanykitevo));
			break;
			case 4:
				System.out.println((int)Math.pow(hatvanyalap, hatvanykitevo));
			break;
			default:
				System.out.println("Hibás adat!");
			break;
		}
		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		//e.printStackTrace();
		System.out.println("Hibás adat!");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
