
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Ötöslottó: Készítsünk alkalmazást, amely egy teljes év ötöslottó húzásainak lehetséges
> eredményeit kezeli. Az ötöslottónál hetenként 5 számot húznak, a lehetséges számok 1-90 közötti
> tartományból kerülnek kiválasztásra. A mátrix feltöltésénél figyeljünk oda arra, hogy 1 számot 1
> héten csak 1X húznak ki!
>
> - a. Írjuk ki mind az 52 hét nyerőszámait (soronként)!
> - b. Kérjük be a felhasználótól, hogy melyik hét nyerőszámaira kíváncsi (1-52), majd írjuk ki a húzott számokat!
> - c. Melyik heteken húzták ki a 13-as számot?
> - d. A számok hány százaléka volt páros?
> - e. Hány darab 80-nál nagyobb szám volt az év második felében?
> - f. Volt –e olyan hét, ahol mindegyik szám páratlan volt?
> - g. A harmadik vagy a negyedik negyedévben volt több 50 feletti szám?
> - h. Kérjünk be a felhasználótól 5 darab (különböző) számot, majd vizsgáljuk meg melyik héten hány találata lett volna! Az eredményben csak a 2 vagy több találatos heteket kell megjeleníteni!
> - i. Melyik számot húzták ki a leggyakrabban? (emelt)
> - j. Melyek voltak azok a hetek, ahol volt egymást követő szám? (emelt)

> Main:

```java
private static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

public static void main(String[] args) {

	try {
		int[][] matrix = new int[52][5];
		arrUpload(matrix);
		arrWriteOut(matrix);
		System.out.println();
		whichWeeksWinningNumbers(matrix);
		System.out.println();
		inWhichWeeksTheNumberThirteenWasDrawn(matrix);
		System.out.println();
		howManyPercentIsAnEvenNumber(matrix);
		System.out.println();
		ANumberGreaterThanEightyInTheSecondHalfOfTheYear(matrix);
		System.out.println();
		weeksWhereAllNumbersAreOdd(matrix);
		System.out.println();
		thirdOrFourthQuarterOfTheYearOverFifty(matrix);
		System.out.println();
		howManyHitsWouldThereHaveBeen(matrix);
		System.out.println();
		whichNumberMostOften(matrix);
		System.out.println();
		whichWeeksConsecutiveNumbers(matrix);
		System.out.println();

		br.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> Hetek ahol egymást követő számok voltak:

```java
// j. Melyek voltak azok a hetek, ahol volt egymást követő szám? (emelt)
private static void whichWeeksConsecutiveNumbers(int[][] arr) {
	System.out.println("j. feladat:");

	List<String> weeks = new ArrayList<String>();

	int identifies = arr[0][0];

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(identifies == arr[i][j]) {
				if(i != 0) {
					weeks.add(i + ".hét és " + (i+1) + ".hét");
				}
			}
		}
		identifies = arr[i][0];
	}
	for(int i = 0; i < weeks.size(); i++) {
		System.out.println(weeks.get(i));
	}
}
```

> Melyik számot húzták a legtöbbször:

```java
// i. Melyik számot húzták ki a leggyakrabban? (emelt)
private static void whichNumberMostOften(int[][] arr) {
	System.out.println("i. feladat:");

	int[] counts = new int[91];
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			counts[arr[i][j]]++;
		}
	}
	/*
	for(int i = 0; i < counts.length; i++) {
		System.out.println(i + ". " + counts[i]);
	}
	*/
	int max = counts[0];
	for(int i = 0; i < counts.length; i++) {
		if(counts[i] > max) {
			max = counts[i];
		}
	}

	System.out.print("A szám vagy számok, melyet legtöbbször húztak: ");
	for(int i = 0; i < counts.length; i++) {
		if(max == counts[i]) {
			System.out.print(i + ". ");
		}
	}
	System.out.println();
}
```

> Melyik héten hány találat lett volna:

```java
// h. Kérjünk be a felhasználótól 5 darab (különböző) számot, majd vizsgáljuk meg melyik héten
//    hány találata lett volna! Az eredményben csak a 2 vagy több találatos heteket kell megjeleníteni!
private static void howManyHitsWouldThereHaveBeen(int[][] arr) {
	System.out.println("h. feladat:");

	int[] nums = new int[5];

	System.out.println("Kérlek adj meg öt egész számot (1-90):");

	for(int i = 0; i < nums.length; i++) {
		System.out.print((i+1) + ". szám: ");
		try {
			nums[i] = Integer.parseInt(br.readLine());
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
	System.out.println();

	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			for(int k = 0; k < nums.length; k++) {
				if(nums[k] == arr[i][j]) {
					count++;
				}
			}
		}
		if(count > 1) {
			System.out.println((i+1) + ". héten " + count + " találata volt.");
		}
		count = 0;
	}
}
```

> harmadik vagy negyedik negyedévben volt több 50 feletti találat:

```java
// g. A harmadik vagy a negyedik negyedévben volt több 50 feletti szám?
private static void thirdOrFourthQuarterOfTheYearOverFifty(int[][] arr) {
	System.out.println("g. feladat:");

	int whole_arr = 0;

	for(int i = 0; i < arr.length; i++) {
		whole_arr++;
	}		
	int half_arr = whole_arr / 2;
	int one_quarter_arr = half_arr / 2;
	int three_quarters_arr = half_arr + one_quarter_arr;

	//System.out.print(whole_arr + " " + three_quarters_arr + " " + half_arr + " " + one_quarter_arr);

	int three_quarters_above_fifty_count = 0;
	for(int i = half_arr; i < three_quarters_arr; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] > 50) {
				three_quarters_above_fifty_count++;
			}
		}
	}

	int fourth_quarters_above_fifty_count = 0;
	for(int i = three_quarters_arr; i < whole_arr; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] > 50) {
				fourth_quarters_above_fifty_count++;
			}
		}
	}

	if(three_quarters_above_fifty_count > fourth_quarters_above_fifty_count) {
		System.out.println("A harmadik negyedévben volt több 50 feletti szám.");
	} else if(three_quarters_above_fifty_count < fourth_quarters_above_fifty_count) {
		System.out.println("A negyedik negyedévben volt több 50 feletti szám.");
	} else {
		System.out.println("A harmadik és negyedik negyedévben, pont ugyanannyi 50 feletti szám volt.");
	}
}
```

> hét ahol csak páratlan számok voltak:

```java
// f. Volt –e olyan hét, ahol mindegyik szám páratlan volt?
private static void weeksWhereAllNumbersAreOdd(int[][] arr) {
	System.out.println("f. feladat:");

	int[] temp = new int[5];
	boolean find = true;

	System.out.println("Hét vagy hetek, mikor minden szám páratlan volt:");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			temp[j] = arr[i][j];
			if(j == 4) {
				for(int k = 0; k < temp.length; k++) {
					if(temp[k] % 2 != 0 && find == true) {
						if(k == 4) {
							System.out.print((i+1) + ". ");
						}
					} else {
						find = false;
					}
				}
			}
		}
		find = true;
	}
	System.out.println();
}
```

> második félévben hány 80 feletti szám:

```java
// e. Hány darab 80-nál nagyobb szám volt az év második felében?
private static void ANumberGreaterThanEightyInTheSecondHalfOfTheYear(int[][] arr) {
	System.out.println("e. feladat:");

	int biggerThanEighty = 0;
	boolean find = true;

	for(int i = 26; i < 52; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(find == true && arr[i][j] > 80) {
				//System.out.print((i+1) + ". ");
				biggerThanEighty++;
				find = false;
			}
		}
		find = true;
	}		
	System.out.println("A második félévben " + biggerThanEighty + " darab 80-nál nagyobb szám volt.");
}
```

> számok hány százaléka páros:

```java
// d. A számok hány százaléka volt páros?
private static void howManyPercentIsAnEvenNumber(int[][] arr) {
	System.out.println("d. feladat:");

	int even_count = 0;
	double result = 0;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] % 2 == 0) {
				even_count++;
			}
		}
	}
	result = (double)even_count / (double)(52*5) * 100;
	//System.out.println(even_count);
	System.out.println("A számok " + Math.round(result) + "%-a volt páros.");
}
```

> mely heteken húzták a 13-as számot:

```java
// c. Melyik heteken húzták ki a 13-as számot?
private static void inWhichWeeksTheNumberThirteenWasDrawn(int[][] arr) {
	System.out.println("c. feladat:");
	System.out.print("Ezeken a heteken húzták ki a 13-as számot: ");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] == 13) {
				System.out.print((i+1) + ". ");
			}
		}
	}
	System.out.println();
}
```

> x. hét nyerőszámai:

```java
// b. Kérjük be a felhasználótól, hogy melyik hét nyerőszámaira kíváncsi (1-52), majd írjuk ki a húzott számokat!
private static void whichWeeksWinningNumbers(int[][] arr) {
	System.out.println("b. feladat: ");

	try {
		System.out.println("Melyik hét nyerőszámaira kíváncsi?");
		System.out.print("Írja be a hét számát (1-52): ");
		int week = Integer.parseInt(br.readLine());

		System.out.print("A " + week + ".hét nyerőszámai: ");
		for(int i = 0; i < 5; i++) {
			System.out.print(arr[week-1][i] + " ");
		}
		System.out.println();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> éves lottószámok kiírása:

```java
// a. Írjuk ki mind az 52 hét nyerőszámait (soronként)!
private static void arrWriteOut(int[][] arr) {
	System.out.println("a. feladat: ");
	for(int i = 0; i < arr.length; i++) {
		System.out.print((i+1) + ". hét: ");
		for(int j = 0; j < arr[i].length; j++) {
			System.out.print(arr[i][j] + " ");
		}
		System.out.println();
	}
}
```

> tömbfeltöltés:

```java
private static void arrUpload(int[][] arr) {
	Random r = new Random();

	int[] temp_arr = new int[5];
	int num;
	boolean answer;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			do {
				num = r.nextInt(90-1+1)+1;
				answer = arrCheck(temp_arr, num);
			} while(!answer);
			temp_arr[j] = num;
			arr[i][j] = temp_arr[j];
		}
	}
}
```

> számok ismétlődésének vizsgálata:

```java
private static boolean arrCheck(int[] arr, int search) {
	boolean is_on = true;
	for(int item: arr) {
		if(item == search) {
			is_on = false;
		}
	}
	return is_on;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
