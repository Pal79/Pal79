
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (dolgozo_fizetes_atlag)

> Kérd be a dolgozó első féléves fizetését havonta 
> (januártól - júniusig), majd írd ki az átlagfizetését, 
> és hogy mennyit keresett összesen eddig!

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	int employee_payments[] = new int[6];
	int all_payments = 0;
	int average_payments = 0;
	String half_year[] = {"Január", "Február", "Március", "Április", "Május", "Június"};

	try {
		for(int i = 0; i < employee_payments.length; i++) {
			System.out.print(half_year[i] + "i fizetés: ");
			employee_payments[i] = Integer.parseInt(br.readLine());
			all_payments += employee_payments[i];
		}
		br.close();

		System.out.println("A dolgozó átlagfizetése: " + (all_payments/6) + " Ft.\nÖsszes fizetése az első fél évben: " + all_payments + " Ft.");

	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		// e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
