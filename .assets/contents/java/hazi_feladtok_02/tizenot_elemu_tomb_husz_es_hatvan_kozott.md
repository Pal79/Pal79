
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Hozz létre egy 15 elemű tömböt véletlen számokkal [20, 60] közötti intervallumban, 
> majd írd ki az elemeket egymás mellé szóközzel elválasztva!
> - a. Írd ki az 40-nél nagyobb értékeket egymás mellé!
> - b. Írd ki a 25-nél kisebb értékeket, ha nincs ilyen, akkor „Nincsen 25-nél kisebb” szöveg jelenjen meg a konzolon!
> - c. Írd ki az 3-mal maradék nélkül osztható számokat egymás mellé!
> - d. Írd ki a páratlan elemeket egymás mellé!

> Main:

```java
public static void main(String[] args) {

	//arrWriteOut(arrUpload());
	//System.out.println();
	valueBiggerThanForty(arrUpload());
	System.out.println("\n");
	valuesLowerThanTwentyFive(arrUpload());
	System.out.println("\n");
	divisibleWithThree(arrUpload());
	System.out.println("\n");
	oddElements(arrUpload());
	System.out.println("\n");
}
```

> Páratlan elemek keresése:

```java
// d. Írd ki a páratlan elemeket egymás mellé!
private static void oddElements(int[] arr) {
	System.out.println("d. feladat");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] % 2 != 0) {
			System.out.print(arr[i] + " ");
		}
	}
}
```

> hárommal osztható számok:

```java
// c. Írd ki az 3-mal maradék nélkül osztható számokat egymás mellé!
private static void divisibleWithThree(int[] arr) {
	System.out.println("c. feladat:");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] % 3 == 0) {
			System.out.print(arr[i] + " ");
		}
	}
}
```

> 25-nél kisebb elemek:

```java
// b. Írd ki a 25-nél kisebb értékeket, ha nincs ilyen, akkor „Nincsen 25-nél kisebb” szöveg jelenjen meg a konzolon!
private static void valuesLowerThanTwentyFive(int[] arr) {
	int count = 0;

	for(int i = 0; i < arr.length; i++) {
		if(arr[i] < 25) {
			count++;
		}
	}
	//System.out.println(count);

	System.out.println("b. feladat:");
	if(count == 0) {
		System.out.println("Nincsen 25-nél kisebb");
	} else {
		int[] nums = new int[count];
		int j = 0;

		for(int item : arr) {
			if(item < 25) {
				nums[j] = item;
				System.out.print(nums[j] + " ");
			}
		}
	}
}
```

> 40-nél nagyobb elemek:

```java
// a. Írd ki az 40-nél nagyobb értékeket egymás mellé!
private static void valueBiggerThanForty(int[] arr) {

	System.out.println("a. feladat:");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 40) {
			System.out.print(arr[i] + " ");
		}
	}
}
```

> tömb kiírás (teszteléshez):

```java
private static void arrWriteOut(int[] arr) {
	for(int i = 0; i < arr.length; i++) {
		System.out.print(arr[i] + " ");
	}
}
```

> tömbfeltöltés:

```java
private static int[] arrUpload() {
	Random r = new Random();
	int[] nums = new int[15];

	for(int i = 0; i < nums.length; i++) {
		nums[i] = r.nextInt((60 - 20) + 1) + 20;
	}
	return nums;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---