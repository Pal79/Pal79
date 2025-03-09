
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

>  Mozi: Készítsünk alkalmazást, amely egy vidéki mozi nézőterének foglaltságát, jegyeladásait
> szimulálja. A terem 40 sorának mindegyikében 30 szék található. Töltsünk fel egy megfelelő
> méretű mátrixot véletlenszerűen 0-val (üres), 1-el (foglalt – felnőtt jegy) vagy 2-es (foglalt –
> gyerek, nyugdíjas jegy) értékekkel. A jegyárakat két kategóriába sorolják: felnőtt jegy 1600 Ft,
> gyerek, nyugdíjas jegy 1200 Ft. A sorok számozása fentről, a székek számozása pedig baloldalról
> indul.
>
> - a. Írjuk ki a mátrix elemeit! Jelenítsük meg a sorok: 1-40 és a székek: 1-30 számát is (csak fejlécként 1X szerepeljen)!
> - b. Eddig hány forintért értékesítettek jegyeket?
> - c. Hány jegyet nem adtak még el?
> - d. Az értékesített jegyek hány százaléka gyerek-nyugdíjas, felnőtt jegy?
> - e. Kérjünk be egy sorszámot és székszámot a felhasználótól, majd ellenőrizzük, hogy foglalt – e az adott hely! Amennyiben üres volt, hajtsuk végre a foglalást, amelyhez kérjük be a jegy kategóriáját is (1 es vagy 2-es)!
> - f. A 8-as sorban melyik helyek üresek még? Írjuk ki a székek sorszámát egymás mellé szóközzel elválasztva!
> - g. Hány üres hely maradt a nézőtér első kettő és utolsó kettő sorában?
> - h. Melyik sorokban adtak el több felnőttjegyet, mint gyerek, nyugdíjas jegyet (egymás mellé szóközzel elválasztva írjuk ki a sorszámokat)?
> - i. A nézőtér első vagy második 20 sorában eladott jegyekből jön a több bevétel? A válaszban jelenítsük meg a számított értékeket is!
> - j. Készíts statisztikát: soronként hány százalékát adták el a jegyeknek és abból hány százalék volt felnőtt illetve gyerek, nyugdíjas jegy? (emelt)
> - k. Melyik sorban van 3 egymás melletti üres hely? (emelt)

> Main:

```java
public static void main(String[] args) {

		int[][] places = arrUpload();
}
```

> tömbfeltöltés:

```java
private static int[][] arrUpload() {

	Random r = new Random();

	int[][] places = new int[40][30];

	for(int i = 0; i < places.length; i++) {
		for(int j = 0; j < places[i].length; j++) {
			places[i][j] = r.nextInt(1 - 0 + 1) + 0;
		}
	}
	return places;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---