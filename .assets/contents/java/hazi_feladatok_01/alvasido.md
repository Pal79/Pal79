
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (alvasido)

> Olvasd be, hogy a felhasználó átlagosan hány órát alszik naponta 
> (egész számként), és jellemezd az alvásidejét a következő módon: 
> - 0-6 óráig kevés, 
> - 7-9 óráig átlagos, 
> - 10-12 óráig sok, 
> - 13-24 óráig nagyon sok!

> Main:

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		try {
			System.out.print("Naponta hány órát alszol? (egész számot adj meg): ");
			Integer hours = Integer.parseInt(br.readLine());
			
			if(hours == 0 || hours <= 6) {
				System.out.println("kevés");
			} else if(hours == 7 || hours <= 9) {
				System.out.println("átlagos");
			} else if(hours == 10 || hours <= 12) {
				System.out.println("sok");
			} else if(hours == 13 || hours <= 24) {
				System.out.println("nagyon sok");
			} else {
				System.out.println("Ilyen létezik egyáltalán?");
			}
			
			br.close();
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			//e.printStackTrace();
			System.out.println("Hibás adatbevitel!");
		}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
