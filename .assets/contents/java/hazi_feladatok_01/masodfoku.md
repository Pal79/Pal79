
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (masodfoku)

> Készítsünk egy másodfokú egyenlet megoldó alkalmazást! 
> Kérjük be a, b és c értékét, 
> majd számoljuk ki x1-et és x2-t, ahol:

> Main:

```java
public static void main(String[] args) {
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
	System.out.println("Kérlek add meg \"a\", \"b\" és \"c\" értékét.");
	try {
		System.out.print("\"a\" értéke: ");
		Double a = Double.parseDouble(br.readLine());
		
		System.out.print("\"b\" értéke: ");
		Double b = Double.parseDouble(br.readLine());
		
		System.out.print("\"c\" értéke: ");
		Double c = Double.parseDouble(br.readLine());		
			
	if(QuadraticEquation_1(a, b, c).isNaN()) {
			System.out.println("Az egyenletnek nincs valós gyöke");
		} else {
			System.out.println(QuadraticEquation_1(a, b, c));
		}
			
	if(QuadraticEquation_1(a, b, c).isNaN()) {
				System.out.println("Az egyenletnek nincs valós gyöke");
		} else {
			System.out.println(QuadraticEquation_2(a, b, c));
		}
			
	br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		//e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}		
}
```

> X1:

```java
/**
 * @param a, b, c
 * @return x1 = -b + sqrt( pow(b, 2) - 4 * a * c ) / 2 * a
 */
public static Double QuadraticEquation_1(Double a, Double b, Double c) {
	return (-b + Math.sqrt(Math.pow(b, 2) - 4 * a * c)) / (2 * a);
}
```

> X2:

```java
/**
 * @param a, b, c
 * @return x2 = -b - sqrt( pow(b, 2) - 4 * a * c ) / 2 * a
 */	
public static Double QuadraticEquation_2(Double a, Double b, Double c) {
	return (-b - Math.sqrt(Math.pow(b, 2) - 4 * a * c)) / (2 * a);
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
