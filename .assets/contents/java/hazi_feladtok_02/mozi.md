
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

    arrWriteOut(places);
	System.out.println();
    income(places);
	System.out.println();
	howManyTicketsCantSoldOut(places);
	System.out.println();
	whatPercentageOfTicketsSoldChildRetiredAdult(places);
	System.out.println();
	isTheSeatTaken(places);
	System.out.println();
}
```

> helyfoglalás, ha foglalt, akkor nem:

```java
// e. Kérjünk be egy sorszámot és székszámot a felhasználótól, majd ellenőrizzük, hogy foglalt –
//    e az adott hely! Amennyiben üres volt, hajtsuk végre a foglalást, amelyhez kérjük be a jegy
//    kategóriáját is (1 es vagy 2-es)!
private static void isTheSeatTaken(int[][] arr) {
	System.out.println("e. feladat:");

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Adjon meg egy sorszámot és egy székszámot:");
	try {
		System.out.print(" - sorszám (1-40): ");
		int row = Integer.parseInt(br.readLine());
		System.out.print(" - székszám (1-30): ");
		int seat = Integer.parseInt(br.readLine());

		boolean is_taken = true;

		if(arr[row-1][seat-1] == 0) {
			is_taken = false;
		}

		if(is_taken) {
			System.out.println("A hely már foglalt.");
		} else {
			System.out.println("A hely jelenleg nem foglalt.");
			System.out.println("Ha szeretné lefoglalni, akkor kérem válasszon:");
			System.out.println("Milyen típusú jegyet szeretne?");
			System.out.println(" - Diák vagy nyugdíjas jegyet szeretne? Nyomja meg az 1-es gombot");
			System.out.println(" - Felnőtt jegyet szeretne? Nyomja meg a 2-es gombot");
			System.out.println(" - Esetleg mégsem foglalna? Nyomja meg a 0-ás gombot.");
			int ticket_type = Integer.parseInt(br.readLine());

			if(ticket_type == 1) {
				arr[row-1][seat-1] = ticket_type;
				System.out.println("A " + row + ". sorban a " + seat + ". szék lefoglalva.");
			} else if(ticket_type == 2) {
				arr[row-1][seat-1] = ticket_type;
				System.out.println("A " + row + ". sorban a " + seat + ". szék lefoglalva.");
			} else {
				System.out.println("A jegy vásárlás törölve.");
			}
			/*
			for(int i = 0; i < 31; i++) {
				if(i == 0) {
					System.out.print("\t");
				} else {
					System.out.print(i + ".\t");
				}
			}
			System.out.println("\n");

			for(int i = 0; i < arr.length; i++) {
				System.out.print((i+1) + ".\t");
				for(int j = 0; j < arr[i].length; j++) {
					System.out.print(arr[i][j] + "\t");
				}
				System.out.println();
			}
			*/
		}
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nCsak egész számok adhatóak meg a megadott intervallumokban.");
	}
}
```

> az értékesített jegyek hány százaléka gyerek/felnőt vagy felnőtt:

```java
// d. Az értékesített jegyek hány százaléka gyerek-nyugdíjas, felnőtt jegy?
private static void whatPercentageOfTicketsSoldChildRetiredAdult(int[][] arr) {
	System.out.println("d.feladat:");

	int child_retired_count = 0;
	int adult_count = 0;
	int all_count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				child_retired_count++;
			} else if(arr[i][j] == 2) {
				adult_count++;
			}
			all_count++;
		}
	}

	double child_retired_percent = (double)child_retired_count / (double)all_count * 100;
	double adult_percent = (double)adult_count / (double)all_count * 100;

	System.out.println("Az értékesített jegyek " + child_retired_percent + "%-a gyerek/nyugdíjas.");
	System.out.println("Az értékesített jegyek " + adult_percent + "%-a felnőtt.");
}
```

> hány jegy nem lett értékesítve:

```java
// c. Hány jegyet nem adtak még el?
private static void howManyTicketsCantSoldOut(int[][] arr) {
	System.out.println("c.feladat:");

	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 0) {
				count++;
			}
		}
	}
	System.out.println(count + " darab jegyet nem sikerült értékesíteni.");
}
```

> eddigi bevételek:

```java
// b. Eddig hány forintért értékesítettek jegyeket?
private static void income(int[][] arr) {
	System.out.println("b. feladat:");

	int child_and_retired_tickets_count = 0; // 1200
	int adult_tickets_count = 0; // 1600

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				child_and_retired_tickets_count++;
			} else if(arr[i][j] == 2) {
				adult_tickets_count++;
		}
		}
	}

	int child_and_retired_tickets_value = child_and_retired_tickets_count * 1200;
	int adult_tickets_value = adult_tickets_count * 1600;

	System.out.println("Az eddig eladott jegyek összege:");
	System.out.println(" - Gyerek / nyugdíjas jegyek: " + child_and_retired_tickets_value + " forint");
	System.out.println(" - Felnőtt jegyek: " + adult_tickets_value + " forint");
	System.out.println(" - Összesen: " + (child_and_retired_tickets_value + adult_tickets_value) + " forint.");
}
```

> tömbkiírás:

```java
// a. Írjuk ki a mátrix elemeit! Jelenítsük meg a sorok: 1-40 és a székek: 1-30 számát is 
//    (csak fejlécként 1X szerepeljen)!
private static void arrWriteOut(int[][] arr) {
	System.out.println("a. feladat:");
	for(int i = 0; i < 31; i++) {
		if(i == 0) {
			System.out.print("\t");
		} else {
			System.out.print(i + ".\t");
		}
	}
	System.out.println("\n");
	for(int i = 0; i < arr.length; i++) {
		System.out.print((i+1) + ".\t");
		for(int j = 0; j < arr[i].length; j++) {
			System.out.print(arr[i][j] + "\t");
		}
		System.out.println();
	}
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