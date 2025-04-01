
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

> Készíts egy Tanulo nevű osztályt (vezetéknév, keresztnév, átlag)!
>
> - a. Hozz létre 2 objektumpéldányt a felhasználótól érkező adatokkal!
> - b. Készíts metódust, ami kiírja az adatokat egymás alá!
> - c. Készíts metódus, ami eldönti, kell –e értesíteni a szülőt a tanuló rossz érdemjegye miatt (2-es átlag alatt)!
> - d. Készíts metódus, ami eldönti, kap –e dicséretet a tanuló (4,5-ös átlag felett jár)!

> Tanulo.java

```java
public class Tanulo {
	
	String vezeteknev;
	String keresztnev;
	Double atlag;
	
	public Tanulo(String vezeteknev, String keresztnev, Double atlag) {
		this.vezeteknev = vezeteknev;
		this.keresztnev = keresztnev;
		this.atlag = atlag;
	}

	public String getVezeteknev() {
		return vezeteknev;
	}

	public void setVezeteknev(String vezeteknev) {
		this.vezeteknev = vezeteknev;
	}

	public String getKeresztnev() {
		return keresztnev;
	}

	public void setKeresztnev(String keresztnev) {
		this.keresztnev = keresztnev;
	}

	public Double getAtlag() {
		return atlag;
	}

	public void setAtlag(Double atlag) {
		this.atlag = atlag;
	}
	
	// d. Készíts metódus, ami eldönti, kap –e dicséretet a tanuló (4,5-ös átlag felett jár)!
	public void StudentHonourable() {
		if(this.atlag > 4.5) {
			System.out.println("A " + this.vezeteknev + " " + this.keresztnev + " nevű tanuló dícséretre érdemes");
		}
	}
	
	// c. Készíts metódus, ami eldönti, kell –e értesíteni a szülőt a tanuló rossz érdemjegye miatt (2-es átlag alatt)
	public void InformWrongRate() {
		if(this.atlag <2) {
			System.out.println("A szülőt értesíteni kell a " + this.vezeteknev + " " + this.keresztnev + " nevű tanuló rossz átlaga miatt.");
		}
	}
	
	// b. Készíts metódust, ami kiírja az adatokat egymás alá!
	public void TanuloAdatokKiir() {
		System.out.println("Tanuló adatai:");
		System.out.println(" - neve: " + this.vezeteknev + " " + this.keresztnev);
		System.out.println(" - átlaga: " + this.atlag);
	}

}
```

> DatasUpload.java

```java
public class DatasUpload {
	
	private static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	public Tanulo StudentDatas() {
		
		Tanulo tanulo_obj = null;
		
		
		try {
			// a. Hozz létre 2 objektumpéldányt a felhasználótól érkező adatokkal!
			System.out.println("Kérlek add meg a tanuló adatait:");
			System.out.print(" - vezetéknév: ");
			String last_name = br.readLine();
			System.out.print(" - keresztnév: ");
			String first_name = br.readLine();
			System.out.print(" - tanuló átlaga: ");
			Double avereage = Double.parseDouble(br.readLine());
			
			tanulo_obj = new Tanulo(last_name, first_name, avereage);
			
			//br.close();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		
		return tanulo_obj;
	}

}
```

> Main.java

```java
public class Main {

	public static void main(String[] args) {
		
		DatasUpload datas_obj = new DatasUpload();
		System.out.println("a. feladat:");
		System.out.println("1. tanuló adatainak felvétele:");
		Tanulo tanulo_1_obj = datas_obj.StudentDatas();
		System.out.println("2. tanuló adatainak felvétele:");
		Tanulo tanulo_2_obj = datas_obj.StudentDatas();
		System.out.println("--------------------");
		
		System.out.println("b. feladat:");
		System.out.println("1. tanuló adatai:");
		tanulo_1_obj.TanuloAdatokKiir();
		System.out.println();
		tanulo_1_obj.InformWrongRate();
		tanulo_1_obj.StudentHonourable();
		System.out.println();
		System.out.println("2. tanuló adatai:");
		tanulo_2_obj.TanuloAdatokKiir();
		System.out.println();
		tanulo_2_obj.InformWrongRate();
		tanulo_2_obj.StudentHonourable();
		System.out.println();
	}

}
```

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---