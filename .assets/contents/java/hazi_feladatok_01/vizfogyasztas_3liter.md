
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (vizfogyasztas_3liter)

> Kérjük be a felhasználótól a napi vízfogyasztását! 
> Döntsük el, hogy elég vizet ivott –e 
> (ajánlott bevitel min. 3 liter)! 

> Main:

```java
public static void main(String[] args) {

	Scanner input = new Scanner(System.in);

	System.out.print("Írd be, hogy hány liter vizet fogyasztasz naponta: ");
	Double water = input.nextDouble();

	if(water >= 3.0) {
		System.out.println("Az ön vízfogyasztása megfelelő.");
	} else if(water < 3.0) {
		System.out.println("Az ön vízfogyasztása kevés.");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
