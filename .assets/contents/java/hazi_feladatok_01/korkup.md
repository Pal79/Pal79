
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (korkup)

> Olvasd be egy egyenes körkúp sugarát és magasságát, 
> majd számold ki belőle a térfogatát és a felszínét!

> Main:

```java
public static void main(String[] args) {
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  try {
    System.out.print("Add meg a körkúp sugarát: ");
    Double r = Double.parseDouble(br.readLine());
			
    System.out.print("Add meg a körkúp magasságát: ");
    Double m = Double.parseDouble(br.readLine());
			
    System.out.println("A körkúp térfogata: " + terfogat(r, m));
    System.out.println("A körkúp felszíne: " + felszin(r, m));
			
    br.close();
  } catch (NumberFormatException | IOException e) {
    // TODO Auto-generated catch block
    //e.printStackTrace();
			
    System.out.println("Hibás adatbevitel!");
  }
}
```

> - Térfogat számítás
> - Alap terület számítás
> - Palást terület számítás
> - Felszín számítás
> - Palást sugár számítás
> - Átmérő számítás

```java
/**
 * V = térfogat
 * A = felszín
 * Ta = az alap teülete
 * Tp = a palást területe
 * r = sugár
 * d = átmérő
 * m = magasság
 * s = a palást sugara
 * S' = középpont
 * V' = a kúp csúcsa
 * 
 * @param r, m
 * 
 * @return V = (1/3)*Math.pi*Math.pow(r,2)*m
 * @return Ta = Math.pi*Math.pow(r,2)
 * @return Tp = Math.pi*r*s
 * @return A = Ta + Tp
 * @return A = Math.pi*r*(r+s)
 * @return s = Math.sqrt(Math.pow(r,2)+Math.pow(m,2))
 * @return d = 2*r
 */
private static Double terfogat(Double r, Double m) {
  return (1/3) * (Math.PI * (Math.pow(r, 2) * m));
}
private static Double alapTerulet(Double r) {
  return Math.PI * Math.pow(r, 2);
}
private static Double palastTerulet(Double r, Double s) {
  return Math.PI * r * s;
}
private static Double felszin(Double Ta, Double Tp) {
	return Ta + Tp;
}
private static Double palastSugara(Double r, Double m) {
	return Math.sqrt(Math.pow(r, 2) + Math.pow(m, 2));
}
private static Double atmero(Double r) {
	return 2 * r;
}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
