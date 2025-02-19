
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (uzemanyag)

> Programunk kérje be egy autó fogyasztását (literben 100 km-en),
> a benzin literenkénti árát és a megteendő út hosszát,
> majd számítsa ki az útiköltséget!
> (pld. Autó fogyasztása: 5 liter / 100km, út hossza: 850 km, benzinár: 370 Ft / liter, útiköltség: 15.725 Ft)
>
> Utazási távolság (km) ÷ 100 = Egységnyi fogyasztás
> Egységnyi fogyasztás × Fogyasztás (liter/100 km) = Felhasznált üzemanyag mennyisége (liter)
> Felhasznált üzemanyag mennyisége (liter) × Üzemanyag ára (literenként) = Teljes üzemanyagköltség

> Main:

```java
public static void main(String[] args) {

	Double consumption, fuelPrice, roadDistance;
	Scanner input = new Scanner(System.in);

	System.out.print("Add meg az autó fogyasztását 100km-en: ");
	consumption = input.nextDouble();
	System.out.print("Add meg az üzemanyag literenkénti árát: ");
	fuelPrice = input.nextDouble();
	System.out.print("Add meg a megteendő út hosszát: ");
	roadDistance = input.nextDouble();

	Double individualConsumption = roadDistance / 100;
	Double amountOfFuelUsed = individualConsumption * consumption;
	Double totalFuelCost = amountOfFuelUsed * fuelPrice;

	System.out.println("Felhasznált üzemanyag: " + amountOfFuelUsed + "l");
	System.out.println("A teljes utiköltség: " + totalFuelCost + " Ft");
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
