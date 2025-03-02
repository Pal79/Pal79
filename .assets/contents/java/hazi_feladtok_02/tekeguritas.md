
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Készítsünk tekegurításokat szimuláló alkalmazást! 
> 10 gurítás van, 2 játékos, ledönthető bábuk száma 0-10. Határozzuk meg a következőket:
> - a. Melyik játékos hány pontot ért el?
> - b. Melyik játékos győzött, hány ponttal?
> - c. A játék felénél ki állt nyerésre?
> - d. Ki hányszor tarolt?
> - e. Az nyert, aki többször tarolt?

> Main:

```java
public static void main(String[] args) {

	int[] player1 = bowling();
	int[] player2 = bowling();

	whichPlayerHowManyPoints(player1, player2);
	System.out.println();
	whichPlayerWonByHowManyPoints(player1, player2);
	System.out.println();
	halfwayThroughTheGgameWhoStoodToWin(player1, player2);
	System.out.println();
	whoHowManyTimesOverturned(player1, player2);
	System.out.println();
	theOneWhoWinsMoreThanOverturned(player1, player2);
	System.out.println();
}
```

> az nyert aki többször tarolt?

```java
// e. Az nyert, aki többször tarolt?
private static void theOneWhoWinsMoreThanOverturned(int[] arr1, int[] arr2) {
	System.out.println("e. feladat:");

	int overturn1 = 0;
	int overturn2 = 0;
	int points1 = 0;
	int points2 = 0;

	for(int i = 0; i < arr1.length; i++) {
		if(arr1[i] == 10) {
			overturn1++;
		}
		if(arr2[i] == 10) {
			overturn2++;
		}
		points1 += arr1[i];
		points2 += arr2[i];
	}

	if(overturn1 > overturn2) {
		if(points1 > points2) {
			System.out.println("Az egyes játékos nyert, mert ő többször tarolt.");
		} else {
			System.out.println("A kettes játékos nyert, pedig kevesebbszer tarolt.");
		}
	} else if(overturn2 > overturn1) {
		if(points2 > points1) {
			System.out.println("A kettes játékos nyert, mert ő többször tarolt.");
		} else {
			System.out.println("Az egyes játékos nyert, pedig kevesebbszer tarolt.");
		}
	} else if(overturn1 == 0 && overturn2 == 0) {
		System.out.println("Egyikük sem tarolt, így az nem volt döntő szerep a meccsen.");
	} else if(overturn1 == overturn2) {
		System.out.println("Mindketten ugyanannyiszor taroltak, így az nem volt döntő szerep a meccsen.");
	}	
}
```

> ki hányszor tarolt?

```java
// d. Ki hányszor tarolt?
private static void whoHowManyTimesOverturned(int[] arr1, int[] arr2) {
	System.out.println("d. feladat:");

	int count1 = 0;
	int count2 = 0;

	for(int i = 0; i < arr1.length; i++) {
		if(arr1[i] == 10) {
			count1++;
		}
		if(arr2[i] == 10) {
			count2++;
		}
	}
	System.out.println("Az egyes játékos tarolásai: " + count1);
	System.out.println("A kettes játékos tarolásai: " + count2);
}
```

> játék felénél ki volt a nyertes?

```java
// c. A játék felénél ki állt nyerésre?
private static void halfwayThroughTheGgameWhoStoodToWin(int[] arr1, int[] arr2) {
	System.out.println("c. feladat:");

	int count1 = 0;
	int count2 = 0;

	for(int i = 0; i < 4; i++) {
		count1 += arr1[i];
		count2 += arr2[i];
	}

	if(count1 > count2) {
		System.out.println("A játék felénél az egyes játékos állt nyerésre.");
	} else {
		System.out.println("A játék felénél a kettes játékos állt nyerésre.");
	}
}
```

> ki volt a nyertes és hány ponttal?

```java
// b. Melyik játékos győzött, hány ponttal?
private static void whichPlayerWonByHowManyPoints(int[] arr1, int[] arr2) {

	System.out.println("b. feladat:");

	int count1 = 0;
	int count2 = 0;
	int difference;

	for(int i = 0; i < arr1.length; i++) {
		count1 += arr1[i];
		count2 += arr2[i];
	}

	if(count1 > count2) {
		difference = count1 - count2;
		System.out.println("Az egyes játékos nyerte a meccset " + difference + " ponttal.");
	} else if(count2 > count1) {
		difference = count2 - count1;
		System.out.println("A kettes játékos nyerte a meccset " + difference + " ponttal.");
	} else {
		System.out.println("A játék végeredménye döntetlen lett.");
	}
}
```

> ki hány pontot ért el?

```java
// a. Melyik játékos hány pontot ért el?
private static void whichPlayerHowManyPoints(int[] arr1, int[] arr2) {

	System.out.println("a. feladat:");

	int count1 = 0;
	int count2 = 0;

	for(int i = 0; i < arr1.length; i++) {
		count1 += arr1[i];
		count2 += arr2[i];
	}
	System.out.println("Az egyes játékos " + count1 + " pontot ért el.");
	System.out.println("A kettes játékos " + count2 + " pontot ért el.");
}
```

> gurítás(ok):

```java
private static int[] bowling() {
	Random r = new Random();
	int[] rollings = new int[10];
	for(int i = 0; i < rollings.length; i++) {
		rollings[i] = r.nextInt(10 - 0 + 1) + 0;
		//System.out.print(rollings[i] + " ");
	}
	return rollings;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---