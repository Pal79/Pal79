
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (sipalya)

> A sípályák nehézség szerint osztályozva vannak mindenhol.
> A könnyű pályákat kék színnel jelzik.
> Ezeken a pályákon maximum 12 fokos lejtők találhatók. 
>
> A középnehéz pályák piros színűek, és maximum 20 fokos lejtők találhatók rajtuk. 
>
> Ennél meredekebb lejtővel rendelkező pályák fekete színűek. 
>
> Írj programot, amely beolvassa, hogy egy sípálya legmeredekebb lejtője hány fokos, 
> és az alapján megadja a sípálya színét! 
> Ügyelj arra, hogy negatív lejtésszög nem lehet! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Add meg a lejtő meredekségét: ");
		Double angle = Double.parseDouble(br.readLine());

		if(angle < 0) {
			System.out.println("Ilyen dőlésszögű pálya nem létezik.");
		} else if(angle <= 12) {
			System.out.println("Ez egy kék színű (könnyű) pálya.");
		} else if(angle <= 20) {
			System.out.println("Ez egy piros színű (középnehéz) pálya.");
		} else {
			System.out.println("Ez egy fekete színű (nehéz) pálya.");
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
