
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (evszakok)

> Készíts programot, 
> mely a hónap sorszáma alapján megadja, 
> melyik évszakba tartozik! 
> Használj switch-case szerkezetet! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  	try {
		System.out.print("Írd be egy hónap sorszámát és megtudod, melyik évszakba tartozik (1-12): ");
		Integer month = Integer.parseInt(br.readLine());
			
		switch(month) {
			case 1:
			case 2:
			case 12:
				System.out.println("Tél");
			break;
			case 3:
			case 4:
			case 5:
				System.out.println("Tavasz");
			break;
			case 6:
			case 7:
			case 8:
				System.out.println("Nyár");
			break;
			case 9:
			case 10:
			case 11:
				System.out.println("Ősz");
			break;
			default:
				System.out.println("Hibás adatbevitel!");
			break;
		}
		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
