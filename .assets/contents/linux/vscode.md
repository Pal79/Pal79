
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# visual studio code telepítése debian rendszerekre

---

> Telepítés

```shell
sudo apt update && sudo apt upgrade -y
```

```shell
sudo apt install software-properties-common apt-transport-https wget
```

```shell
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
```

```shell
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
```

```shell
sudo apt install code
```

```shell
sudo apt update && sudo apt upgrade -y
```

program indítás terminálból az adott program könyvtárából:
```
code .
```

## flatpak telepítés
### Ha még nincs fent a flatpak:
flatpak telepítése:
```bash
sudo apt update
sudo apt install flatpak -y
```
majd flathub tároló hozzáadása:
```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
### Visual studio code telepítése:
```bash
flatpak install flathub com.visualstudio.code
```
program indítás terminálból az adott program könyvtárából:
```bash
flatpak run com.visualstudio.code .
```
vagy beállíthatod, a `code .` paranccsal indíthasd:
#### Bash-nál:
```bash
echo 'alias code="flatpak run com.visualstudio.code"' >> ~/.bashrc
source ~/.bashrc
```
#### Zsh-nál:
```bash
echo 'alias code="flatpak run com.visualstudio.code"' >> ~/.zshrc
source ~/.zshrc
```

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---
