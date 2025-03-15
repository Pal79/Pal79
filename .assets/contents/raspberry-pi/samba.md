
---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---

# Samba szerver telepítése

<!--
Shell:      console, shell
Bash:       bash, sh, zsh
PowerShell: powershell, ps
DOS:        dos, bat, cmd
-->

---

> Rendszer frissítése

```shell
sudo apt update
```

> Telepítés

```shell
sudo apt install samba
```

> Ellenőrzés

```shell
whereis samba
```

> Eredmény:

```shell
samba: /usr/sbin/samba /usr/lib/samba /etc/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz
```

> Könyvtár létrehozás (ha még nincs)

```shell
sudo mkdir /home/<username>/sambashare/
```

> konfigurációs fájl szerkesztése:

```shell
sudo nano /etc/samba/smb.conf
```

> A fájl végére beírni:

```shell
[sambashare]
    comment = Samba on Ubuntu
    path = /home/username/sambashare
    read only = no
    browsable = yes
```

> Samba szerver újraindítása

```shell
sudo service smbd restart
```

> Tűzfal engedély:

```shell
sudo ufw allow samba
```

> Felhasználónév létrehozás és jelszó megadása*2

```shell
sudo smbpasswd -a username
```

> Samba server elérése:

```shell
smb://ip-address
```

### Ha nem tudsz fájlokat megosztani:

> hozzáadás az smb.conf >> [Global] részéhez:

```shell
server min protocol = NT1
client min protocol = NT1
```

---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---