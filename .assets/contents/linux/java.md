
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Java telepítése és beállítása

> A java LTS verziói: ```8 - 11 - 17```
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