
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (szinhaz_jegyek)

> A magyar kultúra napján 3 program közül választhatnak a diákok. 
> A színházi jegy ára 2500 Ft-ba kerül, 
> a komolyzenei koncert jegyének ára 2200 Ft, 
> a népzenei koncert jegyének ára pedig 2400 Ft. 
> Olvasd be, hogy az iskolából melyik programra hányan jelentkeznek, 
> és add meg, hogy összesen mennyibe fognak a jegyek kerülni! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	Integer theater_ticket, theater_ticket_price, classical_music_ticket, classical_music_ticket_price, folk_music_ticket, folk_music_ticket_price;

	try {
		System.out.println("Válasszon az alábbi jegyek közül: ");

		System.out.print("Színházi jegy (2500 Ft/db): ");
		theater_ticket = Integer.parseInt(br.readLine());
		System.out.print("Komolyzenei koncert jegy (2200 Ft/db): ");
		classical_music_ticket = Integer.parseInt(br.readLine());
		System.out.print("Klasszikus zenei koncert jegy (2400 Ft/db): ");
		folk_music_ticket = Integer.parseInt(br.readLine());

		theater_ticket_price = theater_ticket * 2500;
		classical_music_ticket_price = classical_music_ticket * 2200;
		folk_music_ticket_price = folk_music_ticket * 2400;

		System.out.println("Fizetendő összegek:");
		System.out.println(Events("Színházi", theater_ticket, theater_ticket_price));
		System.out.println(Events("Komolyzenei koncert", classical_music_ticket, classical_music_ticket_price));
		System.out.println(Events("Klasszikus zenei koncert", folk_music_ticket, folk_music_ticket_price));
		System.out.println(" - A jegyek összesen: " + (theater_ticket_price + classical_music_ticket_price + folk_music_ticket_price) + " Ft.");

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> Események (Events):

```java
public static String Events(String ticket_name, Integer piece, Integer price) {
	return " - " + ticket_name + " jegy(ek): " + piece + " db = " + price + " Ft.";
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
