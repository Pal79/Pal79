
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (szokoEv)

> Adott évről döntsük el, hogy szökőév-e! 
>
> (Szökőévek a következők: 
> minden néggyel osztható év, 
> kivéve a százzal is oszthatókat. 
> Szökőévek viszont a 400-zal osztható évek. 
> Vagyis a százasra végződő évek közül csak azok szökőévek, 
> amelyek 400-zal is oszthatók.)
>
> Ez alapján tehát szökőév: 
> 1988, 1992, 1996, 2000, 2004, 2008, 2012, 2016, 2020 és 2024. 
>
> Nem szökőév 
> 1700, 1800, 1900, 2100, 2200 és 2300. 
>
> Viszont szökőévek a következő esztendők: 1600, 2000 és 2400 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	String is_leap = "Szökőév";
	String is_not_leap = "nem szökőév";

	try {
		System.out.print("Írj be egy évszámot: ");
		Integer year = Integer.parseInt(br.readLine());

		if(year % 4 == 0) {
			if(year % 100 == 0) {
				if(year % 400 == 0) {
					System.out.println(is_leap);
				} else {
					System.out.println(is_not_leap);
				}
			} else {
				System.out.println(is_not_leap);
			}
		} else {
			System.out.println(is_not_leap);
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
