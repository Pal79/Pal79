
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (felnott_e)

> Kérjük be a felhasználó életkorát, 
> majd döntsük el, 
> hogy felnőtt –e (18 éves kortól már felnőtt)!

> Main:

```java
public static void main(String[] args) {
		
  Scanner input = new Scanner(System.in);
		
  System.out.print("Kérlek add meg az életkorod: ");
  Integer age = input.nextInt();
		
  if(age < 18) {
    System.out.println("Még nem vagy felnőtt");
  } else {
    System.out.println("Felnőtt vagy");
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
