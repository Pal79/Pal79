
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Hozz létre egy tömböt, amely a következő értékeket tárolja: 
> ’a’, ’h’, ’r’, ’t’, ’z’, ’e’, ’v’
> - a. Írd ki a tömb elemeit egymás mellé szóközzel elválasztva!
> - b. Melyik indexeken található magánhangzó?
> - c. Ellenőrizd, hogy szerepel -e a tömbben a ’z’ karakter?

> Main:

```java
public static void main(String[] args) {

	char[] characters = {'a', 'h', 'r', 't', 'z', 'e', 'v'};

	arrWriteOut(characters);
	System.out.println("\n");
	chekZ(characters);
	System.out.println("\n");
	whichIndexVocalorAlveloar(characters);
}
```

> Tömb kiírás:

```java
// a. Írd ki a tömb elemeit egymás mellé szóközzel elválasztva!
private static void arrWriteOut(char[] arr) {
	System.out.println("a feladat: ");
	for(int i = 0; i < arr.length; i++) {
		System.out.print(arr[i] + " ");
	}
}
```

> Magánhangzó keresés, index kiírás

```java
// b. Melyik indexeken található magánhangzó?
private static void whichIndexVocalorAlveloar(char[] arr) {

	char[] arr2 = {'e','u','i','o','a'};
	char[] temp;

	boolean is_in = false;
	System.out.println("b feladat: ");
	System.out.print("Magánhangzó található a(z): ");
	for(int i = 0; i < arr.length; i++) {
		for(char chars : arr2) {
			if(arr[i] == chars) {
				System.out.print(i + ". ");
			}
    	}
	}
	System.out.println("indexen.");	
}
```

> 'z' karakter keresése:

```java
// c. Ellenőrizd, hogy szerepel -e a tömbben a ’z’ karakter?
private static void chekZ(char[] arr) {
	System.out.println("c feladat: ");
	for(int i = 0; i < arr.length; i++) {
		if(arr[i] == 'z') {
			System.out.println("A tömbben van \"z\" karakter, a(z) " + i + ". indexen");
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
