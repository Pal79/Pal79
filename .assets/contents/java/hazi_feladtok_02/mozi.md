
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
	whichPlacesEmptyInEighthRow(places);
	System.out.println();
	System.out.println(howManyEmptySeatsInFirstAndTwiceRowAndBeforeLastAndLastRow(places));
	System.out.println();
	whichRowMoreAdultTicketsSoldOut(places);
	System.out.println();
	moreRevenueCameFromTheFirstOrSecondTwentyRowsOfTheAuditorium(places);
	System.out.println();
	howManyPercentSoldOutInRows(places);
	System.out.println();
	whichRowIsThreeEmptySeatsNextToEachOther(places);
	System.out.println();
}
```

> melyik sorban van 3 egymás melleti üres szék:

```java
// k. Melyik sorban van 3 egymás melletti üres hely? (emelt)
private static void whichRowIsThreeEmptySeatsNextToEachOther(int[][] arr) {
	System.out.println("k. feladat:");

	boolean find = true;

	System.out.println("Sorok száma, ahol legalább 3 egymás melletti üres szék van: ");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(find == true && j < 18 && arr[i][j] == 0 && arr[i][j+1] == 0 && arr[i][j+2] == 0) {
				System.out.print(i+1 + ". ");
				find = false;
			}
		}
		find = true;
	}
}
```

> soronként hány százalékát értékesítették a jegyeknek (összes, gyerek/nyugdíjas, felnőtt):

```java
// j. Készíts statisztikát: soronként hány százalékát adták el a jegyeknek és abból hány százalék
//    volt felnőtt illetve gyerek, nyugdíjas jegy? (emelt)
private static void howManyPercentSoldOutInRows(int[][] arr) {
	System.out.println("j. feladat:");

	for(int i = 0; i < arr.length; i++) {
		int retired_child_count = 0;
		int adult_count = 0;
		int result = 0;
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				retired_child_count++;
			} else if(arr[i][j] == 2) {
				adult_count++;
			}
		}
		System.out.println("Az eladott jegyek százalékosan a(z) " + (i+1) + ". sorban:");
		System.out.println(" - összes: " + (double)(retired_child_count + adult_count) / (double)30 *100 + "%");
		System.out.println(" - gyerek/nyugdíjas: " + (double)retired_child_count / (double)30 * 100 + "%");
		System.out.println(" - felnőtt: " + (double)adult_count / (double)30 * 100 + "%");
	}
}
```

> első vagy második húsz sor bevétele volt több:

```java
// i. A nézőtér első vagy második 20 sorában eladott jegyekből jön a több bevétel? A válaszban
//    jelenítsük meg a számított értékeket is!
private static void moreRevenueCameFromTheFirstOrSecondTwentyRowsOfTheAuditorium(int[][] arr) {
	System.out.println("i. feladat:");

	int first_twenty_rows_income = incomeCount(arr, 0, 19);
	int second_twenty_rows_income = incomeCount(arr, 20, 39);

	if(first_twenty_rows_income > second_twenty_rows_income) {
		System.out.println("Az első húsz sorban volt több bevétel.");
		System.out.println(" - Első húsz sor bevétele: " + first_twenty_rows_income + " forint");
		System.out.println(" - Második húsz sor bevétele: " + second_twenty_rows_income + " forint");
	} else if(first_twenty_rows_income < second_twenty_rows_income) {
		System.out.println("A második húsz sorban volt több bevétel.");
		System.out.println(" - Első húsz sor bevétele: " + first_twenty_rows_income + " forint");
		System.out.println(" - Második húsz sor bevétele: " + second_twenty_rows_income + " forint");
	} else {
		System.out.println("Az első és második húsz sorban egyenlő volt a bevétel.");
		System.out.println(" - Első húsz sor bevétele: " + first_twenty_rows_income + " forint");
		System.out.println(" - Második húsz sor bevétele: " + second_twenty_rows_income + " forint");
	}
}

private static int incomeCount(int[][] arr, int start, int end) {
	int result = 0;
	// 1600 - 1200
	for(int i = start; i < end; i ++) {
		for(int j = 0; j < 30; j++) {
			if(arr[i][j] == 2) {
				result += 1600;
			} else if(arr[i][j] == 1) {
				result += 1200;
			}
		}
	}		
	return result;
}
```

> sorok ahol több felnőtt jegyet adtak el:

```java
// h. Melyik sorokban adtak el több felnőttjegyet, mint gyerek, nyugdíjas jegyet (egymás mellé
//    szóközzel elválasztva írjuk ki a sorszámokat)?
private static void whichRowMoreAdultTicketsSoldOut(int[][] arr) {
	System.out.println("h. feladat:");

	int child_retired_count = 0;
	int adult_count = 0;

	System.out.print("Sorok, ahol több felnőttjegyet adtak el, mint gyerek/nyugdíjas jegyet: ");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				child_retired_count++;
			} else if(arr[i][j] == 2) {
				adult_count++;
			}
		}
		if(child_retired_count < adult_count) {
			System.out.print((i+1) + ". ");
		}
		child_retired_count = 0;
		adult_count = 0;
	}
	System.out.println();
}
```

> első kettő és utolsó kettő sorban az üresen maradt székek száma:

```java
// g. Hány üres hely maradt a nézőtér első kettő és utolsó kettő sorában?
private static int howManyEmptySeatsInFirstAndTwiceRowAndBeforeLastAndLastRow(int[][] arr) {
	System.out.println("g. feladat:");

	int empty_seats = 0;
	int row_1 = emptySeatsCount(arr, 0, empty_seats);
	int row_2 = emptySeatsCount(arr, 1, empty_seats);
	int row_39 = emptySeatsCount(arr, 38, empty_seats);
	int row_40 = emptySeatsCount(arr, 39, empty_seats);

	System.out.print("Az első kettő és az utolsó két sorban üresen maradt helyek száma: ");

	return row_1 + row_2 + row_39 + row_40;
}
private static int emptySeatsCount(int[][] arr, int row, int empty_seats) {
	for(int i = 0; i < 30; i++) {
		if(arr[row][i] == 0) {
			empty_seats++;
		}
	}
	return empty_seats;
}
```

> a 8. sorban melyik szék(ek) üres(ek)

```java
// f. A 8-as sorban melyik helyek üresek még? Írjuk ki a székek sorszámát egymás mellé
//    szóközzel elválasztva!
private static void whichPlacesEmptyInEighthRow(int[][] arr) {
	System.out.println("f. feladat:");

	System.out.println("Helyek amelyek üresen maradtak a 8.sorban:");
	for(int i = 0; i < 30; i++) {
		if(arr[7][i] == 0) {
			System.out.print((i+1) + ". ");
		}
	}
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
			//arrWriteOut(arr);
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