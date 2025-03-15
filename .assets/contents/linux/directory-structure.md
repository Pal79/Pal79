
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Könyvtárszerkezet

---

| könyvtár | Leírás |
| :-- | :-- |
| / | A hierarchikus könyvtárfa kiindulópontja (gyökér könyvtár) |
| /boot | A rendszer indításához szükséges állományok helye (grub, vmlinuz, stb) |
| /bin | A futtatható parancsok könyvtára -binaries |
| /sbin | A rendszergazda parancsai -superuser bin |
| /lib | Az induláshoz szükséges osztott rendszerkönyvtárak -libraries<br/>Továbbá tartalmazza a rendszerhez csatolható modulokat, meghajtóprogramokat |
| /dev | A rendszerhez csatlakozott, csatolható különleges állományok -devices |
| /etc | Beállítófájlok, helyi indító parancsok, jelszavak, hálózati-beállítók, etc. helye. |
| /home | Minden felhasználó saját könyvtára itt foglal helyet. (Otthon, édes otthon) |
| /mnt | A felcsatolt (mountolt) perifériák könyvtára. -mount |
| /proc | Itt látható, ahogy a rendszer "él". -process information<br/>Érdemes tüzetesebben átnézni, hiszen érdekes dolgokat találhatunk itt.<br/>pl.: /proc/cpuinfo fájl kiíratásával információt kaphatsz processzorodról. |
| /root | A rendszer gazdájának könyvtára. |
| /tmp | Ideiglenes adatok tárolására használt könyvtár. -temp |
| /usr | Alkalmazások, rendszereszközök tömkelege, a legforgalmasabb könytár. (pl X Window) |
| /var | Változó adatokat tartalmazó állományok könyvtára. (pl.: nyomtatási munkák, levelek, etc)<br/>/var/log : napló fájlok, különös jelentőséggel bírnak a rendszer biztonságának szempontjából |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---