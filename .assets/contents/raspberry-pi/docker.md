
---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---

# Docker

---

## Esetleges régi verzió törlése

```shell
sudo apt-get remove docker docker-engine docker.io containerd runc
```

## Repository beállítása


> Rendszer frissítése

```shell
sudo apt update
```

> csomagok telepítése

```shell
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

## Docker GPG kulcs hozzáadása

> könyvtár létrehozás

```shell
sudo mkdir -p /etc/apt/keyrings
```

> GPG kulcs másolása a könyvtárba

```shell
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

## Repository beállítása:

```shell
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```  

## Docker telepítése

> Rendszer frissítése:

```shell
sudo apt-get update
```

---

> GPG hiba üzenet a frissítés futtatásakor?
> Lehetséges, hogy az alapértelmezett umask rosszul van konfigurálva, ami miatt nem lehet a kulcsot olvasni. A frissítés előtt olvasási engedélyt kell adni a docker nyilvános kulcsának:

```shell
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```

---

## Docker-engine, konténer és docker-compose telepítés

```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

## A hello-world image futtatásával ellenőrizzük a docker-engine sikeres telepítését:

```shell
sudo docker run hello-world
```

---

## Docker 'sudo' megkerülése/kiktatása

> docker csoport létrehozása:

```shell
sudo groupadd docker
```

> a felhasználó hozzáadása a csoporthoz

```shell
sudo gpasswd -a $USER docker
```

> majd végül sudo nélküli futtatás:

```shell
docker run hello-world
```

---

- [Back to the first page](../../../README.md)
- [Back to the Raspberry Pi](../raspberry-pi.md)

---