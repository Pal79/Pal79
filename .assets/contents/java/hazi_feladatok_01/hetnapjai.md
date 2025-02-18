
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (hetnapjai)

> Switch-case szerkezettel készíts el a következő programot! 
> Kérjük be egy nap sorszámát (1..7) numerikus formában, 
> és írjuk ki a nap megnevezését a képernyőre 
> (hétfő, kedd, ..., vasárnap).
> Amennyiben a beírt sorszám nem 1..7 közötti szám, 
> úgy a „Hibás adat!” kiírás jelenjen meg.

> Main:

```java
public static void main(String[] args) {
		
  Integer day;
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  try {
    System.out.print("Kérlek add meg egy nap sorszámát (1-7): ");
    day = Integer.parseInt(br.readLine());
			
    switch(day) {
      case 1:
        System.out.println("Hétfő");
      break;
      case 2:
        System.out.println("Kedd");
      break;
      case 3:
        System.out.println("Szerda");
      break;
      case 4:
        System.out.println("Csütörtök");
      break;
      case 5:
        System.out.println("Péntek");
      break;
      case 6:
        System.out.println("Szombat");
      break;
      case 7:
        System.out.println("Vasárnap");
      break;
      default:
        System.out.println("Hibás adat!");
      break;
    }
    br.close();
  } catch (NumberFormatException | IOException e) {
    // TODO Auto-generated catch block
    //e.printStackTrace();
    System.out.println("Hibás adat!");
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
