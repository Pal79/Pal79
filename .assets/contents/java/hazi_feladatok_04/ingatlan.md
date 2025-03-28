
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Hozz létre egy Ingatlan nevű osztályt (
> - megnevezés -> szöveg, 
> - négyzetméter -> egész szám,
> - irányítószám -> egész szám, 
> - város -> szöveg, 
> - cím -> szöveg, 
> - szobák száma -> egész szám)!
>
> - a. Kérd be a felhasználótól egy ingatlan adatait, majd hozz létre egy objektumpéldányt az adatokkal!
> - b. Készíts metódust, ami kiírja, az ingatlan minden adatát!
> - c. Készíts metódust, ami eldönti, hogy fővárosi –e az ingatlan (csak Magyarországi ingatlanokat kell kezelnie az alkalmazásnak)!
> - d. Készíts metódust ami, eldönti, hogy nagycsaládosok számára alkalmas –e (110nm felett már alkalmas)!
> - e. Készíts metódust, ami kiírja, hogy Pesten vagy Budán van –e az ingatlan? (emelt szint)

## Ingatlan.java

```java
public class Ingatlan {

	String megnevezes;
	Integer negyzetmeter;
	Integer iranyitoszam;
	String varos;
	String cim;
	Integer szobak_szama;

	public Ingatlan(String megnevezes, Integer negyzetmeter, Integer iranyitoszam, String varos, String cim, Integer szobak_szama) {
		super();
		this.megnevezes = megnevezes;
		this.negyzetmeter = negyzetmeter;
		this.iranyitoszam = iranyitoszam;
		this.varos = varos;
		this.cim = cim;
		this.szobak_szama = szobak_szama;
	}

	public String getMegnevezes() {
		return megnevezes;
	}

	public void setMegnevezes(String megnevezes) {
		this.megnevezes = megnevezes;
	}

	public Integer getNegyzetmeter() {
		return negyzetmeter;
	}

	public void setNegyzetmeter(Integer negyzetmeter) {
		this.negyzetmeter = negyzetmeter;
	}

	public Integer getIranyitoszam() {
		return iranyitoszam;
	}

	public void setIranyitoszam(Integer iranyitoszam) {
		this.iranyitoszam = iranyitoszam;
	}

	public String getVaros() {
		return varos;
	}

	public void setVaros(String varos) {
		this.varos = varos;
	}

	public String getCim() {
		return cim;
	}

	public void setCim(String cim) {
		this.cim = cim;
	}

	public Integer getSzobak_szama() {
		return szobak_szama;
	}

	public void setSzobak_szama(Integer szobak_szama) {
		this.szobak_szama = szobak_szama;
	}
	
	// e. Készíts metódust, ami kiírja, hogy Pesten vagy Budán van –e az ingatlan? (emelt szint)
	public void PropertyIsOnPestOrBuda() {
		if(this.varos.equals("budapest") || this.varos.equals("Budapest") || this.varos.equals("BudaPest")) {
			if(this.iranyitoszam >= 1010 && this.iranyitoszam <= 1039) {
				System.out.println("Az ingatlan Budán található.");
			} else if(this.iranyitoszam >= 1110 && this.iranyitoszam <= 1129) {
				System.out.println("Az ingatlan Budán található.");
			} else if(this.iranyitoszam >= 1220 && this.iranyitoszam <= 1229) {
				System.out.println("Az ingatlan Budán található.");
			} else {
				System.out.println("Az ingatlan Pesten található.");
			}
		} else {
			System.out.println("Az ingatlan nem a fővárosban található.");
		}
	}
	
	// d. Készíts metódust ami, eldönti, hogy nagycsaládosok számára alkalmas –e (110nm felett már alkalmas)!
	public void PropertyForLargeFamilysOrNot() {
		if(this.negyzetmeter > 110) {
			System.out.println("Az ingatlan nagy családosoknak.");
		} else {
			System.out.println("Az ingatlan nem nagy családosoknak ajánlott.");
		}
	}
	
	// c. Készíts metódust, ami eldönti, hogy fővárosi –e az ingatlan 
	//    (csak Magyarországi ingatlanokat kell kezelnie az alkalmazásnak)!
	public void IsCapital() {
		if(this.varos.equals("budapest") || this.varos.equals("Budapest") || this.varos.equals("BudaPest")) {
			System.out.println("Az ingatlan a fővárosban található.");
		} else {
			System.out.println("Az ingatlan vidéken található.");
		}
	}
	
	// b. Készíts metódust, ami kiírja, az ingatlan minden adatát!
	public void DisplayDatas() {
		System.out.println("Az ingatlan adatai:");
		System.out.println(" - megnevezése: " + this.megnevezes);
		System.out.println(" - mérete: " + this.negyzetmeter + " nm");
		System.out.println(" - irányítószáma: " + this.iranyitoszam);
		System.out.println(" - város: " + this.varos);
		System.out.println(" - cím: " + this.cim);
		System.out.println(" - szobák száma: " + this.szobak_szama);
	}
}
```

## DatasInput.java

```java
public class DatasInput {
	
	// a. Kérd be a felhasználótól egy ingatlan adatait, majd hozz létre egy objektumpéldányt az adatokkal!
	
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	public Ingatlan DatasUp() {
		
		Ingatlan ingatlan_obj = null;
		
		System.out.println("Add meg az ingatlan adatait:");
		
		try {
			System.out.print("Ingatlan megnevezése: ");
			String megnevezes = br.readLine();
			System.out.print("Ingatlan mérete (nm): ");
			int negyzetmeter = Integer.parseInt(br.readLine());
			System.out.print("Az ingatlan irányítószáma: ");
			int iranyitoszam = Integer.parseInt(br.readLine());
			System.out.print("Az ingatlan melyik városban található: ");
			String varos = br.readLine();
			System.out.print("Az ingatlan címe: ");
			String cim = br.readLine();
			System.out.print("Az ingatlan szobáinak száma: ");
			int szobak_szama = Integer.parseInt(br.readLine());
			
			ingatlan_obj = new Ingatlan(
					megnevezes, 
					negyzetmeter, 
					iranyitoszam, 
					varos, 
					cim, 
					szobak_szama);
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return ingatlan_obj;
	}

}
```

## Main.java

```java
public class Main {

	public static void main(String[] args) {
		
		System.out.println("a. feladat:");
		System.out.println("Az ingatlan felvétele: ");
		
		DatasInput datas_obj = new DatasInput();
		Ingatlan ingatlan_obj = datas_obj.DatasUp();
		
		System.out.println();
		System.out.println("b. feladat:");
		ingatlan_obj.DisplayDatas();
		System.out.println();
		System.out.println("c. feladat:");
		ingatlan_obj.IsCapital();
		System.out.println();
		System.out.println("d. feladat:");
		ingatlan_obj.PropertyForLargeFamilysOrNot();
		System.out.println();
		System.out.println("e. feladat:");
		ingatlan_obj.PropertyIsOnPestOrBuda();
		System.out.println();
	}

}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---