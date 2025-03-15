
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Spring Tool Suite telepítése

---

| Művelet | Leírás |
| :------ | :----- |
| Letöltés | ```https://www.spring.io/``` |
| Letöltött fájl ellenőrzése | ```cd Downloads/```<br>```ls``` |
| Letöltött fájl áthelyezése | ```sudo mv downloaded_file.tar.gz /opt``` |
| Az áthelyezett fájl helyének megnyitása | ```cd /opt``` |
| Letöltött fájl kicsomagolása | ```sudo tar -xvf downloaded-file.tar.gz``` |
| Indító ikon létrehozása | ```sudo nano /usr/share/applications/stsLauncher.desktop``` |
| Írd ezt a fájlba | ```[Desktop Entry]```<br>```Name=Spring Tool Suite```<br>```Comment=Spring Tool Suite 4.16.0```<br>```Exec=/opt/sts-4.16.0.RELEASE/SpringToolSuite4```<br>```Icon=/opt/sts-4.16.0.RELEASE/icon.xpm```<br>```StartupNotify=true```<br>```Terminal=false```<br>```Type=Application```<br>```Categories=Development;IDE;Java;``` |
| Mentés | Ctrl + x -> y -> [enter] |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---