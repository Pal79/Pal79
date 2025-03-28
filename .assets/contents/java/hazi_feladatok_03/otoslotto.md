
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# otoslotto

---

> Készíts ötös-lottó alkalmazást! 
> Egy teljes év húzásait szimulálja az alkalmazás, 
> az egyes hetek kihúzott számait mentsük az otoslotto.txt állományba! 
> Figyeljünk arra, hogy 1 héten azonos szám nem kerül kihúzásra! 
> Soronként 1 hét adatai szerepeljenek a fájlba! 
>
> (otoslotto)
>
> Készítsünk statisztikát a statisztika.txt fájlba, 
> melybe a következő adatokat tároljuk:
>
> - a. Ezeken a heteken volt a 13-as szám kihúzva
> - b. Ennyi páros szám volt: X, ennyi páratlan: Y
> - c. Kérjünk be egy hét sorszámát a felhasználótól, majd írjuk ki az adott hét nyerőszámait!
> - d. Az összes kihúzott szám hány százaléka volt 80 felett?

> Main:

```java
public static void main(String[] args) {

	int[][] nums = new int[52][5];
	ArrUpload(nums);

	NumsUploadToFile(nums);
	System.out.println();
	ThisWeeksWasTihrteenNumber(nums);
	System.out.println();
	SoManyEvenAndSoManyOddNumbers(nums);
	System.out.println();
	WinningNumbersForTheGivenWeek(nums);
	System.out.println();
	WhatPercentageOfTheNumbersDrawnWereOverEighty(nums);
	System.out.println();
}
```

> kihúzott számok hány százaléka 80 felett:

```java
// d. Az összes kihúzott szám hány százaléka volt 80 felett?
private static void WhatPercentageOfTheNumbersDrawnWereOverEighty(int[][] arr) {
	System.out.println("d. feladat:");

	int all_count = 0;
	int eighty_count = 0;
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			if(arr[i][j] > 80) {
				eighty_count++;
			}
			all_count++;
		}
	}

	//System.out.println(all_count + " " + eighty_count);

	double result = Math.round((double)eighty_count / (double)all_count * 100);

	System.out.println("A kihúzott számok " + result + "%-a volt 80 feletti szám.");
}
```

> adott hét nyerőszámai:

```java
// c. Kérjünk be egy hét sorszámát a felhasználótól, majd írjuk ki az adott hét nyerőszámait!
private static void WinningNumbersForTheGivenWeek(int[][] arr) {
	System.out.println("c. feladat:");

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.println("Add meg az adott hét számát (1-52): ");
		int week = Integer.parseInt(br.readLine());

		System.out.println(week + ". hét nyerőszámai:");
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

> ennyi páros és páratlan szám volt:

```java
// b. Ennyi páros szám volt: X, ennyi páratlan: Y
private static void SoManyEvenAndSoManyOddNumbers(int[][] arr) {
	System.out.println("b. feladat:");
	try {
		BufferedReader br = new BufferedReader(
				new InputStreamReader(
						new FileInputStream("statisztika.txt"),"UTF-8"));

		String content = "";
		while(br.ready()) {
			String row = br.readLine();
			content = row;
		}

		FileWriter fw = new FileWriter("statisztika.txt", false);

		int evens = 0;
		int odds = 0;

		fw.write(content);
		fw.write("\n");

		for(int i = 0; i < arr.length; i++) {
			for(int j = 0; j < arr[i].length; j++) {
				if(arr[i][j] % 2 == 0) {
					evens++;
				} else {
					odds++;
				}
			}
		}
		fw.write("Ennyi páros szám volt: " + evens + "\n");
		fw.write("Ennyi páratlan szám volt: " + odds);

		fw.close();
		br.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> hetek, melyeken a 13-as számot kihúzták:

```java
// a. Ezeken a heteken volt a 13-as szám kihúzva
private static void ThisWeeksWasTihrteenNumber(int[][] arr) {
	System.out.println("a. feladat:");
	try {
		FileWriter fw = new FileWriter("statisztika.txt", false);

		fw.write("Ezeken a heteken húzták a 13-as számot: ");
		for(int i = 0; i < arr.length; i++) {
			for(int j = 0; j < arr[i].length; j++) {
				if(arr[i][j] == 13) {
					fw.write((i+1) + ". ");
				}
			}
		}

		fw.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> számok feltöltése fájlba:

```java
private static void NumsUploadToFile(int[][] arr) {
	try {
		FileWriter fw = new FileWriter("otoslotto.txt", false);

		for(int i = 0; i < arr.length; i++) {
			for(int j = 0; j < arr[i].length; j++) {
				fw.write(arr[i][j] + " ");
			}
			fw.write("\n");
		}

		fw.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> tömbfeltöltés:

```java
private static void ArrUpload(int[][] arr) {
	Random r = new Random();

	int[] temp_arr = new int[5];
	int num;
	boolean answer;

	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr[i].length; j++) {
			do {
				num = r.nextInt(90-1+1)+1;
				answer = ArrCheck(temp_arr, num);
			} while(!answer);
			temp_arr[j] = num;
			arr[i][j] = temp_arr[j];
		}
	}
}
```

> számok ismétlődésének ellenőrzése:

```java
private static boolean ArrCheck(int[] arr, int search) {
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