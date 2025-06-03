# hello-world

```
docker run hello-world = docker create hello-world && docker start -a hello-world-id
```

---

# konténerek listázása

```
Docker ps
Docker ps -a
```

---

# image törlés

```
docker rm image-id
```

> összes image törlése

```
docker container prune
```

---

# docker konténer újraindítása

```
docker start container-id
```

> ha látni szeretném a lefutást a terminálon

```
docker start -a container-id
```

> indulástól a jelen pillanatig megnézem a log-ot

```
docker logs container-id
```

---

# docker leállítása

> finom leállítás -> kb. 10mp a leállásig

```
docker stop container-id
```

> kemény leállítás -> rögtön leáll

```
docker kill container-id
```

---

# docker futás közbeni parancs hozzáadás

```
docker exec container-id echo Bármilyen utsítás
```

> további parancsok hozzáadása (interaktivitás)

```
docker exec -it container-id echo Bármilyen utasítás
```

##### -i : kösd rá a lefuttatott programra ezt a terminált, hogy tudjak a programmal kommunikálni (további parancsokat átadni neki)
##### -t A kommunikáció legyen szintaktikailag formázott (legyen szép)

> **kilépés az interakcióból: ctrl+d**

> exec nélküli interakció:

```
docker run -it container-name/container-id
```

---

# image létrehozása

> fájlrendszer:

```
FROM alpine
```

> belső parancsok részlege (az image létrehozása előtt fut le):

```
RUN apk --update add openjdk7-jre
```

> (docker konténer elindítás előtt fut le)

```
CMD ["java", "-version"]
```

---

# docker build

```
docker build .
```

---

# Taggelés

```
docker build -t felhasznalonev/projektnev:latest .
```

> futtatás

```
docker run felhasznalonev/projektnev:latest
```

> vagy

```
docker run felhasznalonev/projektnev
```

---

# saját projekt létrehozása


---

# port átirányítás

```
docker run -p 8881:8888 felhasznalonev/projektnev
```


---

- []
