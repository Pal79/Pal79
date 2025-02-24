
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (szamok_amig_nem_het)

> Hozz létre véletlen számokat 1-10 között mindaddig amíg, 7-es nem lesz!

> Main:

```java
public static void main(String[] args) {

	Random r = new Random();
	int num = r.nextInt(10)+1;

	if(num == 7) {
		System.out.println("a program kilép, mert elértük a " + num + "-es számot");
	} else {
		System.out.println(num);
		num = r.nextInt(10)+1;
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

