
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (tavolsag)

> Írj programot, 
> amely bekéri két pont koordinátáit,
>  majd kiszámolja azok távolságát! 

> Main:

```
public static void main(String[] args) {

  /**
   * @param x1, x2, y1, y2
   * @return sqrt( (x1 - x2) * (x1 - x2) + (y2 - y1) * (y2 - y1) )
   */

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Add meg a koordinátákat: ");
	try {
		System.out.print("X1: ");
		Double x1 = Double.parseDouble(br.readLine());
		System.out.print("X2: ");
		Double x2 = Double.parseDouble(br.readLine());
		System.out.print("Y1: ");
		Double y1 = Double.parseDouble(br.readLine());
		System.out.print("Y2: ");
		Double y2 = Double.parseDouble(br.readLine());

		System.out.println("A koordináták közti távolság: " + Range(x1, x2, y1, y2));

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

> Range:

```java
public static Double Range(Double x1, Double x2, Double y1, Double y2) {
	return Math.sqrt((x1-x2)*(x1-x2) + (y2-y1)*(y2-y1));
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
