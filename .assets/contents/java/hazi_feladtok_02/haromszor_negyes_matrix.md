
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Töltsünk fel sorfolytonosan egy 3X4 –es mátrixot a felhasználótól érkező egész számokkal.
> - a. Írjuk ki a mátrix elemeit!
> - b. Kérjünk be egy sor és oszlopindexet, majd írjuk ki az indexek által határolt értéket!
> - c. Cseréljük meg az első és utolsó sorát, majd írjuk ki újra a mátrixot!
> - d. Cseréljük meg az első és második oszlopot, majd írjuk ki újra a mátrixot!

> Main:

```java
public static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

public static void main(String[] args) {

	try {
		int[][] arr = arrUpload();
		System.out.println();

		// a. feladat
		arrWriteOut(arr);
		System.out.println();

		// b.feladat
		rowColumnIndexValue(arr);
		System.out.println();

		// c. feladat
		changeRowsWriteOut(changeFirstRowToLastRow(arr));
		System.out.println();

		changeColumnsWriteOut(changeColumnFirstAndSecond(arr));
		System.out.println();

		br.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

> első és második oszlop csere és kiíratás:

```java
// d. Cseréljük meg az első és második oszlopot, majd írjuk ki újra a mátrixot!
private static int[][] changeColumnFirstAndSecond(int[][] arr) {
	int temp;
	for(int i = 0; i < arr.length; i++) {
		temp = arr[i][0];
		arr[i][0] = arr[i][1];
		arr[i][1] = temp;
	}
	return arr;
}
private static void changeColumnsWriteOut(int[][] arr) {
	System.out.println("d. feladat:");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr.length; j++) {
			System.out.print(arr[i][j] + " ");
		}
		System.out.println();
	}
}
```

> első és utolsó sorok cseréje és kiíratás:

```java
// c. Cseréljük meg az első és utolsó sorát, majd írjuk ki újra a mátrixot!
private static int[][] changeFirstRowToLastRow(int[][] arr) {
	int temp;
	for(int i = 0; i < arr.length; i++) {
		temp = arr[0][i];
		arr[0][i] = arr[2][i];
		arr[2][i] = temp;
	}
	return arr;
}
private static void changeRowsWriteOut(int[][] arr) {
	System.out.println("c. feladat:");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr.length; j++) {
			System.out.print(arr[i][j] + " ");
		}
		System.out.println();
	}
}
```

> index bekérés és érték kiírás:

```java
// b. Kérjünk be egy sor és oszlopindexet, majd írjuk ki az indexek által határolt értéket!
private static void rowColumnIndexValue(int[][] arr) {
	System.out.println("b. feladat:");
	System.out.println("Kérlek adj meg egy sor(0-2) és egy oszlop(0-2) indexet:");
	try {
		System.out.print(" Sor index: ");
		int row = Integer.parseInt(br.readLine());
		System.out.print(" Oszlop index: ");
		int column = Integer.parseInt(br.readLine());
		System.out.println("Az indexek helyén találaható szám: " + arr[row][column]);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

> mátrix elemeinek kiírása:

```java
// a. Írjuk ki a mátrix elemeit!
private static void arrWriteOut(int[][] arr) {
	System.out.println("a. feladat: ");
	for(int i = 0; i < arr.length; i++) {
		for(int j = 0; j < arr.length; j++) {
			System.out.print(arr[i][j] + " ");
		}
		System.out.println();
	}
}
```

> mátrix feltöltése elemekkel, felhasználó által:

```java
// Töltsünk fel sorfolytonosan egy 3X4 –es mátrixot a felhasználótól érkező egész számokkal.
private static int[][] arrUpload() {
	int[][] matrix = new int[3][4];

	System.out.println("Kérlek írj be egész számokat:");
	try {
		for(int i = 0; i < matrix.length; i++) {
			for(int j = 0; j < matrix.length; j++) {
				System.out.print((i+1) + ".sor " + (j+1) + ". oszlop száma: ");
				int num = Integer.parseInt(br.readLine());
				matrix[i][j] = num;
			}
		}
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
	return matrix;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
