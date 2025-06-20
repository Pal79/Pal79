
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# SmPlayer telepítése

## 1. Ellenőrizzük a hivatalos tárolókat:

Nyisd meg a terminált (Ctrl+Alt+T) és írd be a következő parancsot:
```Bash
sudo apt update
sudo apt install smplayer
```

Ha az SMPlayer elérhető a hivatalos tárolókból, akkor ez a parancs sikeresen telepíteni fogja. Ekkor már kész is vagy!

## 2. Ha az első lépés nem működött (nem található a csomag): PPA hozzáadása

Előfordulhat, hogy az SMPlayer nem található meg az Ubuntu 24.04 alapértelmezett tárolóiban, vagy egy régebbi verzió van ott. Ilyenkor érdemes megkeresni egy megbízható PPA-t, ami az SMPlayer legújabb verzióját biztosítja.

Jelenleg az SMPlayer fejlesztői egy hivatalos PPA-t tartanak fenn, ami a legfrissebb verziókat tartalmazza. Ez a PPA a legtöbb felhasználó számára a legjobb választás.

Add hozzá a PPA-t a következő parancsokkal:
```Bash
sudo add-apt-repository ppa:smplayer-dev/stb
sudo apt update
sudo apt install smplayer smplayer-themes smplayer-skins
```

- ```sudo add-apt-repository ppa:smplayer-dev/stb```: Ez hozzáadja az SMPlayer fejlesztői PPA-ját a rendszeredhez.
- ```sudo apt update```: Ez frissíti a csomaglistát, hogy az újonnan hozzáadott PPA-ból is lássa a csomagokat.
- ```sudo apt install smplayer smplayer-themes smplayer-skins```: Ez telepíti az SMPlayert, valamint az ajánlott témákat és skineket.

## 3. Indítsd el az SMPlayert:

Miután a telepítés befejeződött, az SMPlayert megtalálhatod az alkalmazások menüjében, vagy elindíthatod a terminálból a smplayer paranccsal.

Fontos megjegyzések:

- PPA megbízhatóság: Mindig győződj meg róla, hogy csak megbízható PPA-kat adsz hozzá a rendszeredhez. Az SMPlayer-dev PPA a hivatalos forrás, így ez biztonságos.
- Frissítések: Ha PPA-ból telepítetted, az SMPlayer a jövőbeni rendszerfrissítésekkel együtt fog frissülni.

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---
