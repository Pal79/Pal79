
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# ko_papir_ollo

---

		/*
		 * Készíts programot a kő-papír-olló játék szimulálására! 
		 * 
		 * (ko_papir_ollo)
		 */

> Main:

```java
public static void main(String[] args) {

	Random r = new Random();

	// rock = 0 - paper = 1 - scissors = 2
	int player1 = r.nextInt(2-0+1)+0;
	int player2 = r.nextInt(2-0+1)+0;

	RockPaperScissors(player1, player2);
}
```

> kő, papír, olló:

```java
private static void RockPaperScissors(int num1, int num2) {

	if(num1 == 0 && num2 == 0) {
		System.out.println("Mindkét játékos követ mutatott, így a játék döntetlen.");
	} else if(num1 == 0 && num2 == 1) {
		System.out.println("Az 1-es játékos követ, míg a 2-es játékos papírt mutatott, így a 2-es játékos nyert.");
	} else if(num1 == 0 && num2 == 2) {
		System.out.println("Az 1-es játékos követ, míg a 2-es játékos ollót mutatott, így az 1-es játékos nyert.");
	} else if(num1 == 1 && num2 == 0) {
		System.out.println("Az 1-es játékos papírt mutatott, míg a 2-es játékos követ, így az 1-es játékos nyert.");
	} else if(num1 == 1 && num2 == 1) {
    	System.out.println("Mindkét játékos papírt mutatott, így a játék döntetlen.");
	} else if(num1 == 1 && num2 == 2) {
		System.out.println("Az 1-es játékos papírt mutatott, míg a 2-es játékos ollót, így az 2-es játékos nyert.");
	} else if(num1 == 2 && num2 == 0) {
		System.out.println("Az 1-es játékos ollót mutatott, míg a 2-es játékos követ, így a 2-es játékos nyert.");
	} else if(num1 == 2 && num2 == 1) {
		System.out.println("Az 1-es játékos ollót mutatott, míg a 2-es játékos papírt, így az 1-es játékos nyert.");
	} else {
		System.out.println("Mindkét játékos ollót mutatott, így a játék döntetlen.");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---