
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Tölts fel egy 30 elemű tömböt véletlen számokkal [-10;+15] intervallumból, 
> majd írd ki az elemeket egymás mellé szóközzel elválasztva!
> - a. Hány db pozitív szám van a tömbben?
> - b. Hány db 2-vel és 3-mal is maradék nélkül osztható szám van tömbben?
> - c. Hány db 10 feletti elem van a tömbben?
> - d. Melyik érték van az utolsó előtti helyen?
> - e. Kérj be a felhasználótól egy egész számot (0-29 között), majd írd ki a megadott indexen lévő elemet!
> - f. Írd ki a legnagyobb elem értékét és indexét!
> - g. Írd ki a legkisebb elem értékét és indexét!

> Main:

```java
public static void main(String[] args) {

	int[] nums = arrUpload();
		
	isPositive(nums);
	System.out.println();
	divisibleByTwoAndThree(nums);
	System.out.println();
	moreThanTenItems(nums);
	System.out.println();
	penultimateElement(nums);
	System.out.println();
	betweenZeroAndTwentyEight(nums);
	System.out.println();
	largestItemValueAndIndex(nums);
	System.out.println();
	smallestItemValueAndIndex(nums);
	System.out.println();
}

> Legisebb elem értéke és indexe:

```java
// g. Írd ki a legkisebb elem értékét és indexét!
private static void smallestItemValueAndIndex(int[] arr) {
	System.out.println("g. feladat:");

	int[] temp = new int[2];
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] < temp[0]) {
			temp[0] = arr[i];
			temp[1] = i;
		}
	}
	System.out.println("A legkisebb elem a tömbben: " + temp[0] + " és indexe: " + temp[1]);
}
```

> Legnagyobb elem értéke és indexe:

```java
// f. Írd ki a legnagyobb elem értékét és indexét!
private static void largestItemValueAndIndex(int[] arr) {
	System.out.println("f. feladat:");

	int[] temp = new int[2];
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > temp[0]) {
			temp[0] = arr[i];
			temp[1] = i;
		}
	}
	System.out.println("A legnagobb elem a tömbben: " + temp[0] + " és indexe: " + temp[1]);
}
```

> 0-29 index bekérés:

```java
// e. Kérj be a felhasználótól egy egész számot (0-29 között), majd írd ki a megadott indexen lévő elemet!
private static void betweenZeroAndTwentyEight(int[] arr) {
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("e. feladat:");

	try {
		System.out.print("Kérlek írj be egy számot 0 és 29 között: ");
		int index = Integer.parseInt(br.readLine());

		System.out.println("A(z) " + index + ". indexen lévő szám értéke: " + arr[index]);

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!\nCsak egész számokat adhatsz meg\n0 és 29 között!");
	}
}
```

> Utolsó előtti index értéke:

```java
// d. Melyik érték van az utolsó előtti helyen?
private static void penultimateElement(int[] arr) {
	System.out.println("d. feladat:");
	int num = arr[arr.length-2];
	System.out.println("Az utolsó előtti elem a tömbben: " + num);
}
```

> 10 feletti elemek a tömbben:

```java
// c. Hány db 10 feletti elem van a tömbben?
private static void moreThanTenItems(int[] arr) {
	System.out.println("c. feladat:");

	int count = 0;
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 10) {
			count++;
		}
	}
	System.out.println(count + " db 10 feletti elem található a tömbben!");
}
```

> hány darab 2-vel és 3-al osztható számok:

```java
// b. Hány db 2-vel és 3-mal is maradék nélkül osztható szám van tömbben?
private static void divisibleByTwoAndThree(int[] arr) {
	System.out.println("b. feladat:");

	int count = 0;
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] % 2 == 0 && arr[i] % 3 == 0 && arr[i] != 0) {
			count++;
		}
	}
	System.out.println("A tömbben " + count + " db 2-vel és 3-al is maradék nélkül osztható szám van.");
	/*
	int[] temp = new int[count];
	count = 0;
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] % 2 == 0 && arr[i] % 3 == 0 && arr[i] != 0) {
			temp[count] = arr[i];
			count++;
		}
	}
	for(int i = 0; i < temp.length; i++) {
		System.out.print(temp[i] + " ");
	}
	*/
}
```

> Hány darab pozitív szám:

```java
// a. Hány db pozitív szám van a tömbben?
private static void isPositive(int[] arr) {
	System.out.println("a. feladat:");

	int count = 0;
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] > 0) {
			count++;
		}
	}
	System.out.println("A tömbben " + count + " pozitív elem található.");
}
```

> Tömb feltöltés:

```java
private static int[] arrUpload() {
	Random r = new Random();
	int[] nums = new int[30];
	for(int i = 0; i < nums.length; i++) {
		//r.nextInt(max + 10) - 10
		nums[i] = r.nextInt(15 + 10)-10;
		//System.out.print(nums[i] + " ");
	}
	//System.out.println();
	return nums;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---