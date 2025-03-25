
```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	boolean is_on = true;

	try {
		while (is_on) {
			System.out.println("Válassz az alábbi lehetőségek közül: ");
			System.out.println(" - Számok megadása (1): ");
			System.out.println(" - Kilépés (0): ");
			int choose = Integer.parseInt(br.readLine());

			if(choose == 0) {
				is_on = false;
				System.out.println("A program kilépett!");
			} else {
				System.out.print("Add meg az első számot: ");
				int num1 = Integer.parseInt(br.readLine());
				System.out.print("Add meg a második számot: ");
				int num2 = Integer.parseInt(br.readLine());

				OperationDisplay(num1, num2);
				System.out.print("tehát a kapott eredméy: ");
				if(IsDoubleOrIsInteger(num1, num2) == true) {
					System.out.println("négyzetszám.");
				} else {
					System.out.println("nem négyzetszám.");
				}
				is_on = true;
			}
			System.out.println();
		}
		br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
	}		
}
```

```java
private static void OperationDisplay(double num1, double num2) {
	double addition = Math.pow(num1, 2) + Math.pow(num2, 2);
	double result = Math.sqrt(Math.pow(num1, 2) + Math.pow(num2, 2));

	System.out.println(Math.pow(num1, 2) + " + " + Math.pow(num2, 2) + " = " + addition);
	System.out.println("Az eredmény gyök alatt: " + result);
}
```

```java
private static boolean IsDoubleOrIsInteger(double num1, double num2) {
	double result = Math.sqrt((Math.pow(num1, 2) + Math.pow(num2, 2)));

	if(result % 1 == 0) {
		return true;
	} else {
		return false;
	}
}
```