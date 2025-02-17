
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (benzin_fogyasztas)

> Kérjük be két autó rendszámát és fogyasztását, 
> majd írjuk ki melyik rendszámú autónak több a fogyasztása, 
> esetleg egyenlő -e! 

> Main:

```java
public static void main(String[] args) {
		
  String rendszam1, rendszam2;
  Double fogyasztas1, fogyasztas2;
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  try {
    System.out.print("Add meg az első autó rendszámát: ");
    rendszam1 = br.readLine();
    System.out.print("Add meg az első autó fogyasztását: ");
    fogyasztas1 = Double.parseDouble(br.readLine());
			
    System.out.print("Add meg a második autó rendszámát: ");
    rendszam2 = br.readLine();
    System.out.print("Add meg a második autó fogyasztását: ");
    fogyasztas2 = Double.parseDouble(br.readLine());
			
    if(fogyasztas1 > fogyasztas2) {
      System.out.println("A " + rendszam1 + " rendszámú autó többet fogyaszt, mint a " + rendszam2 + " rendszámú autó.");
    } else if(fogyasztas1 < fogyasztas2) {
      System.out.println("A " + rendszam2 + " rendszámú autó többet fogyaszt, mint a " + rendszam1 + " rendszámú autó.");
    } else {
      System.out.println("A két autó fogyaszása egyenlő.");
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
