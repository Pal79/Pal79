
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> A sarki zöldséges 36. heti bevételei hétfőtől vasárnapig a következők: 
> 250600 Ft 200150 Ft 190500 Ft 230700 Ft 280640 Ft 220750 Ft 195300 Ft
> - a. Mennyi volt a heti összbevétel? (Mintaválasz: A heti összes bevétel: x Ft volt.)
> - b. Mennyi volt a napi átlagos bevétel? (Mintaválasz: A napi átlagos bevétel: x Ft volt.)
> - c. Hány olyan nap volt, amikor meghaladta a bevétel a 200.000 Ft-ot? (Mintaválasz: Ennyi db nap volt, amikor meghaladta a bevétel a 200000 Ft: 5 db)
> - d. Mennyi volt a legkevesebb bevétel és melyik napra esett? (Mintaválasz: Legkevesebb bevétel szerdán volt: 190500 Ft)
> - e. Mennyi volt a legtöbb bevétel és melyik napra esett? (Mintaválasz: Legtöbb bevétel pénteken volt: 280640 Ft)
> - f. Mennyi volt az összes bevétel hétköznap? (Mintaválasz: Hétköznap ennyi volt az összes bevétel: x Ft)
> - g. Mennyi volt a hétvégi átlagbevétel? (Mintaválasz: Hétvégi átlagbevétel: x Ft)
> - h. Kérj be a felhasználótól egy számot 1-7 között (H-V), majd írd ki a napnak megfelelő bevételt!
> - i. A hétvégi bevétel hány százaléka a teljes heti bevételnek? (Mintaválasz: A hétvégi bevétel: x %-a a teljes heti bevételnek.)

> Main:

```java
public static void main(String[] args) {

	int[] payments = {250600, 200150, 190500, 230700, 280640, 220750, 195300};

	totalWeeklyIncome(payments);
	System.out.println();
	dailyAverageIncome(payments);
	System.out.println();
	howManyDaysDidItExceedHUFTwoHundredThousand(payments);
	System.out.println();
	whichDayLowestIncome(payments);
	System.out.println();
	whichDayHighestIncome(payments);
	System.out.println();
	allIncomeOnWeekdays(payments);
	System.out.println();
	weekendIncomeAverage(payments);
	System.out.println();
	incomeForAGivenDay(payments);
	System.out.println();
	weekendIncomeAsAPercentageOfweeklyIncome(payments);
	System.out.println();
}
```

> hétvégi bevétel hány százaléka a heti bevételnek:

```java
// i. A hétvégi bevétel hány százaléka a teljes heti bevételnek? 
// (Mintaválasz: A hétvégi bevétel: x %-a a teljes heti bevételnek.)
private static void weekendIncomeAsAPercentageOfweeklyIncome(int[] arr) {
	System.out.println("i. feladat:");

	double weekly_income = 0;
	for(int i = 0; i < arr.length; i++) {
		weekly_income += arr[i];
	}

	double weekend_income = 0;
	for(int i = 0; i < arr.length; i++) {
		if(i >= 5) {
			weekend_income += arr[i];
		}
	}
	double result = weekend_income / weekly_income * 100;
	// System.out.println("Heti bevétel: " + weekly_income);
	// System.out.println("Hétvégi bevétel: " + weekend_income);
	System.out.println("A hétvégi bevétel: " + result + " %-a a teljes heti bevételnek.");
}
```

> felhasználó adott napi bevétel megtekintés:

```java
// h. Kérj be a felhasználótól egy számot 1-7 között (H-V), 
//majd írd ki a napnak megfelelő bevételt!
private static void incomeForAGivenDay(int[] arr) {
	System.out.println("h. feladat:");

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	String[] days = {"hétfő", "kedd", "szerda", "csütörtök", "péntek", "szombat", "vasárnap"};
	int index;

	try {
		System.out.print("kérlek írd be az adott nap sorszámát (1-7; H-V): ");
		index = Integer.parseInt(br.readLine())-1;

		System.out.println("A " + days[index] + "i összes bevétel: " + arr[index]);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nCsak egész számot írhatsz be 1-től 7-ig.");
	}
}
```

> hétvégi átlag bevétel:

```java
// g. Mennyi volt a hétvégi átlagbevétel? (Mintaválasz: Hétvégi átlagbevétel: x Ft)
private static void weekendIncomeAverage(int[] arr) {
	System.out.println("g. feladat:");

	int incomes = 0;
	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		if(i >= 5) {
			incomes += arr[i];
			count++;
		}
	}
	int result = incomes / count;

	System.out.println("Hétvégi átlagbevétel: " + result +" Ft");
}
```

> összes bevétel hétköznap:

```java
// f. Mennyi volt az összes bevétel hétköznap? 
// (Mintaválasz: Hétköznap ennyi volt az összes bevétel: x Ft)
private static void allIncomeOnWeekdays(int[] arr) {
	System.out.println("f. feladat:");

	int result = 0;

	for(int i = 0; i < arr.length; i++) {
		if(i <= 4) {
			result += arr[i];
		}
	}

	System.out.println("Hétköznap ennyi volt az összes bevétel: " + result + " Ft");
}
```

> legtöbb bevétel és melyik napon:

```java
// e. Mennyi volt a legtöbb bevétel és melyik napra esett? 
// (Mintaválasz: Legtöbb bevétel pénteken volt: 280640 Ft)
private static void whichDayHighestIncome(int[] arr) {
	System.out.println("e. feladat:");

	String[] days = {"hétfőn", "kedden", "szerdán", "csütörtökön", "pénteken", "szombaton", "vasárnap"};
	int index = 0;
	int income_temp = 0;

	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > income_temp) {
			income_temp = arr[i];
			index = i;
		}
	}

	System.out.println("Legtöbb bevétel " + days[index] + " volt: " + income_temp + " Ft");
}
```

> legkevesebb bevétel és melyik napon:

```java
// d. Mennyi volt a legkevesebb bevétel és melyik napra esett? 
// (Mintaválasz: Legkevesebb bevétel szerdán volt: 190500 Ft)
private static void whichDayLowestIncome(int[] arr) {
	System.out.println("d. feladat:");

	String[] days = {"hétfőn", "kedden", "szerdán", "csütörtökön", "pénteken", "szombaton", "vasárnap"};
	int index = 0;
	int income_temp = 500000000;

	for(int i = 0; i < arr.length; i++) {
		if(arr[i] < income_temp) {
			income_temp = arr[i];
			index = i;
		}
	}

	System.out.println("Legkevesebb bevétel " + days[index] + " volt: " + income_temp + " Ft");
}
```

> napok száma, melyek meghaladták a 200.000 Ft-os bevételt:

```java
// c. Hány olyan nap volt, amikor meghaladta a bevétel a 200.000 Ft-ot? 
//(Mintaválasz: Ennyi db nap volt, amikor meghaladta a bevétel a 200000 Ft: 5 db)
private static void howManyDaysDidItExceedHUFTwoHundredThousand(int[] arr) {
	System.out.println("c. feladat:");

	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 200000) {
			count++;
		}
	}

	System.out.println("Ennyi db nap volt, amikor meghaladta a bevétel a 200000 Ft: " + count + " db");
}
```

> napi átlagos bevétel a héten:

```java
// b. Mennyi volt a napi átlagos bevétel? (Mintaválasz: A napi átlagos bevétel: x Ft volt.)
private static void dailyAverageIncome(int[] arr) {
	System.out.println("b. feladat:");

	int incmoes = 0;
	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		incmoes += arr[i];
		count++;
	}
	int result = incmoes / count;

	System.out.println("A napi átlagos bevétel: " + result + " Ft volt.");
}
```

> összes bevétel:

```java
// a. Mennyi volt a heti összbevétel? (Mintaválasz: A heti összes bevétel: x Ft volt.)
private static void totalWeeklyIncome(int[] arr) {
	System.out.println("a. feladat:");

	int result = 0;

	for(int i = 0; i < arr.length; i++) {
		result += arr[i];
	}
	System.out.println("A heti összes bevétel: " + result + " Ft volt.");
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---