
# (euro_ft)

> Programunk kérje be az Euró árfolyamát (1 € hány Ft-ot ér), 
> majd azt, hogy hány eurót akarunk átváltani Ft-ba, 
> majd írja ki, hogy hány Ft az átváltott euró. 

> Main:

```java
public static void main(String[] args) {
  Double euro, change;
  Integer result;
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  try {
    System.out.print("Írja be az euro árfolyamát: ");
    euro = Double.parseDouble(br.readLine());
    System.out.print("Írja be, hogy hány euro-t szeretne átváltani forintba: ");
    change = Double.parseDouble(br.readLine());
			
    result = (int)(euro * change);
			
    System.out.println("Az átváltandó " + change + " euro: " + result + " forint.");
			
    br.close();
  } catch (NumberFormatException | IOException e) {
    // TODO Auto-generated catch block
    // e.printStackTrace();
    System.out.println("Hibás adatbevitel!");
  }
}
```
