
---

[Vissza az előző oldalra](../raspberry-pi.md)
[Vissza a főoldalra](../../../README.md)

---

# NFS beállítása (Szerver: Debian, Kilens: Arch,Debian)
## 1. Szerver beállításai
### 1.1 NFS szerver telepítése:
```Bash
sudo apt update
sudo apt install nfs-kernel-server
```
### 1.2 Megosztani kívánt mappa létrehozása és jogosultságok:
```Bash
sudo mkdir -p /mnt/hare
sudo chown -R $USER:$USER /mnt/share
sudo chmod -R 777 /mnt/share
```
:memo: Megjegyzés: Ezek a jogosultságok nagyon megengedők, de így biztosan nem lesz jogosultsági probléma.
### 1.3 Megosztás hozzáadása az `/etc/exports` fájlhoz:
```Bash
sudo nano /etc/exports
```
ez egy belső hálózati megosztás:
```Bash
/mnt/share 192.168.1.0/24(rw,sync,no_subtree_check,all_squash,anonuid=1000,anongid=1000,crossmnt)
```
### 1.4 Export újratöltése és NFS szolgáltatás újraindítása:
```Bash
sudo exportfs -ra
sudo systemctl restart nfs-kernel-server
```
## 2. Kliens beállításai
### 2.1 NFS kliens telepítése:
Arch:
```Bash
sudo pacman -Syu
sudo pacman -S nfs-utils
```
Debian:
```Bash
sudo apt update
sudo apt install nfs-common
```
### 2.2 Csatolási pont létrehozása
```Bash
sudo mount /home/<username>/pi_share
```
### 2.3 Megosztás csatolása
Állandó csatolás:
```Bash
sudo nano /etc/fstab
```
és beleírni:
```Bash
192.168.1.10:/mnt/share  /home/<username>/pi_share  nfs  defaults,noauto,x-systemd.automount,_netdev,soft,timeo=10,retrans=2 0 0
```
### 2.4 Ellenőrzés
```Bash
ls -l /home/<username>/pi_share
```
Ha minden jól ment, a megosztott fájlok itt láthatók.
## Jogosultságok
- Ellenőrizd a szerveren a /mnt/share jogosultságát:
```Bash
ls -ld /mnt/share
```
Ha a jogosultság `root:root`, állítsd be:
```Bash
sudo chown -R $USER:$USER /mnt/share/torrents
sudo chmod -R 755 /mnt/share/torrents
```

---

# SSH
### 1. Kliens gépen
Ha még nincs kulcspár, hozz létre egyet:
```Bash
ssh-keygen -t ed25519 -f ~/.ssh/id_rpi_ed25519 -C "kulcs a raspberry pi-hez"
```
ha jelszót kér, csak nyugodtan nyomj Enter-t
- Így létrehoz két fájlt:
    - `~/.ssh/id_rpi_ed25519` - ez a privát kulcsod ( :alert: NE OSZD MEG!!! )
    - `~/.ssh/id_rpi_ed25519.pub` ez lesz a publikus kulcs
### 2. Feltöltés Pi-re
Az IP-t természetesen módosítani kell a Raspberry IP címére
```Bash
ssh-copy-id -i ~/.ssh/id_rpi_ed25519.pub pi@192.168.1.10
```
Így a Pi-n bekerül egy `authorized_keys` fájlba a publikus kulcs
### 3. Tesztelés
```Bash
ssh -i ~/.ssh/id_rpi_ed25519 pi@192.168.1.10
```
Ha nem kéri a jelszót és beenged, akkor működik.
## Egyszerű belépés Raspberry Pi-re
### 1. Léterhozol egy `config` fájlt a(z) `~/.ssh/` könyvtárba
```Bash
touch ~/.ssh/config
```
### 2. Megfelelő jogosultságok megadása
```Bash
chmod 600 ~/.ssh/config
```
### 3. Majd a fájl szerkesztése
```Bash
nano ~/.ssh/config
```
majd beleírjuk:
```Bash
Host raspberrypi
    HostName 192.168.1.10
    User pi
    IdentityFile ~/.ssh/id_rpi_ed25519
```
- A `Host` résznél megadhatsz bármit amit akarsz,
- a `HostName` a raspberry IP címe,
- `User` a Raspberry felhasználó neve,
- az`IdentityFile` pedig a kulcs elérési útja.
### 4. Majd belépés Pi-re
```Bash
ssh raspberrypi
```
## Jelszavas belépés tiltása
### 1. Lépj be a Pi-dre és nyisd meg
```Bash
sudo nano /etc/ssh/sshd_config
```
Majd keresd meg ezeket a sorokat és módosítsd, vagy csak vedd ki a `#` kommnetet előlük:
```Bash
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
PasswordAuthentication no
PermitRootLogin no
```
:memo: Én pl. csak beírtam a fájl végére és így is működik és ha valamiért vissza kell állítani, akkor nem kell keresgélni, csak kommentelni.
>
Ez megtiltja a jelszavas belépést, csak kulccsal lehet majd belépni.
### 2. Mentés után újraindítás:
```Bash
sudo systemctl restart ssh
```
### 2.3 Vagy használd ezt
#### Raspberry pi-re optimalizált `sshd_config`
```Bash
# Alapbeállítások
Port 22
Protocol 2
AddressFamily any
ListenAddress 0.0.0.0
ListenAddress ::

# Felhasználók
PermitRootLogin no
AllowUsers grunghar

# Hitelesítés
PubkeyAuthentication yes
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM yes

# Host kulcsok (hagyhatod a default-ot)
HostKey /etc/ssh/ssh_host_ed25519_key
HostKey /etc/ssh/ssh_host_rsa_key

# Biztonsági opciók
PermitEmptyPasswords no
PermitUserEnvironment no
X11Forwarding no
AllowTcpForwarding no
GatewayPorts no
PermitTunnel no
AllowAgentForwarding yes

# Idle timeout (ha valaki elfelejt kijelentkezni)
ClientAliveInterval 300
ClientAliveCountMax 2

# Logging
LogLevel VERBOSE

# Szigorúbb crypto (modern kliensekkel működik)
KexAlgorithms curve25519-sha256,curve25519-sha256@libssh.org
Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com
MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com

# Banner (opcionális, jogi figyelmeztetéshez)
# Banner /etc/issue.net
```
- `PermitRootLogin no` $rarr; root soha nem tud belépni SSH-val.
- `AllowUsers grunghar` $rarr; csak a te felhasználód léphet be.
- `PubkeyAuthentication yes` + `PasswordAuthentication no` $rarr; csak kulccsal lehet belépni.
- `X11Forwarding no` $rarr; ne próbáljon grafikus programot SSH-n átküldeni.
- `ClientAliveInterval 300` $rarr; 5 perc inaktivitás után ellenőrzi, él-e a kapcsolat.
- `Ciphers`, `MACs`, `KexAlgorithms` $rarr; modern, biztonságos titkosítás (régi kliensek esetleg nem mennek, de Linux/Win10+/Mac mind jó).

---

# Szerver (Raspberry Pi, Debian) – UFW
## Telepítés:
```Bash
sudo apt install ufw -y
```
Alapbeállítások:
```Bash
# alapból mindent tiltunk
sudo ufw default deny incoming
sudo ufw default allow outgoing

# engedjük az SSH-t (ha biztosan 22-es port)
sudo ufw allow 22/tcp

# engedjük az NFS-t (2049)
sudo ufw allow from 192.168.1.0/24 to any port 2049 proto tcp
sudo ufw allow from 192.168.1.0/24 to any port 2049 proto udp

# (opcionális) Samba, ha használnád
# sudo ufw allow from 192.168.1.0/24 to any app Samba

# engedélyezés
sudo ufw enable
sudo ufw status verbose
```
- kívülről senki nem tud kapcsolódni, csak a belső háló (`192.168.1.0/24`) gépei.
- SSH mindig elérhető, hogy ne zárd ki magad.
- NFS-hez kell a `2049/tcp` és `2049/udp`.
## Kliens
### 1.1 Arch (firewalld)
Telepítés (Arch):
```Bash
sudo pacman -S firewalld
sudo systemctl enable --now firewalld
```
Alapbeállítások:
```Bash
# zóna: home (belső hálóra ideális)
sudo firewall-cmd --set-default-zone=home

# engedjük az SSH-t
sudo firewall-cmd --permanent --zone=home --add-service=ssh

# engedjük az NFS klienst
sudo firewall-cmd --permanent --zone=home --add-service=nfs

# engedjük az rpc-bind-et is (NFS-hez szükséges)
sudo firewall-cmd --permanent --zone=home --add-service=rpc-bind
sudo firewall-cmd --permanent --zone=home --add-service=mountd

# újratöltés
sudo firewall-cmd --reload

# státusz ellenőrzés
sudo firewall-cmd --list-all --zone=home
```
### 1.2 Debian (ufw):
Telepítés (Debian):
```Bash
sudo apt install ufw -y
```
Alapbeállítások:
```Bash
# UFW engedélyezése, ha még nincs
sudo ufw enable

# SSH engedélyezése
sudo ufw allow ssh

# NFS alap port (2049)
sudo ufw allow 2049/tcp
sudo ufw allow 2049/udp

# rpcbind (111)
sudo ufw allow 111/tcp
sudo ufw allow 111/udp

# mountd (általában 20048)
sudo ufw allow 20048/tcp
sudo ufw allow 20048/udp

# statd (például 32765)
sudo ufw allow 32765/tcp
sudo ufw allow 32765/udp

# státusz ellenőrzése
sudo ufw status verbose
```
Ez biztosítja, hogy a kliens tudjon csatlakozni a szerverhez NFS-en keresztül, és SSH-val is elérhető marad.

---

[Vissza az előző oldalra](../raspberry-pi.md)
[Vissza a főoldalra](../../../README.md)

---