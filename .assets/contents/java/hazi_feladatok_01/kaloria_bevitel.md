
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (kaloria_bevitel)

> Kérd be a felhasználó napi kalória-bevitelét, 
> majd döntsd el, hogy megfelelően táplálkozott –e
> (megfelelő bevitel 2500 kcal-3500 kcal között van)! 

> Main:

```java
public static void main(String[] args) {
		
  Scanner input = new Scanner(System.in);
  Integer calorie;
		
  System.out.print("Írd be, hogy napi hány kalóriát fogyasztasz: ");
  calorie = input.nextInt();
		
  if(calorie >= 2500 && calorie <=3000) {
    System.out.println("Ön megfelelő mennyiségű kalóriát visz be.");
  } else if(calorie < 2500) {
    System.out.println("Ön kevés mennyiségű kalóriát visz be.");
  } else {
    System.out.println("Ön sok mennyiségű kalóriát visz be.");
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
