
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (penztaros)

> Egy pénztáros a napi bevételének 5%-át megkapja jutalomként. 
> Kérd be a napi bevételt, és írd a képernyőre, hogy mennyi a jutalom! 
> A jutalmat kerekítsd egész értékre! 

> Main:

```java
public static void main(String[] args) {

	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

	try {
		System.out.print("Add meg a napi bevételt: ");
		Integer money = Integer.parseInt(br.readLine());

		Integer result = (money / 100) * 5;

    System.out.println("A pénztáros napi jutalma: " + result);
			
    br.close();
  } catch (NumberFormatException | IOException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
  }
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
