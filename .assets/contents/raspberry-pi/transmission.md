
---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---

# Transmission telepítése

---

> rendszer frissítése

```shell
sudo apt-get update && sudo apt-get upgrade
```

> telepítés

```shell
sudo apt-get install transmission-daemon
```

> program leállítás

```shell
sudo systemctl stop transmission-daemon
```

> beállítások

```shell
sudo nano /etc/transmission-daemon/settings.json
```

> ezeket a sorokat módosítsd:

```shell
"download-dir": "/var/lib/transmission-daemon/downloads",
"rpc-username": "felhasznalo",
"rpc-password": "jelszo",
"rpc-whitelist": "192.168.*.*",
```

> Ctrl+x -> y -> [enter]

> minden jog megadása a torrent könyvtárának:

```shell
sudo chmod 777 -R /könyvtár
```

> program indítása

```shell
sudo systemctl start transmission-daemon
```


> webes belépés

```shell
http://RPi IP címe:9091/transmission/
```

> vagy

```shell
http://RPi IP címe:9091
```

---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---