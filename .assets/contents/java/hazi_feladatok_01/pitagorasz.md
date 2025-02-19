
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (pitagorasz)

> Írjunk programot a Pitagorasz-tétel alkalmazására!
> A program kérje be egy derékszögű háromszög két befogóját,
> és számítsa ki az átfogó hosszát!

> Main:

```java
public static void main(String[] args) {

  /**
   * @param a, b
   * @return Math.pow(a,2)+Math.pow(b,2) = Math.pow(c,2)
  */

  Double a;
	Double b;
	Double result;
	Scanner input = new Scanner(System.in);

	System.out.print("Kérem adja meg az \"A\" befogó összegét: ");
	a = input.nextDouble();
	System.out.println();

	System.out.print("Kérem adja meg az \"B\" befogó összegét: ");
	b = input.nextDouble();
	System.out.println();

	result = Math.sqrt(Math.pow(a, 2) + Math.pow(b, 2));
		
	System.out.println("A háromszög átfogójának hossza: " + result);
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
