
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Tölts fel egy 20 elemű tömböt véletlen számokkal [-60;+60] intervallumból, 
> majd írd ki az elemeket egymás mellé szóközzel elválasztva! 
> Alatta írd ki egy sorban egymás mellé a negatív számok közül azokat 
> a számokat, amelyek kisebbek -20-nál

> Main:

```java
public static void main(String[] args) {		

	int[] nums = arrUpload();

	for(int i = 0; i < nums.length; i++) {
		System.out.print(nums[i] + " ");
	}

	System.out.println();

	for(int i = 0; i < nums.length; i++) {
		if(nums[i] < -20) {
			System.out.print(nums[i] + " ");
		}
	}		
}
```

> Tömbfeltöltés:

```java
private static int[] arrUpload() {
	Random r = new Random();
	int[] nums = new int[20];

	for(int i = 0; i < nums.length; i++) {
		nums[i] = r.nextInt((60 - (-60)) + 1) + (-60);
	}
	return nums;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

