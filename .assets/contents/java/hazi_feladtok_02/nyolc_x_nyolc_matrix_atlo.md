
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Töltsünk fel egy 8X8-as mátrix főátlóját 1-esekkel, a többi elem legyen 0.

> Main:

```java
public static void main(String[] args) {

	int[][] matrix = new int[8][8];
	int rowColumn = 0;

	for(int i = 0; i < matrix.length; i++) {
		for(int j = 0; j < matrix.length; j ++) {
			if(i == rowColumn && j == rowColumn) {
				matrix[i][j] = 1;
				System.out.print(matrix[i][j]);
			} else {
				matrix[i][j] = 0;
				System.out.print(matrix[i][j]);
			}
		}
		System.out.println();
		rowColumn++;
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---