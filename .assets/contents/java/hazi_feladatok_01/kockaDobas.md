
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (kockaDobas)

```java
/**
 * Kérdezzük meg a felhasználót hány kockával szeretne dobni 
 * (hagyományos 6 oldalú), 
 * majd írjunk ki 5 lehetséges dobás eredményét a megadott kockaszámmal! 
 */

public static void main(String[] args) {

  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
  Random r = new Random();

  try {
    System.out.print("Hány kockával szeretnél dobni? ");
    int cubePieces = Integer.parseInt(br.readLine());

    for(int i = 0; i < 5; i++) {
      System.out.println((i+1) + ". dobás: ");
        for(int j = 0; j < cubePieces; j++) {
          int throwing = r.nextInt(6)+1;
          System.out.println(" - " + (j + 1) + ".kocka: " + throwing + ", ");
        }
        System.out.println();
    }
  } catch (NumberFormatException | IOException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
