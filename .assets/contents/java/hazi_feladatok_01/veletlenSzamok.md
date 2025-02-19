
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (veletlenSzamok)

> Hozz létre 12 db véletlen számot [10, 40] közötti tartományban, 
> majd írjuk ki a páros számok közül a 3-mal is oszthatóakat! 

> Main:

```java
public static void main(String[] args) {

	Random r = new Random();

	int[] nums = new int[12];

	for(int i=0; i<nums.length; i++) {
		nums[i] = r.nextInt(40-10+1)+10;
	}

	for(int i = 0; i<nums.length; i++) {
		if(nums[i] % 2 == 0) {
			if(nums[i] % 3 == 0) {
				System.out.println(nums[i]);
			}
		}
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
