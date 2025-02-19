
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (posta)

> A postai küldeményeket súlyuk alapján árazzák 
> (2 kg-ig 475 Ft, 20 kg-ig 3395 Ft, 40 kg-ig 6415 Ft).
>
> Készíts alkalmazást, ami bekéri a küldemény súlyát, 
> majd kiírja a fizetendő összeget! 40 kg felett írja ki, 
> hogy nem vállal a posta súlyos küldemény kézbesítését! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

  try {
		System.out.print("Kérlek add meg a csomagod súlyát (kg): ");
		Double weight = Double.parseDouble(br.readLine());

		if(weight <= 2) {
			System.out.println("Fizetendő összeg: 475 Ft.");
		} else if(weight <= 20) {
			System.out.println("Fizetendő összeg: 3395 Ft.");
		} else if(weight <= 40) {
			System.out.println("Fizetendő összeg: 6415 Ft.");
		} else {
			System.out.println("A posta nem vállal súlyos küldemény kézbesítést!");
		}

		br.close();
  } catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
