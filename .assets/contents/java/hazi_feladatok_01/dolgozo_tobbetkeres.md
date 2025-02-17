
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (dolgozo_tobbetkeres)

> Kérd be két dolgozó nevét, 
> beosztását és fizetését, 
> majd írd ki a többet kereső munkavállaló minden adatát egymás mellé! 
> Lehetséges, hogy ugyanannyit keresnek, 
> ebben az esetben azt írd ki: „Fizetésük egyenlő.”! 

```java
public static void main(String[] args) {
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	String worker_1_name, worker_2_name, worker_1_post, worker_2_post;
	Integer worker_1_payment, worker_2_payment;
		
	System.out.println("Add meg a dolgozók nevét, beosztását és fizetését.");
		
	try {
		System.out.print("1. dolgozó neve: ");
		worker_1_name = br.readLine();
		System.out.print("1. dolgozó beosztása: ");
		worker_1_post = br.readLine();
		System.out.print("1. dolgozó fizetése: ");
		worker_1_payment = Integer.parseInt(br.readLine());

		System.out.print("2. dolgozó neve: ");
		worker_2_name = br.readLine();
		System.out.print("2. dolgozó beosztása: ");
		worker_2_post = br.readLine();
		System.out.print("2. dolgozó fizetése: ");
		worker_2_payment = Integer.parseInt(br.readLine());

	if(worker_1_payment > worker_2_payment) {
		System.out.println("Dolgozó neve: " + worker_1_name);
		System.out.println("Dolgozó beosztása: " + worker_1_post);
		System.out.println("Dolgozó fizetése: " + worker_1_payment + " Ft");
	} else if(worker_1_payment < worker_2_payment) {
		System.out.println("Dolgozó neve: " + worker_2_name);
		System.out.println("Dolgozó beosztása: " + worker_2_post);
		System.out.println("Dolgozó fizetése: " + worker_2_payment + " Ft");
	} else {
		System.out.println("Fizetésük egyenlő.");
	} catch (IOException e) {
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
