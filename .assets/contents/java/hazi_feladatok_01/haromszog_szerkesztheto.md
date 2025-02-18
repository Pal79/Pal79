
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (haromszog_szerkesztheto)

> Kérd be a háromszög három oldalát és döntsd el, 
> hogy szerkeszthető –e a háromszög!

> Main:
 
```java
public static void main(String[] args) {
  /**
	 * @return a + b > c
	 * @return a + c > b
	 * @return b + c > a
	 */
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  Double a,b,c;
		
  System.out.println("Kérlek add meg a háromszög oldalainak hosszát és megtudod, hogy szerkeszthető e.");
  try {
    System.out.print("a oldal: ");
    a = Double.parseDouble(br.readLine());

    System.out.print("b oldal: ");
    b = Double.parseDouble(br.readLine());

    System.out.print("c oldal: ");
    c = Double.parseDouble(br.readLine());
			
    if((a+b>c) && (a+c>b) && (b+c>a)) {
      System.out.println("A háromszög szerkeszthető.");
    } else {
      System.out.println("A háromszög nem szerkeszthető.");
    }
			
    br.close();
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
