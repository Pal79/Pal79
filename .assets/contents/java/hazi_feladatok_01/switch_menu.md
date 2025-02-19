
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (switch_menu)

> Készíts min. 5 menüpontból álló menüt switch-case szerkezettel! 
> (pld. az 1-est lenyomva írja ki: "Az első menüpontot választotta!”, 
> a 2-est lenyomva írja ki: "A második menüpontot választotta!" stb.) 

> Main:

```java
public static void main(String[] args) {

	Integer menu;

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Írjon be egy menüpontot (1-5): ");
		menu = Integer.parseInt(br.readLine());

		switch(menu) {
			case 1:
				System.out.println("Az első menüpontot váasztotta!");
			break;
  		case 2:
  			System.out.println("A kettes menüpontot váasztotta!");
			break;
			case 3:
				System.out.println("A hármas menüpontot váasztotta!");
			break;
			case 4:
				System.out.println("A négyes menüpontot váasztotta!");
			break;
			case 5:
				System.out.println("Az ötös menüpontot váasztotta!");
			break;
			default:
				System.out.println("Hibás adatbevitel!");
		}
    br.close();
	} catch (NumberFormatException | IOException e) {
		// TODO Auto-generated catch block
		//e.printStackTrace();
		System.out.println("Hibás adatbevitel!");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
