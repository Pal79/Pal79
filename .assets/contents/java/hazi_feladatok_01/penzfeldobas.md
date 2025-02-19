
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (penzfeldobas)

> Írjuk ki 3 db pénzfeldobás eredményét 
> (fej vagy írás véletlenszerűen, szövegesen jelenjen meg)!

> Main:

```java
public static void main(String[] args) {
		
	Random r = new Random();
	//System.out.println(throwing);
	for(int i=0; i<3; i++) {
		int throwing = r.nextInt(1-0+1)+0;
		if(throwing == 0) {
			System.out.println("fej");
		} else {
			System.out.println("írás");
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
