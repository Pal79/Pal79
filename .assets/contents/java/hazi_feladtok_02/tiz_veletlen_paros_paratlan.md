
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (tiz_veletlen_paros_paratlan)

> Hozz létre 10 db véletlen számot [5, 30] közötti tartományban,
> majd határozzuk meg, hogy az elemek összege páros vagy páratlan szám!

> Main:

```java
public static void main(String[] args) {

	Random r = new Random();
	int nums_value = 0;

	for(int i = 0; i < 10; i++) {
		int num = r.nextInt(30-5+1)+5;
		nums_value += num;
	}

	if(nums_value % 2 == 0) {
		System.out.println(nums_value + " - páros");
	} else {
		System.out.println(nums_value + " - páratlan");
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
