
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (szuletett_fovaros)

> Kérjük be a felhasználó születési helyét, 
> majd döntsük el, 
> hogy vidéken vagy a fővárosban született! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	String city;

	System.out.print("Kérlek add meg melyik városban születtél (Magyarország): ");
	try {
		city = br.readLine();

		switch(city) {
			case "budapest":
				System.out.println("Te a fővárosban születtél.");
			break;
			case "Budapest":
				System.out.println("Te a fővárosban születtél.");
			break;
			case "BudaPest":
				System.out.println("Te a fővárosban születtél.");
			break;
			default:
				System.out.println("Te egy vidéki városban születtél.");
			break;
		}

		br.close();
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
