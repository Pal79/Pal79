
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (kocka)

> Hozzunk létre alkalmazást, 
> amely kiszámolja a kocka felszínét és térfogatát! 

> Main:

```java
public static void main(String[] args) {
		
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
  System.out.println("Kérlek add meg, melyik adat áll rendelkezésedre.");
  System.out.println("Él (a)");
  System.out.println("Testátló (D)");
  System.out.println("Lapátló (d)");
  System.out.println("Térfogat (V)");
  System.out.println("Felszín (F)");
  System.out.println("Alapterület (Ta)");
  System.out.println("Palást terület (Tp)");	
		
  try {
    System.out.print("Add meg a meglévő adat betűjelét: ");
    String option = br.readLine();
			
    switch(option) {
      case "a":
        System.out.println("Add meg az él méretét (a méret centiméterben értendő): ");
        Double a = Double.parseDouble(br.readLine());
        System.out.println("Kocka éle: " + a + " cm" );
        System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
        System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
        System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
        System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
        System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
        System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
        System.out.println();
        System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
        System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
      break;
				case "D":
					System.out.println("Add meg a testátló méretét (a méret centiméterben értendő): ");
					Double D = Double.parseDouble(br.readLine());
					a = ElSzamitasTestatloval(D);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + D + "cm");
					System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
					System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
					System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
					System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
					System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				case "d":
					System.out.println("Add meg a lapátló méretét (a méret centiméterben értendő): ");
					Double d = Double.parseDouble(br.readLine());
					a = ElSzamitasLapatloval(d);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
					System.out.println("Kocka lapátlója: " + d + " cm");
					System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
					System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
					System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
					System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				case "V":
					System.out.println("Add meg a térfogat méretét (a méret köbcentiméterben értendő): ");
					Double V = Double.parseDouble(br.readLine());
					a = ElSzamitasTerfogattal(V);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
					System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
					System.out.println("Kocka térfogata: " + V + " cm3");
					System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
					System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
					System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				case "F":
					System.out.println("Add meg a felszín méretét (a méret négyzetcentiméterben értendő): ");
					Double F = Double.parseDouble(br.readLine());
					a = ElszamitasFelszinnel(F);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
					System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
					System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
					System.out.println("Kocka Felszíne: " + F + " cm2");
					System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
					System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				case "Ta":
					System.out.println("Add meg az alapterület méretét (a méret négyzetcentiméterben értendő): ");
					Double Ta = Double.parseDouble(br.readLine());
					a = ElSzamitasAlapterulettel(Ta);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
					System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
					System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
					System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
					System.out.println("Kocka alap területe: " + Ta + " cm2");
					System.out.println("Kocka palást területe: " + PalastTerulet(a) + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				case "Tp":
					System.out.println("Add meg a palást terület méretét (a méret négyzetcentiméterben értendő): ");
					Double Tp = Double.parseDouble(br.readLine());
					a = ElSzamitasPalastTerulettel(Tp);
					System.out.println("Kocka éle: " + a + " cm" );
					System.out.println("Kocka testátlója: " + Testatlo(a) + "cm");
					System.out.println("Kocka lapátlója: " + Lapatlo(a) + " cm");
					System.out.println("Kocka térfogata: " + Terfogat(a) + " cm3");
					System.out.println("Kocka Felszíne: " + Felszin(a) + " cm2");
					System.out.println("Kocka alap területe: " + AlapTerulet(a) + " cm2");
					System.out.println("Kocka palást területe: " + Tp + " cm2");
					System.out.println();
					System.out.println("Kocka köré írható gömb: " + kockaKoreIrhatoGomb(a) + " cm3");
					System.out.println("Kockába írható gömb: " + kockabaIrhatoGomb(a) + " cm3");
				break;
				default:
					System.out.println("Hibás adatbevitel!");
				break;
			}
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			// e.printStackTrace();
			System.out.println("Hibás adatbevitel!");
		}
		
	}
	
	/**
	 * Él számítások:
	 * 
	 * @param d
	 * @return a = (d) / (Math.sqrt(2));
	 * 
	 * @param D
	 * @return a = (D) / (Math.sqrt(3));
	 * 
	 * @param V
	 * @return a = Math.pow(Math.sqrt(V),3);
	 * 
	 * @param F
	 * @return a = Math.sqrt(F / 6);
	 * 
	 * @param Ta
	 * @return a = Math.sqrt(Ta);
	 * 
	 * @param Tp
	 * @return a = (Math.sqrt(Tp)) / (2);
	 */
	private static Double ElSzamitasLapatloval(Double d) {
		return d / Math.sqrt(2);
	}
	private static Double ElSzamitasTestatloval(Double D) {
		return D / Math.sqrt(3);
	}
	private static Double ElSzamitasTerfogattal(Double V) {
		return Math.pow(Math.sqrt(V), 3);
	}
	private static Double ElszamitasFelszinnel(Double F) {
		return Math.sqrt(F / 6);
	}
	private static Double ElSzamitasAlapterulettel(Double Ta) {
		return Math.sqrt(Ta);
	}
	private static Double ElSzamitasPalastTerulettel(Double Tp) {
		return Math.sqrt(Tp) / 2;
	}

	/**
	 * Térfogat:
	 * @return V = Math.pow(a,3);
	 */
	private static Double Terfogat(Double a) {
		return Math.pow(a, 3);
	}
	/**
	 * Felszín:
	 * @return F = 6*Math.pow(a,2);
	 */
	private static Double Felszin(Double a) {
		return 6*Math.pow(a, 2);
	}
	/**
	 * Alapterület:
	 * @return Ta = Math.pow(a,2);
	 */
	private static Double AlapTerulet(Double a) {
		return Math.pow(a, 2);
	}
	/**
	 * Palást terület:
	 * @return Tp = 4 * Math.pow(a,2);
	 */
	private static Double PalastTerulet(Double a) {
		return 4 * Math.pow(a, 2);
	}
	/**
	 * Testátló:
	 * @return D = a * Math.sqrt(3);
	 */
	private static Double Testatlo(Double a) {
		return a * Math.sqrt(3);
	}
	/**
	 * Lapátló:
	 * @return d = a * Math.sqrt(2);
	 */
	private static Double Lapatlo(Double a) {
		return a * Math.sqrt(2);
	}
	
	
	/**
	 * A kocka további tulajdonságai
	 * 
	 * Minden kocka köré írható egy gömb. 
	 * Ennek a gömbnek a sugara a testátlónak a felével egyezik meg.
	 * 
	 * @param a
	 * @return R = (Math.sqrt(3 * a)) / 2
	 * 
	 * A kockába is írtható egy gömb, ennek pedig az oldalhosszúság felével egyezik meg a sugara.
	 * 
	 * @param a
	 * @return r = a / 2
	 */
	public static Double kockaKoreIrhatoGomb(Double a) {
		return (Math.sqrt(3*a))/2;
	}
	public static Double kockabaIrhatoGomb(Double a) {
		return a/2;
	}

---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---
