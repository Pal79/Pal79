
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Java telepítése és beállítása

> | LTS verziók | Kiadás dátuma | Támogatás dátum | Kiterjesztett támogatás dátum |
> | :-- | :-- | :-- | :-- |
> | 8 | 2014 Március | 2022 Március | 2030 December |
> | 11 | 2018 Szeptember | 2023 Szeptember | 2032 Január |
> | 17 | 2021 Szeptember | 2026 Szeptember vagy később | 2029 Szeptember vagy később |
> | 21 | 2023 Szeptember | 2028 Szeptember vagy később | 2031 Szeptember vagy később |
> | 25 | 2025 Szeptember | 2026 Szeptember | 2033 Szeptember |
> 
> jelen esetben a 17-es java telepítése és beállítása

|     | Ubuntu |
| :-- | :----- |
| Verzió ellenőrzése | ```java -version```<br>vagy<br>```which java``` |
| Telepítés | ```sudo apt install openjdk-17-jre```<br>```sudo apt install openjdk-17-jdk``` |
| Alapértelmezett java beállítása | ```sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/java-17-openjdk-amd64/bin/javac" 1```<br>majd ezután<br>```sudo update-alternatives --config javac``` |

---

|     | Manjaro |
| :-- | :------ |
| Verzió ellenőrzése | ```java -version```<br>vagy<br>```which java``` |
| elérhető java verziók listázása | ```sudo pacman -sS java \| grep jre``` |
| Telepítés | ```sudo pacman -S jre17-openjdk```<br>```sudo pacman -S jdk17-openjdk``` |
| alapértelmezett java megtekintése | ```archlinux-java status``` |
| alapértelmezett java verzió kiválasztása |  ```sudo archlinux-java set java-17-openjdk``` |
| alapértelmezett java deaktiválása | ```sudo archlinux-java unset java-17-openjdk``` |
| automatikus alapértelmezett java kiválasztása | ```sudo archlinux-java fix``` |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---