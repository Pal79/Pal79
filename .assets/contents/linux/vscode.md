
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

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---