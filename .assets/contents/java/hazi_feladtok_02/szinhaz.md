
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

>  Színház: Készítsünk alkalmazást, amely egy színház nézőterének foglaltságát, 
> jegyeladásait szimulálja. A terem 30 sorának mindegyikében 20 szék található. 
> Töltsünk fel egy megfelelő méretű mátrixot véletlenszerűen 
> 0-val (üres) vagy 1-el (foglalt) értékekkel. 
> A jegyárakat két kategóriába sorolják: 
>    - emeltáras az első 6 sorban, 4500 Ft, 
>    - a többi helyen 3500 Ft.
>
> - a. Írjuk ki a mátrix elemeit!
> - b. Kérjünk be egy sorszámot és székszámot a felhasználótól, majd ellenőrizzük, hogy foglalt-e az adott hely! Amennyiben üres volt, hajtsuk végre a foglalást!
> - c. Eddig hány jegyet értékesítettek?
> - d. A jegyek hány százalékát nem értékesítették még?
> - e. Kérjünk be egy sorszámot, majd írjuk ki, a megadott sorban melyik székek üresek még!
> - f. Eddig mennyi a bevétel jegyeladásokból?
> - g. Hány üres hely maradt a nézőtér mindkét oldalának szélső két-két székében?
> - h. Volt –e olyan sor és ha igen melyik, amelyiknél még 6 jegyet sem sikerült értékesíteni?
> - i. Készíts statisztikát: soronként hány százalékát adták el a jegyeknek? (emelt)
> - j. Van –e olyan sor és ha igen melyik az, ahol 3 üres hely egymás mellett helyezkedik el? (emelt)

> Main:

```java
public static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

public static void main(String[] args) {

	int[][] tickets = arrUpload();

	try {
		matrixWriteOut(tickets);
		System.out.println();
		checkReservation(tickets);
		System.out.println();
		System.out.println("Eddig " + howManyTicketsWereSold(tickets) + " jegyet árusítottak.");
		System.out.println();
		System.out.println("A jegyek " + whatPercentageOfTicketsAreNotSold(tickets) + "%-át még nem árusították.");
		System.out.println();
		whichSeatIsEmptyInTheGivenRow(tickets);
		System.out.println();
		System.out.println("Eddigi bevétel a jegyeladásokból: " + howMuchIsTheRevenueFromTheTicketsSoldSoFar(tickets) + " Forint.");
		System.out.println();
		System.out.println("Üresen maradt székek a nézőtér mindkét oldalának két-két székében: " + emptySeatsTwoOnEachSide(tickets));
		System.out.println();
		inWhichRowThereWereNoSales(tickets);
		System.out.println();
		whatPercentageOfTicketsWereSoldPerRow(tickets);
		System.out.println();
		threeEmptyChairsNextToEachOther(tickets);
		System.out.println();

		br.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> 3 üres szék egymás mellett:

```java
// j. Van –e olyan sor és ha igen melyik az, ahol 3 üres hely egymás mellett helyezkedik el? (emelt)
private static void threeEmptyChairsNextToEachOther(int[][] arr) {
	System.out.println("j.feladat:");

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

> soronként hány százalékát adták el a jegyeknek:

```java
// i. Készíts statisztikát: soronként hány százalékát adták el a jegyeknek? (emelt)
private static void whatPercentageOfTicketsWereSoldPerRow(int[][] arr) {
	System.out.println("i. feladat:");

	int[] sold_seats = new int[30];
	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(j < 20 && arr[i][j] == 1) {
				count++;
				sold_seats[i] = count;
			}
		}
		count = 0;
	}

	/*
	for(int i = 0; i < sold_seats.length; i++) {
		System.out.println((i+1) + ". sorban: " + sold_seats[i] + " helyet adtak el.");
	}
	*/

	double[] sold_percents = new double[30];
	for(int i = 0; i < sold_percents.length; i++) {
		sold_percents[i] = (double)sold_seats[i] / (double)20 * 100;
		//System.out.print(sold_percents[i] + " ");
	}

	for(int i = 0; i < sold_percents.length; i++) {
		System.out.println((i+1) + ". sorban " + sold_percents[i] + "%-át adták el a jegyeknek.");
	}
}
```

> volt-e olyan sor, ahol még 6 jegyet sem sikerült értékesíteni:

```java
// h. Volt –e olyan sor és ha igen melyik, amelyiknél még 6 jegyet sem sikerült értékesíteni?
private static void inWhichRowThereWereNoSales(int[][] arr) {
	System.out.println("h.feladat:");

	int count = 0;
	int[] empty_seats = new int[30];

	System.out.println("Sorok, ahol még nem sikerült még 6 jegyet értékesíteni: ");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 0 && j < 20) {
				count++;
				empty_seats[i] = count;
			}
		}
		count = 0;
	}

	for(int i = 0; i < empty_seats.length; i++) {
		//System.out.print(empty_seats[i] + " ");
		if(empty_seats[i] >= 6) {
			System.out.print((i+1) + ". ");
		}
		//System.out.println();
	}	
	System.out.println();
}
```

> nézőtér két-két oldanlán maradt üres székek:

```java
// g. Hány üres hely maradt a nézőtér mindkét oldalának szélső két-két székében?
private static int emptySeatsTwoOnEachSide(int[][] arr) {
	System.out.println("g.feladat:");

	int empty_seats = 0;
	int column_1 = emptySeatsCount(arr, 0, empty_seats);
	int column_2 = emptySeatsCount(arr, 1, empty_seats);
	int column_3 = emptySeatsCount(arr, 18, empty_seats);
	int column_4 = emptySeatsCount(arr, 19, empty_seats);

	return column_1 + column_2 + column_3 + column_4;
}
```

> üres székek megszámolása és tömbbe írása:

```java
private static int emptySeatsCount(int[][] arr, int row, int empty_seats) {
	for(int i = 0; i < 30; i++) {
		if(arr[i][19] == 0) {
			empty_seats++;
		}
	}
	return empty_seats;
}
```

> összes bevétel eddig:

```java
// f. Eddig mennyi a bevétel jegyeladásokból?
private static int howMuchIsTheRevenueFromTheTicketsSoldSoFar(int[][] arr) {
	System.out.println("f. feladat:");

	int result = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				if(i <= 5) {
					result += 4500;
				} else {
					result += 3500;
				}
			}
		}
	}
	return result;
}
```

> sorszám bekérés és üres székek elleőrzése:

```java
// e. Kérjünk be egy sorszámot, majd írjuk ki, a megadott sorban melyik székek üresek még!
private static void whichSeatIsEmptyInTheGivenRow(int[][] arr) {
	System.out.println("e. feladat:");

	try {
		System.out.println("Írj be egy sorszámot (1-20), hogy megtudd, az adott sorban mely székek üresek még.");
		System.out.print("Sorszám: ");
		int row_number = Integer.parseInt(br.readLine())-1;

		int count = 0;

		for(int i = 0; i < 20; i++) {
			if(arr[row_number][i] == 0) {
				count++;
			}
		}

		System.out.println("A " + (row_number+1) + ". sorban, " + count + " darab üres szék van.");
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nCsak egész számot adhatsz meg, 1-től 20-ig.");
	}
}
```

> jegyek hány százaléka van értékesítve:

```java
// d. A jegyek hány százalékát nem értékesítették még?
private static double whatPercentageOfTicketsAreNotSold(int[][] arr) {
	System.out.println("d. feladat:");

	int empty_seats = 0;
	int all_seats = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 0) {
				empty_seats++;
			}
			all_seats++;
		}
	}
	return (double)empty_seats / (double)all_seats * 100;
	//num1 / num2 * 100
}
```

> eddigi jegyek értékesítve:

```java
// c. Eddig hány jegyet értékesítettek?
private static int howManyTicketsWereSold(int[][] arr) {
	System.out.println("c. feladat:");

	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 1) {
				count++;
			}
		}
	}
	return count;
}
```

> sorszám és helyszám bekérés és foglalás ha üres:

```java
// b. Kérjünk be egy sorszámot és székszámot a felhasználótól, majd ellenőrizzük, hogy foglalt-e az adott hely! 
//    Amennyiben üres volt, hajtsuk végre a foglalást!
private static void checkReservation(int[][] arr) {
	System.out.println("b. feladat:");
	try {
		System.out.println("Kérlek add meg a sorszámot (1-30) és a székszámot (1-20), hogy megtudd, foglalt-e.");
		System.out.println("Ha üres, akko lefoglaljuk neked.");

		System.out.print("Sorszám: ");
		int row_number = Integer.parseInt(br.readLine()) - 1;
		System.out.print("Székszám: ");
		int column_number = Integer.parseInt(br.readLine()) -1;

		if(arr[row_number][column_number] == 1) {
			System.out.println("Ez a hely már foglalt.");
		} else {
			arr[row_number][column_number] = 1;
			System.out.println("A hely lefoglalva!");
		}			
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nCsak egész számot adhatsz meg, sorszám 1-től 30-ig és székszámot 1-től 20-ig.!");
	}
}
```

> mátrix tömb elemeinek kiírása:

```java
// a. Írjuk ki a mátrix elemeit!
private static void matrixWriteOut(int[][] arr) {
	System.out.println("a. feladat:");
	for(int i = 0; i < arr.length; i++) {
		System.out.print((i+1) + ".sor: ");
		for(int j = 0; j < arr[i].length; j++) {
			System.out.print(arr[i][j] + " ");
		}
		System.out.println();
	}
}
```

> mátrix tömb feltöltése:

```java
private static int[][] arrUpload() {

	Random r = new Random();

	int[][] matrix = new int[30][20];

	for(int i = 0; i < 30; i++) {
		for(int j = 0; j < 20; j++) {
			matrix[i][j] = r.nextInt(1 - 0 + 1) + 0;
		}
	}
	return matrix;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---