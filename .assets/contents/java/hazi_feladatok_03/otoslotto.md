
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
    ThisWeeksWasTihrteenNumber(nums);
    SoManyEvenAndSoManyOddNumbers(nums);
}
```

> ennyi páros és páratlan szám volt:

```java
// b. Ennyi páros szám volt: X, ennyi páratlan: Y
private static void SoManyEvenAndSoManyOddNumbers(int[][] arr) {
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