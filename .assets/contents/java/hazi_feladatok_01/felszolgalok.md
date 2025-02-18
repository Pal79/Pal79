
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (felszolgalok)

> A gyorsétterem felszolgálói hetente kapnak fizetést. 
> Mindenki az alapján hány napot dolgozott a héten. 
> Bérük 8.000 Ft / nap. Kérjük be a felszolgáló nevét 
> és hány napon dolgozott a héten, 
> majd írjuk ki a heti fizetését. 

> Main:

```java
public static void main(String[] args) {
		
  String name;
  Integer days, pay;
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  try {
    System.out.print("Adja meg a dolgozó nevét: ");
    name = br.readLine();
    System.out.print("Ledolgozott napok: ");
    days = Integer.parseInt(br.readLine());
			
    pay = days * 8000;
			
    System.out.println("A dolgozó " + name + " heti bére: " + pay + " forint.");

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
