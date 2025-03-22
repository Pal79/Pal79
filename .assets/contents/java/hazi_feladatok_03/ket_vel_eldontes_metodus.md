
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# ket_vel_eldontes_metodus

---

> Hozz létre metódust, 
> amely létrehoz 2 db véletlen számot 1-10 között, 
> majd eldönti, hogy szorzatuk páros vagy páratlan! 
> Az ellenőrzéshez a generált két számot is írd ki! 
>
> (ket_vel_eldontes_metodus)

> Main:

```java
public static void main(String[] args) {

		decide();
}
```

> eldöntés:

```java
private static void decide() {
	Random r = new Random();

	int num1 = r.nextInt(10-1+1)+1;
	int num2 = r.nextInt(10-1+1)+1;

	int result = num1 * num2;

	if(result % 2 == 0) {
		System.out.println(num1 + " és " + num2 + " szorzata páros szám: " + result);
	} else {
		System.out.println(num1 + " és " + num2 + " szorzata páratlan szám: " + result);
	}
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---