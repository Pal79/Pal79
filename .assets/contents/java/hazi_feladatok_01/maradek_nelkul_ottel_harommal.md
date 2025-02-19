
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (maradek_nelkul_ottel_harommal)

> Kérj be két számot, majd döntsd el,
> hogy összegük osztható –e 5-tel és 3-mal is maradék nélkül!

> Main:

```java
public static void main(String[] args) {
		
  Scanner input = new Scanner(System.in);
		
  System.out.print("Adj meg egy számot: ");
  Integer num = input.nextInt();
		
  if(num % 5 == 0 && num % 3 == 0) {
  	System.out.println("Az adott szám " + num + ", osztható 5-el és 3-al.");
  } else {
  	System.out.println("Az adott szám " + num + ", nem osztható 5-el és 3-al. ");
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
