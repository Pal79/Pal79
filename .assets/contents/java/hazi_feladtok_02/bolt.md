
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Készítsünk alkalmazást, amely egy bolt négy heti bevételeit tükrözi napokra lebontva. 
> Töltsünk fel egy megfelelő méretű mátrixot véletlenszerűen 200.000 Ft. és 300.000 Ft. közti értékekkel.
> a. Írjuk ki a mátrix elemeit táblázatba rendezve! A sorok elé írjuk ki a hét sorszámát, illetve az oszlopok fölé az adott nap sorszámát!
> b. Mennyi volt a teljes havi átlag- és összbevétel?
> c. Mennyi volt az egyes hetek átlag- és összbevétele?
> d. Mennyi volt a második héten a különbség a hétköznapi és a hétvégi bevétel között?
> e. Melyik héten keletkezett a legnagyobb bevétel?
> f. Melyik hét melyik napján keletkezett a legnagyobb bevétel? A nap nevét szövegesen írd ki!
> g. Az első kettő vagy a második kettő héten keletkezett több bevétel?
> h. Kérjünk be a felhasználótól egy összeget és írd ki, hogy mely hetek mely napjain keletkezett a bekért összegnél kisebb bevétel!

> Main:

```java
public static void main(String[] args) {

	int[][] incomes = arrUpload();

	arrWriteOut(incomes);
	System.out.println();
	howManyTheMonthlyIncomeAndMonthlyAverageIncome(incomes);
	System.out.println();
	weeklyIncomeAndWeeklyAverageIncome(incomes);
	System.out.println();
	howManyIncomeSecondWeekDifferentWeekdaysAndWeekend(incomes);
	System.out.println();
	whichWeekIsBiggerIncome(incomes);
	System.out.println();
}
```

> melyik héten volt a legtöbb bevétel:

```java
// e) Melyik héten keletkezett a legnagyobb bevétel?
private static void whichWeekIsBiggerIncome(int[][] arr) {
	System.out.println("e. feladat:");

	int result = 0;
	int week = 0;
	for(int i = 0; i < arr.length; i++) {
		int weekly_income = 0;
		for(int j = 0; j < arr[i].length; j++) {
			weekly_income += arr[i][j];
		}
		if(weekly_income > result) {
			result = weekly_income;
			week = i+1;
		}
	}
	System.out.println("A(z) " + week + ". héten volt a legtöbb bevétel.\nÖsszesen: " + result + " forint");
}
```

> különbség a hétköznapi és hétvégi bevétel között a 2. héten:

```java
// d) Mennyi volt a második héten a különbség a hétköznapi és a hétvégi bevétel között?
private static void howManyIncomeSecondWeekDifferentWeekdaysAndWeekend(int[][] arr) {
	System.out.println("d. feladat:");

	int weekdays_income = 0;
	for(int i = 0; i < 5; i++) {
		weekdays_income += arr[1][i];
	}
	int weekend_income = 0;
	System.out.println();
	for(int i = 5; i < 7; i++) {
		weekend_income += arr[1][i];
	}
	System.out.println("A 2. hét hétköznapi és hétvégi bevételének a különbsége: " + (weekdays_income - weekend_income + " forint."));
}
```

> heti átlag és teljes bevétel:

```java
// c) Mennyi volt az egyes hetek átlag- és összbevétele?
private static void weeklyIncomeAndWeeklyAverageIncome(int[][] arr) {
	System.out.println("c. feladat:");

	for(int i = 0; i < arr.length; i++) {
		int weekly_income = 0;
		int count = 0;
		for(int j = 0; j < arr[i].length; j++) {
			weekly_income += arr[i][j];
			count++;
		}
		System.out.println((i+1) + ". hét átlag bevétele: " + (weekly_income / count));
		System.out.println((i+1) + ". hét teljes bevétele: " + weekly_income);
	}
}
```

> teljes havi bevétel és átlag:

```java
// b) Mennyi volt a teljes havi átlag- és összbevétel?
private static void howManyTheMonthlyIncomeAndMonthlyAverageIncome(int[][] arr) {
	System.out.println("b. feladat:");

	int all_income = 0;
	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			count++;
			all_income += arr[i][j];
		}
	}
	System.out.println("A teljes havi bevétel: " + all_income + " forint volt.");
	System.out.println("Az átlag bevétel: " + (all_income / count) + " forint volt.");
}
```

> tömb kiíratása:

```java
// a. Írjuk ki a mátrix elemeit táblázatba rendezve! 
// A sorok elé írjuk ki a hét sorszámát, illetve az oszlopok fölé az adott nap sorszámát!
private static void arrWriteOut(int[][] arr) {
	System.out.println("a. feladat:");

	System.out.print("\t");
	for(int i = 0; i < 7; i++) {
		System.out.print((i+1) + ".\t");
	}
	System.out.println();

	for(int i = 0; i < arr.length; i++) {
		System.out.print((i+1) + ". hét ");
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
	int[][] incomes = new int[4][7];
	Random r = new Random();

	for(int i = 0; i < incomes.length; i++) {
		for(int j = 0; j < incomes[i].length; j++) {
			incomes[i][j] = r.nextInt(300000 - 200000 + 1) + 200000;
		}
	}	
	return incomes;
}
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---