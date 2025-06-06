
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Pacman

---

### Alap kapcsolók

| Művelet | parancs | Leírás |
| :------ | :------ | :----- |
| rendszer frissítése | sudo pacman -Syu | Sy - csomagtárolók frissítése<br/>u - frissíti az elavult csomagokat |
| egyszerűbb frissítés | sudo pacman -Su | csak a csomagokat frissíti, a csomagtárolókat nem |
| csomag telepítése | sudo pacman -S csomagnév |  |
| több csomag telepítése | sudo pacman -S csomagnév csomagnév ... |  |
| csomag keresése | sudo pacman -Ss web browser | jelen esetben vebböngészöt keresünk |
| csomag információk | sudo pacman -Si csomagnév |  |
| csomag eltávolítása | sudo pacman -R csomagnév | csak az adott csomagott törli, a függőségeit nem |
| csomag eltávolítása függőségekkel | sudo pacman -Rs |  |
| csomagtároló információk frissítése | sudo pacman -Sy | csak a csomagtárolók listáját frissíti |
| csomagtárolók frissítésének kikényszerítése | sudo pacman -Syy |  |
| letárolt csomagok törlése | sudo pacman -Sc | lemezterület felszabadításánál használjuk '/var/cache/pacman/pkg' |
| telepített csomagok listája | sudo pacman -Q |  |
| a felhasználó által telepített csomagok listája (kizárva a függöségeket) | sudo pacman -Qe |  |
| csoportok telepítése | sudo pacman -S gnome<br/>sudo pacman -S plasma<br/>sudo pacman -S xfce4<br/> |  |
| csoportok listája | sudo pacman -Sg csoport neve | például: sudo pacman -Sg plasma |
| saját csomag telepítése | sudo pacman -U csomagnév-x86_64.pkg.tar.zst |  |
| nem használt függőségek listázása | sudo pacman -Qdt |  |
| nem használt függőségek eltávolítása | sudo pacman -Rns $(pacman -Qdtq) | jelentős lemezterületet szabadíthat fel |
| csomagok intergritásának ellenőrzése | sudo pacman -Qk steam |  |
| csomagok intergritásának részletesebb ellenőrzése | sudo pacman -Qkk steam |  |

---

### Speciális kapcsolók

| Művelet | Parancs | Leírás |
| :------ | :------ | :----- |
| telepít egy csomagot, ha még nincs telepítve,vagy ha új verzió érhető el | sudo pacman -S --needed achiso | felesleges újratelepítések esetére |
| frissíti a rendszert, de az ignore után megadott csomagot kihagyja a frissítésből | sudo pacman -Syu --ignore linux-zen | problémás csomagok esetén használjuk |
| csomag letöltése telepítés nélkül | sudo pacman -Sw archiso | hasznos lehet a csomag letöltése későbbi telepítés céljából |
| csomag eltávolítása a függőségek figyelembe vétele nélkül | sudo pacman -Rdd archiso |  |
| csomag megjelölése telepítettként | sudo pacman -D --asexplicit archiso | függőségként nem lesz kezelve (hasznos az árva csomagok kezelésében) |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---