
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (ot_veletlen_atlag)

> Hozz létre 5 darab véletlen számot 1-8 közötti intervallumban, 
> majd írd ki a számok átlagát!

> Main:

```java
public static void main(String[] args) {

	int rand_nums[] = new int[5];
	Random r = new Random();

	for(int i = 0; i < rand_nums.length; i++) {
		int num = r.nextInt(8)+1;
		rand_nums[i] = num; 
	}
	int nums_value = 0;
	for(int i = 0; i < rand_nums.length; i++) {
		nums_value += rand_nums[i];
	}
	System.out.println(nums_value / 5);
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---


