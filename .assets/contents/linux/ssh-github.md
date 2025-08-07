
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# SSH Kapcsolatok

---

## SSH kulcs létrehozása Raspberry Pi-hez, jelszavas belépés nélkül
### Fájl létrehozása
```Bash
ssh-keygen -t ed25519 -f ~/.ssh/id_rpi_ed25519 -C "kulcs a raspberry pi-hez"
```
ha jelszót kér, csak nyugodtan nyomj `Enter`-t
>
Így létrehoz két fájlt:
- `~/.ssh/id_rpi_ed25519` - ez a privát kulcsod ( :memo: NE OSZD MEG!!! )
- `~/.ssh/id_rpi_ed25519.pub` ez lesz a publikus kulcs
### Feltöltés Pi-re
Az IP-t természetesen módosítani kell a Raspberry IP címére
```Bash
ssh-copy-id -i ~/.ssh/id_rpi_ed25519.pub pi@192.168.1.10
```
Így a Pi-n bekerül egy `authorized_keys` fájlba a publikus kulcs
### Tesztelés
```Bash
ssh -i ~/.ssh/id_rpi_ed25519 pi@192.168.1.10
```
Ha nem kéri a jelszót és beenged, akkor működik.
## Egyszerű belépés Raspberry Pi-re
Léterhozol egy `config` fájlt a(z) `~/.ssh/` könyvtárba
```Bash
touch ~/.ssh/config
```
### Megfelelő jogosultságok megadása
```Bash
chmod 600 ~/.ssh/config
```
### Majd a fájl szerkesztése
```Bash
nano ~/.ssh/config
```
majd beleírjuk:
```Bash
Host raspberrypi
    HostName 192.168.1.100
    User pi
    IdentityFile ~/.ssh/id_rpi_ed25519
```
:memo: A `Host` résznél megadhatsz bármit amit akarsz, a `HostName` a raspberry IP címe, `User` a Raspberry felhasználó neve és az `IdentityFile` pedig a kulcs elérési útja 
### Majd belépés Pi-re
```Bash
ssh raspberrypi
```
## Jelszavas belépés tiltása
### Lépj be a Pi-dre és nyisd meg
```Bash
sudo nano /etc/ssh/sshd_config
```
keresd meg ezt a sort:
```Bash
#PasswordAuthentication yes
```
és írd át erre:
```Bash
PasswordAuthentication no
```
majd mentés.
>
Indítsd újra az SSH-t
```Bash
sudo systemctl restart ssh
```
## SSH kapcsolat létrehozása Github-al

---

### ssh kulcs beállítása
```Bash
ssh-keygen -t rsa -b 4096 -C "youremail@gmail.com"
```
```Bash
eval "$(ssh-agent -s)"
```
```Bash
ssh-add ~/.ssh/id_rsa
```
### publikus ssh kulcs kiíratása
```shell
cat ~/.ssh/id_rsa.pub
```
majd a megjelenített kulcs kijelölése és másolása ide: github.com -> Settings -> SSH and GPG keys

---

### ha ezt az üzenetet kapod:

```Bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:R+hosszú kód van ide írva :) .
Please contact your system administrator.
Add correct host key in /home/username/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/username/.ssh/known_hosts:5
  remove with:
  ssh-keygen -f "/home/username/.ssh/known_hosts" -R "192.168.1.1**"
Host key for 192.168.1.1** has changed and you have requested strict checking.
Host key verification failed.
```
töröld az adott hosztnevet vagy az IP-t
```Bash
ssh-keygen -R <hostname>
```
vagy
```Bash
ssh-keygen -R 192.168.1.***
```
ezután próbáld újra a kapcsolódást

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---
