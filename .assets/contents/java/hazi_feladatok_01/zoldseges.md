
---

- [Back to java](../../java.md)
- [Back to main](../../../../README.md)

---

# (zoldseges)
	 * Háromféle terméket vásárolunk: 
	 * almát (240 Ft / kg), 
	 * szilvát (310 Ft/kg) 
	 * és szőlőt (650 Ft/kg). 
	 * A program kérje be a vásárolt mennyiségeket, 
	 * majd írja ki az árakat tételenként és a végösszeget is!
	 * Tájékoztasd a felhasználót az egységárakról is! 
	 * 
	 * 
	 */

	public static void main(String[] args) {
		
		Integer apple, plum, grapes;
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		System.out.println("Melyik termékből hány kilót szeretne vásárolni?");
		try {
			System.out.print("Alma (240 Ft/kg): ");
			apple = Integer.parseInt(br.readLine());
			System.out.print("Szilva (310 Ft/kg): ");
			plum = Integer.parseInt(br.readLine());
			System.out.print("Szőlő (650 Ft/kg): ");
			grapes = Integer.parseInt(br.readLine());
			
			System.out.println("Vásárolt termékek:");
			System.out.println(" - Alma: " + apple + " kg " + apple * 240 + " forint.");
			System.out.println(" - Szilva: " + plum + " kg " + plum * 240 + " forint.");
			System.out.println(" - Szőlő: " + grapes + " kg " + grapes * 240 + " forint.");
			
			br.close();
		} catch (NumberFormatException | IOException e) {
			// TODO Auto-generated catch block
			//e.printStackTrace();
			System.out.println("Hibás adatbevitel!");
		}

	}

