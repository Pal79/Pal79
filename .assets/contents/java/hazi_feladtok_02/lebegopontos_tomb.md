
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Hozz létre egy tömböt, amely a következő értékeket tárolja:
> 5.29 6.71 6.11 9.5 6.00 4.5 8.43 9.31 4.24 4.55 3.87
> - a. Írd ki a tömb elemeit egymás mellé szóközzel elválasztva!
> - b. Írd ki a 6.00-nál nagyobb értékeket egymás alá!
> - c. Írd ki a [4.55, 5.0,] intervallumban lévő számokat indexükkel együtt!
> - d. Hány db 7.00 feletti szám van a tömbben?
> - e. Mennyi az elemek összege?
> - f. Mennyi az elemek átlaga?

> Main:

```java
public static void main(String[] args) {

	double[] nums = {5.29, 6.71, 6.11, 9.5, 6.00, 4.5, 8.43, 9.31, 4.24, 4.55, 3.87};

	arrWriteOut(nums);
	System.out.println();
	numsBiggerThaSix(nums);
	System.out.println();
	numsBetweenFourPointFiftyFiveAndFivePointZero(nums);
	System.out.println();
	howManyNumsAboveSeven(nums);
	System.out.println();
	howManyTheItemsValue(nums);
	System.out.println();
	howManyTheItemsAverage(nums);
	System.out.println();
}
```

> elemek átlaga:

```java
// f. Mennyi az elemek átlaga?
private static void howManyTheItemsAverage(double[] arr) {
	System.out.println("f. feladat:");
	double values = 0;
	int count = 0;
	for(int i = 0; i < arr.length; i++) {
		values += arr[i];
		count++;
	}
	double result = values / count;
	System.out.println("Az elemek átlaga: " + result);
}
```

> elemek összege:

```java
// e. Mennyi az elemek összege?
private static void howManyTheItemsValue(double[] arr) {
	System.out.println("d. feladat:");
	double result = 0;
	for(int i = 0; i < arr.length; i++) {
		result += arr[i];
	}
	System.out.println("Az elemek összege: " + result);
}
```

> elemek 7.00 felett:

```java
// d. Hány db 7.00 feletti szám van a tömbben?
private static void howManyNumsAboveSeven(double[] arr) {
	System.out.println("d. feladat:");
	int count = 0;
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 7.0) {
			count++;
		}
	}
	System.out.println("A tömbben " + count + " darab 7.00-nál nagyobb szám van.");
}
```

> elemek 4.55 és 5.0 intervallumban:

```java
// c. Írd ki a [4.55, 5.0,] intervallumban lévő számokat indexükkel együtt!
private static void numsBetweenFourPointFiftyFiveAndFivePointZero(double[] arr) {
	System.out.println("c. feladat:");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] <= 5.0 && arr[i] >= 4.55) {
			System.out.print(arr[i] + " ");
		}
	}
	System.out.println();
}
```

> 6.00-nál nagyobb elemek:

```java
// b. Írd ki a 6.00-nál nagyobb értékeket egymás alá!
private static void numsBiggerThaSix(double[] arr) {
	System.out.println("b. feladat:");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 6.0) {
			System.out.print(arr[i] + " ");
		}
	}
	System.out.println();
}
```

> tömb kiírása:

```java
// a. Írd ki a tömb elemeit egymás mellé szóközzel elválasztva!
private static void arrWriteOut(double[] arr) {
	System.out.println("a. feladat:");
	for(int i = 0; i < arr.length; i++) {
		System.out.print(arr[i] + " ");
	}
	System.out.println();
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---