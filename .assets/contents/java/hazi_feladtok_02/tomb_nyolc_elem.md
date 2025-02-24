
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (tomb_nyolc_elem)

> Tölts fel egy 8 elemű tömböt a felhasználótól érkező adatokkal! 
> Írd ki az adatokat egymás mellé!
>
> a. Írd ki a párosakat és indexeiket!
> b. Írd ki az utolsó elem négyzetét!
> c. Írd ki az első 2 elem átlagát!
> d. Írd ki az utolsó 3 elem összegét!
> e. Írd ki az első és második elem különbségét!
> f. Kérj be a felhasználótól egy indexet, és egy hatványkitevőt. 
> A megadott indexen lévő elemet emeld a megfelelő hatványra, majd írd ki!

```java
public static void main(String[] args) {

	int[] arr = ArrUpload();

	Task_1(arr);
	System.out.println();
	Task_2(arr);
	System.out.println();
	Task_3(arr);
	System.out.println();
	Task_4(arr);
	System.out.println();
	Task_5(arr);
	System.out.println();
	Task_6(arr);
	System.out.println();
}
```

> tömbfeltöltés

```java
private static int[] ArrUpload() {
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	int[] nums = new int[8];

	System.out.println("Kérlek írj be 8 egész számot");
	for(int i = 0; i < nums.length; i++) {
		try {
			System.out.print((i+1) + ".szám: ");
			nums[i] = Integer.parseInt(br.readLine());
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			// e.printStackTrace();
			System.out.println("Hibás adatbevitel!");
		}
	}
	return nums;
}
```	

> a. Írd ki a párosakat és indexeiket!

```java
private static void Task_1(int[] arr) {

	System.out.println("1. Feladat: ");

	for(int i = 0; i < arr.length; i++) {
		if(arr[i] % 2 == 0) {
			System.out.println("Szám: " + arr[i] + " és az indexe: " + i);
		}
	}		
}
```
	
> b. Írd ki az utolsó elem négyzetét!

```java
private static void Task_2(int[] arr) {

	System.out.println("2. Feladat: ");

	int last_num = arr[arr.length-1];
	System.out.println("Az utolsó szám: " + last_num + " négyzete: " + Math.pow(last_num, 2));
}
```	

> c. Írd ki az első 2 elem átlagát!

```java
private static void Task_3(int [] arr) {

	int average = (arr[0] + arr[1]) / 2;

	System.out.println("3. Feladat: ");
	System.out.println("Első két elem átlaga: " + average);
}
```
	
> d. Írd ki az utolsó 3 elem összegét!

```java
private static void Task_4(int[] arr) {

	int average = arr[arr.length-1] + arr[arr.length-2] + arr[arr.length-3];

	System.out.println("4. Feladat: ");
	System.out.println(arr[arr.length-1]);
	System.out.println(arr[arr.length-2]);
	System.out.println(arr[arr.length-3]);
	System.out.println(average);
}
```
	
> e. Írd ki az első és második elem különbségét!

```java
private static void Task_5(int[] arr) {

	int num1 = arr[0];
	int num2 = arr[1];

	System.out.println("5. Feladat: ");

	if(num1 > num2) {
		System.out.println("A két elem különbsége: " + (num1-num2));
	} else {
		System.out.println("A két elem különbsége: " + (num2-num1));
	}
}
```

> f. Kérj be a felhasználótól egy indexet, és egy hatványkitevőt. 
> A megadott indexen lévő elemet emeld a megfelelő hatványra, majd írd ki!

```java
private static void Task_6(int[] arr) {
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("6. Feladat: ");

	try {
		System.out.print("Kérem adjon meg egy számot 0-7-ig, mely a tömmben lévő szám indexe: ");
		int num = Integer.parseInt(br.readLine());
		System.out.print("Kérem adjon meg egy számot, a szám hatványkitevőjének: ");
		int hatvanyki = Integer.parseInt(br.readLine());

		System.out.println("A " + num + ". indexen lévő szám: " + arr[num] + " szám " + hatvanyki + ". hatványának eredménye: " + Math.pow(arr[num], hatvanyki));

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	} catch(ArrayIndexOutOfBoundsException e) {
		System.out.println("A tömb indexeinek értékén kívül nem tudsz megadni értéket!");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

