
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

<!--
# UFW

---

### Csomagtárolók és rendszer frissítése majd az UFW telepítése:

> frissítés:

```shell
sudo apt update && sudo apt full-upgrade -y
```

> telepítés:

```shell
sudo apt install ufw
```

---

### Port hozzáférés engedélyezése

> sudo ufw allow PORTSZÁM

> ssh port engedélyezése:

```shell
sudo ufw allow 22
```

---

### Sebességkorlátozás a port-on

> ez a funkció hasznos az SSH kapcsolatok korlátozására.

> Megnehezíthetjük egy külső forrás számára a kapcsolat erőszakos kényszerítését.

> Az ufw nem engedélyez 6 vagy több csatlakozást 30 másodpercen belül.

> Beállításhoz az "ufw limit PORTSZÁM"-ot kell használni.

> pl.:

```shell
sudo ufw limit 22
```

-->

# UFW: Az alapoktól a haladó beállításokig

## 1. Bevezetés az UFW-be és az alapvető műveletek

- Mi az UFW? Az UFW (Uncomplicated Firewall) egy felhasználóbarát felület a netfilter tűzfal rendszer számára. Célja, hogy leegyszerűsítse a tűzfal szabályok kezelését a parancssorból.
- Miért érdemes használni?
    - Egyszerűség: A bonyolult iptables parancsok helyett intuitív szintaxist kínál.
    - Biztonság: Segít megvédeni a rendszert a nem kívánt bejövő kapcsolatoktól.
    - Rugalmasság: Lehetővé teszi a szabályok finomhangolását a specifikus igények szerint.

### Az UFW állapotának ellenőrzése:
```Bash
sudo ufw status
```

Ez a parancs megmutatja, hogy az UFW engedélyezve van-e, és milyen szabályok vannak érvényben. Ha még nem aktív, valószínűleg a következő üzenetet látod: ```"Status: inactive"```.

### Az UFW engedélyezése:
```Bash
sudo ufw enable
```

Ezzel a paranccsal aktiválod az UFW-t. Figyelem! Amikor engedélyezed, az alapértelmezett bejövő házirend (```policy```) általában ```"deny"``` (tiltás), ami azt jelenti, hogy minden bejövő kapcsolatot blokkol, hacsak nincs rá kifejezett engedélyező szabály.

### Az UFW letiltása:
```Bash
sudo ufw disable
```

Ez a parancs kikapcsolja az UFW-t és törli az összes betöltött szabályt. Csak akkor használd, ha feltétlenül szükséges, mivel védtelenül hagyja a rendszeredet.

## 2. Alapértelmezett házirendek és bejövő/kimenő forgalom

- Alapértelmezett házirendek (default policies):
    - Bejövő (incoming): Alapértelmezetten az UFW letilt minden bejövő kapcsolatot, ha nincsenek specifikus engedélyező szabályok. Ezt a sudo ufw default deny incoming parancs rögzíti, de ez az alapértelmezett beállítás az engedélyezéskor.
    - Kimenő (outgoing): Alapértelmezetten az UFW engedélyez minden kimenő kapcsolatot. Ezt a sudo ufw default allow outgoing parancs rögzíti.
    - Ezeket az alapértelmezett viselkedéseket módosíthatod, de biztonsági szempontból ajánlott a bejövő forgalom tiltása, és csak a szükséges portok engedélyezése.

Az alapértelmezett házirendek beállítása (ha szükséges):
```Bash
sudo ufw default deny incoming  # Bejövő forgalom tiltása alapértelmezetten
sudo ufw default allow outgoing # Kimenő forgalom engedélyezése alapértelmezetten
```

Ezek a parancsok felülírják az alapértelmezett viselkedést, ha korábban módosítottad volna. Az ufw enable parancs a fenti beállításokat alkalmazza.

### Specifikus portok engedélyezése (bejövő):
SSH (22-es port): Az SSH hozzáférés engedélyezése elengedhetetlen, ha távolról akarsz csatlakozni a szerverhez.
```Bash
sudo ufw allow ssh
# vagy
sudo ufw allow 22/tcp
```
HTTP (80-as port): Ha web szervert futtatsz (pl. Apache, Nginx).
```Bash
sudo ufw allow http
# vagy
sudo ufw allow 80/tcp
```
HTTPS (443-as port): Biztonságos webforgalomhoz.
```Bash
sudo ufw allow https
# vagy
sudo ufw allow 443/tcp
```
Porttartományok engedélyezése:
```Bash
sudo ufw allow 6000:6007/tcp
```
Specifikus portok tiltása (bejövő):
```Bash
sudo ufw deny 23/tcp # Például telnet tiltása
```
Szabályok törlése:
```Bash
sudo ufw delete allow 22/tcp
# vagy törölheted a szabály sorszáma alapján (először listázd a szabályokat számozással)
sudo ufw status numbered
sudo ufw delete <szabály sorszáma>
```
## 3. Haladó szabályok és IP-cím alapú szűrés

Hozzáférés engedélyezése egy specifikus IP-címről:
```Bash
sudo ufw allow from 192.168.1.100 to any port 22
```
Ez a szabály csak az 192.168.1.100 IP-címről érkező SSH kapcsolatokat engedélyezi.
### Hozzáférés engedélyezése egy alhálózatról:
```Bash
sudo ufw allow from 192.168.1.0/24 to any port 80
```
Ez a szabály az 192.168.1.0/24 alhálózatról érkező HTTP kapcsolatokat engedélyezi.
Hozzáférés tiltása egy specifikus IP-címről:
```Bash
sudo ufw deny from 203.0.113.5
```
Ez a parancs blokkol minden bejövő kapcsolatot a 203.0.113.5 IP-címről.
Hozzáférés korlátozása (rate limiting): Az UFW képes korlátozni a kapcsolatok számát, ami segíthet a brute-force támadások elleni védekezésben.
```Bash
sudo ufw limit ssh
# vagy
sudo ufw limit 22/tcp
```
Ez a szabály blokkolja azokat az IP-címeket, amelyek túl sok kapcsolatot próbálnak létesíteni rövid időn belül. Alapértelmezés szerint 6 kapcsolatot engedélyez 30 másodpercen belül.
## 4. Az UFW naplózásának (logging) beállítása
A naplózás elengedhetetlen a hálózati forgalom felügyeletéhez és a biztonsági problémák azonosításához.
### Naplózás bekapcsolása:
```Bash
sudo ufw logging on
```
Naplózás kikapcsolása:
```Bash
sudo ufw logging off
```
### Naplózási szint beállítása (opcionális):
- low: Nagyon kevés naplóbejegyzés.
- medium: Alapértelmezett, mérsékelt mennyiségű napló.
- high: Részletes naplóbejegyzések.
```Bash
sudo ufw logging medium
```
A naplófájlok megtekintése: Az UFW naplóbejegyzései általában a /var/log/syslog vagy a /var/log/ufw.log fájlban találhatók.
```Bash
tail -f /var/log/syslog | grep UFW
```
Ez a parancs valós időben mutatja az UFW-hez kapcsolódó naplóbejegyzéseket.

## 5. Speciális UFW funkciók és tippek
UFW profilok: Egyes alkalmazások UFW profilokat regisztrálhatnak, így egyszerűbben engedélyezhetők.
```Bash
sudo ufw app list # Megmutatja az elérhető profilokat
sudo ufw allow 'Apache Full' # Például Apache engedélyezése HTTP és HTTPS forgalomra
```
Szabályok beszúrása (insert): Ha egy szabályt egy adott pozícióba szeretnél beszúrni a szabálylistában.
```Bash
sudo ufw insert 1 allow from 192.168.1.50 to any port 22
```
Ez a szabály az első pozícióba kerül, megelőzve az esetlegesen meglévő tiltó szabályokat.
### UFW visszaállítása alapállapotba (reset):
```Bash
sudo ufw reset
```
FIGYELEM: Ez a parancs töröl minden UFW szabályt és visszaállítja az UFW alapértelmezett állapotát (ami inaktív). Különösen óvatosan használd távoli szerveren, mert elveszítheted a hozzáférést!

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---