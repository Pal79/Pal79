
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# tomb_hatvany_kiir

---

> Készíts metódust TombElemHatvanyKiir néven, amelynek nincsen visszatérési értéke.
> Két db bemeneti paramétere van, az egész számokat tartalmazó tömb és egy egész szám 
> (hányadik hatványra emeljük). 
> Írja ki egymás mellé szóközzel elválasztva a tömb elemeinek megadott hatványát!
> Teszteljük a metódusunkat a felhasználótól érkező adatokkal.
> - (tomb_hatvany_kiir)

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	int[] nums = {1,2,3,4,5};

	try {
		System.out.print("Adjon meg egy számot: ");
		int exponent = Integer.parseInt(br.readLine());

		System.out.print("A tömb elemei a " + exponent + ". hatványon: ");
		TombElemHatvanyKiir(nums, exponent);
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> TombElemHatvanyKiir:

```java
private static void TombElemHatvanyKiir(int[] arr, int exponent) {
	for(int item: arr) {
		System.out.print(Math.pow(item, exponent) + " ");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---