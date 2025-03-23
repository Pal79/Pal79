
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# tomb_rendezes

---

		/*
		 * Generáljunk le a felhasználó által meghatározott intervallumon belüli véletlen számokat. 
		 * A darabszámot szintén a felhasználó adja meg! (tomb_rendezes)
		 * 
		 * a. Hozzunk létre egy fájlt szamok.txt néven!
		 * b. Írjuk ki a számokat a fájl első sorába a következő formátumban: A tömb elemei: 43 52 66 3
		 * c. A második sorába írjuk ki a tömb elemeit rendezett formátumban:
		 * A tömb elemei rendezve: 3 43 52 66
		 * d. A páros elemeket egy külön fájlba is helyezzük el  paros_szamok.txt
		 */

> Main:

```java
public static void main(String[] args) throws NumberFormatException, IOException {

	int[] nums = arrUpload();

	ContentUploadToSzamokTxt(nums);
	ContentUploadToParosSzamokTxt(nums);
}
```

> páros számok feltöltése fájlba:

```java
private static void ContentUploadToParosSzamokTxt(int[] arr) {
	try {
		FileOutputStream fs = new FileOutputStream("paros_szamok.txt");
		OutputStreamWriter osw = new OutputStreamWriter(fs, "UTF-8");

		for(int item: arr) {
			if(item % 2 == 0) {
				osw.write(item + " ");
			}
		}

		osw.close();
		fs.close();

		System.out.println("Páros számok feltöltve!");
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

> számok feltöltése fájlba:

```java
private static void ContentUploadToSzamokTxt(int[] arr) {
	try {
		FileOutputStream fs = new FileOutputStream("szamok.txt");
		OutputStreamWriter osw = new OutputStreamWriter(fs, "UTF-8");

		osw.write(String.valueOf("A tömb elemei: "));
		for(int item: arr) {
			osw.write(String.valueOf(item + " "));
		}
		osw.write("\n");

		osw.write("A tömb elemei rendezve: ");

		int temp;
		for(int i = 0; i < arr.length; i++) {
			for(int j = 0; j < arr.length-i-1; j++) {
				if(arr[j] > arr[j+1]) {
					temp = arr[j];
					arr[j] = arr[j+1];
					arr[j+1] = temp;
				}
			}
		}
		for(int item: arr) {
			osw.write(item + " ");
		}

		osw.close();
		fs.close();
	} catch (IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
	System.out.println("A fájl létrehozva és az adatok feltöltve!");
}
```

> tömbfeltöltés:

```java
private static int[] arrUpload() throws NumberFormatException, IOException {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.print("Kérem adja meg a hány számot szeretne a tömbbe feltölteni: ");
	int arr_size = Integer.parseInt(br.readLine());

	int[] nums = new int[arr_size];

	System.out.println("Adja meg a számokat: ");
	for(int i = 0; i < nums.length; i++) {
		System.out.print((i+1) + ". szám: ");
		int num = Integer.parseInt(br.readLine());
		nums[i] = num;
	}
	return nums;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---