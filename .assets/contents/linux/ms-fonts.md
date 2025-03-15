
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

|      | Ubuntu | Manjaro |
| :--- | :----- | :------ |
| csomagok frissítése | ```sudo apt update``` | ```sudo pacman -Syu```<br>ha rég volt frissítve<br>```sudo pacman -Syyu``` |
| AUR engedélyezése | ---- | ```sudo sed -Ei '/EnableAUR/s/^#//' /etc/pamac.conf``` |
| Telepítés | ```sudo apt install ttf-mscorefonts-installer``` | ```pamac build ttf-ms-fonts``` |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---