

# (tortszamok_hasonlit)

> Készíts alkalmazást, amely bekér két tört számot, 
> majd eldönti, hogy melyik a kisebb/nagyobb,
> esetleg egyenlő –e a két szám!

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	System.out.println("Írj be két törtszámot: ");
	try {
		System.out.print(" - első szám: ");
		Double num1 = Double.parseDouble(br.readLine());
		System.out.print(" - második szám: ");
		Double num2 = Double.parseDouble(br.readLine());

		if(num1 > num2) {
			System.out.println(num1 + " nagyobb, mint " + num2);
		} else {
			System.out.println(num2 + " nagyobb, mint " + num1);
		}

		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}
}
```

