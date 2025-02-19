
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (teglap_ter_ker)

> Kérd be a téglalap két oldalát és írd ki a kerületét, területét!

> Main:

```java
public static void main(String[] args) {

  /**
   * @return T = a * b = xcm
   * @return K = 2(a+b) = xcm^2
   * d = sqrt(pow(a,2)+pow(b,2))
   */

	Scanner input = new Scanner(System.in);
	Double area, perimeter, diameter;

	System.out.print("Add meg a téglalap \"A\" oldalát: ");
	Double a = input.nextDouble();
	System.out.print("Add meg a téglalap \"B\" oldalát: ");
	Double b = input.nextDouble();

	area = a*b;
	perimeter = 2*(a+b);
	diameter = Math.sqrt(Math.pow(a, 2)+Math.pow(b, 2));

	System.out.println();

	System.out.println("A téglalap területe: " + area);
	System.out.println("A téglalap kerülete: " + perimeter);
	System.out.println("A téglalap átmérője: " + diameter);
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
