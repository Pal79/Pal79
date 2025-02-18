
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (kor_ker_ter)

> Írjunk programot, amely bekéri egy kör sugarát,
> majd kiszámolja a kör kerületét és területét!

> Main:

```java
/**
 * @param r
 * @return K = 2 * r * pi
 * @return T = pow(r,2) * pi
 */
public static void main(String[] args) {
		
  Scanner input = new Scanner(System.in);
  Double radius, areaOfACircle, circumferenceOfACircle;
		
  System.out.print("Add meg a kör sugarát: ");
  radius = input.nextDouble();
		
  areaOfACircle = 2 * radius * Math.PI;
  circumferenceOfACircle = Math.pow(radius, 2) * Math.PI;
		
  System.out.println("A kör kerülete: " + areaOfACircle);
  System.out.println("A kör területe: " + circumferenceOfACircle);
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
