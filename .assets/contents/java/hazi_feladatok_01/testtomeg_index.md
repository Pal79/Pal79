
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (testtomeg_index)

> Kérjük be a felhasználó tömegét kg-ban és magasságát cm-ben, 
> majd számítsuk ki és írjuk a képernyőre a felhasználó testtömeg-indexét 
> a következő képlet alapján:
>
> TTI = tömeg / magassag2
>
> Figyelj rá, hogy a képletben a magasság méterben megadott értékével kell számolni! 
> A testtömeg-index és táblázat alapján írd ki, 
> a testsúly-osztályzást! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Kérem adja meg a testtömegét (kg): ");
		Double weight = Double.parseDouble(br.readLine());
		System.out.print("Kérem adja meg a magasságát (cm): ");
		Double height = Double.parseDouble(br.readLine());

		// body mass index
		Double bmi = weight / Math.pow((height/100),2);

		System.out.println(bmi);

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
