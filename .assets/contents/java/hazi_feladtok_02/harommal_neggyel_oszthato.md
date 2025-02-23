
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Kérj be a felhasználótól egész számokat mindaddig, 
> amíg a megadott szám nem osztható 3-mal és 4-gyel maradék nélkül!

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
	Boolean is_on = true;

	while(is_on) {
		System.out.print("Adj meg egy egész számot: ");
		Integer num;
		try {
			num = Integer.parseInt(br.readLine());

			if(num % 4 == 0 && num % 3 == 0) {
				System.out.println("A megadott szám " + num + " osztható 3-al és 4-el, maradék nélkül.");
				is_on = false;
			}
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			// e.printStackTrace();
			System.out.println("Hibás adatbevitel!");
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

