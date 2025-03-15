
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Állománykezelés

---

> **Fontos!** Nem minden (a leírásban felsorolt) parancs tartozéka egy alaprendszernek, előfordulhat hogy telepítened kell.
>
> ---
>
> böngészőbe írva, a legtöbb telepített program leírása megtalálható
>
> ```shell
> file:///usr/share/doc
>```
>
> ---
>
> Alapértelmezett szövegszerkesztőnket a fenti paranccsal tudjuk módosítani (pl mcedit-re):
>
> ```shell
> update-alternatives --config editor
> ```
>
> ---
>
> A rendszer frissítése. (a tárolók -repository- az /etc/apt/sources.list file-ban vannak megadva.):
>
> ```shell
> sudo apt-get update && sudo apt-get upgrade
> ```
>
> ---

<details>
<summary>Rendszer információk</summary>

> ---
>
> ## parancs manual oldalainak angol nyelvű megjelenítése:
>
> ```shell
> man -L en parancs
> ```
>
> ---
>
> Minden olyan parancsot megad, mely manual oldalaiban szerepel a "word"
>
> ```shell
> apropos word
> ```
>
> ---
>
> Az apropos program kimenete:
>
> ```shell
> man -k word
> ```
>
> ---
>
> Információ a "parancs" használatáról:
>
> ```shell
> parancs --help
> ```
>
> ---
>
> Információ a "parancs" használatáról:
>
> ```shell
> info parancs
> ```
>
> ---
>
> Egysoros kiírás a parancsról:
>
> ```shell
> whatis parancs
> ```
>
> ---
>
> Hol van a parancs:
>
> ```shell
> whereis parancs
> ```
>
> ---
>
> A program futtatható állományának elérési útvonalát adja meg (általában /usr/bin):
>
> ```shell
> which parancs 
> ```
> ---

</details>

<details>
<summary>man</summary>

> ---
>
> ## A parancs manual oldalait nyitja meg, rövid, tömör, célratörő leírás
>
> ---
>
> ```shell
> man parancs
> ```
>
> ---

</details>

<details>
<summary>mc</summary>

> ---
>
> ## Midnight Commander (fájlkezelő)
>
> ---

</details>

<details>
<summary>mcedit</summary>

> ---
>
> ## Az mc szövegszerkesztője
>
> ---

</details>

<details>
<summary>pwd</summary>

> ---
>
> ## Az éppen aktuális könyvtár munkakönyvtár kiíratása
>
> ---

</details>

<details>
<summary>cd</summary>

> ---
>
> ## Könyvtár váltás parancs
>
> ---
>
> az aktuális felhasználó /home könyvtárába való belépéshez:
>
> ```shell
> cd
> ```
>
> ---
>
> az aktuális könyvtárhoz képest egy szinttel feljebb lépés a könyvtár fában:
>
> ```shell
> cd ..
> ```
>
> ---

</details>

<details>
<summary>mkdir</summary>

> ---
>
> ## Könyvtár létrehozása (make directory)
>
> ---
>
> A teljes struktúra létrehozása, almappákkal együtt:
>
> ```shell
> mkdir -p /home/user/1/2/3
> ```
>
> ---

</details>

<details>
<summary>rmdir</summary>

> ---
>
> ## Könyvtár törlés (remove directory)
>
> ---
>
> ```shell
> rmdir /home/user/temp
> ```
>
> ---

</details>

<details>
<summary>rm</summary>

> ---
>
> ## Állományok eltávolítása (remove)
>
> ---
>
> könyvtár eltávolítás:
>
> ```shell
> rm -d könyvtár
> ```
>
> ---
>
> rákérdez a törlés előtt:
>
> ```shell
> rm -i
> ```
>
> ---
>
> Könyvtárstruktúrát töröl (akkor is, ha nem üres):
>
> ```shell
> rm -rf
> ```
>
> ---

</details>

<details>
<summary>ls</summary>

> ---
>
> ## A könyvtárstruktúrát jeleníti meg
>
> ---
>
> méret szerint sorrendben:
>
> ```shell
> ls -lt
> ```
>
> ---
>
> utolsó módosítás szerint sorrendben:
>
> ```shell
> ls -ls
> ```
>
> ---
>
> minden 7 karakteres állományt jelenít meg:
>
> ```shell
> ls ???????
> ```
>
> ---
>
> a rejtett fájlokat is kiírja:
>
> ```shell
> ls -a
> ```
>
> ---
>
> fordított sorrendben írja ki. pl.: -nr : ABC fordított sorrendjében:
>
> ```shell
> ls -r ?
> ```
>
> ---
>
> azokat a 3 betűs fájlokat, melyek középső betűje a,e,s közül bármelyik:
>
> ```shell
> ls [aes]?
> ```
>
> ---
>
> azokat a fájlokat melyek n,m betűvel kezdődnek:
>
> ```shell
> ls [nm]*
> ```
>
> ---
>
> amelyek c-betűre végződnek:
>
> ```shell
> ls *c
> ```
>
> ---
>
> amely fájlok nem s-el kezdődnek:
>
> ```shell
> ls [^s]*
> ```
>
> ---
>
> kilistázza a könyvtár tartalmát, de a szó-t kihagyja:
>
> ```shell
> ls I szó
> ```
>
> ---

</details>

<details>
<summary>tree</summary>

> ---
>
> ## Könyvtárstruktúrát írja ki
>
> ---
>
> csak a mappákat adja meg:
>
> ```shell
> tree -d
> ```
>
> ---
>
> teljes path-al írja ki a file-ok elérési útvonalát:
>
> ```shell
> tree -f
> ```
>
> ---

</details>

<details>
<summary>file</summary>

> ---
>
> ## fájlok vizgálata
>
> ---
>
> megvizsgálja a file.txt fájl típusát:
>
> ```shell
> file file.txt
> ```
>
> ---
>
> Egy létező filelista állományban felsorolt file-okat vizsgálja meg:
>
> ```shell
> file -f *.txt
> ```
>
> ---
>
> Követi a szimbólikus link kötést (nem a linket, hanem az arra mutató file-t vizsgálja):
>
> ```shell
>cfile -L *.txt
> ```
>
> ---
>
> A file karakterkódolását mutatja meg:
>
> ```shell
> file --mime file.txt
> ```
>
> ---

</details>

<details>
<summary>cp</summary>

> ---
>
> ## Fájl, könyvtár másolásra használható parancs
>
> ---
>
> file_1 állományból készít file_2 nevű másolatot file_1 megtartásával:
>
> ```shell
> cp file_1 file_2
> ```
>
> ---
>
> rekurzívan mindent másol a /honnan/mit-ből a /hova mappába
>
> ```shell
> cp file -R /honnan/mit /hova
> ```
>
> ---

</details>

<details>
<summary>cat</summary>

> ---
>
> ## cat - Fájl tartalmát írja ki.
>
> ---
>
> kiírja a fájl tartalmát:
>
> ```shell
> cat file
> ```
>
> ---
>
> várja a bemenetet, amely a "file" tartalma lesz. Ctrl + D kombinációval menthető:
>
> ```shell
> cat > file
> ```
>
> ---
>
> beszámozza a file sorait:
>
> ```shell
> cat -n file
> ```
>
> ---
>
> Minden .sh kiterjesztésű, 2 betűs file tartalmát kiírja a képernyőre:
>
> ```shell
> cat ??.sh
> ```
>
> ---
>
> A CD tartalmának ISO-ban örténő mentése:
>
> ```shell
> cat /dev/cdrom > /eleresi/utvonal/cd.iso
> ```
>
> ---
>
> A rendszerbe felvett felhasználók kiíratása:
>
> ```shell
> cat /etc/passwd |grep "/home" | cut -d: -f1
> ```
>
> ---
>
> a cat beolvassa a bemenet.txt tartalmát és a kimenet.txt-be irányítja:
>
> ```shell
> cat < bemenet.txt > kimenet.txt
> ```
>
> ---
>
> A hibacsatorna is a kimenetre keverhető, azaz a file1.txt tartalma ÉS a lehetséges hibák is bekerülnek a file2.txt-be:
>
> ```shell
> cat file.txt 1> file2.txt 2>&1
> ```
>
> ---

</details>

<details>
<summary>echo</summary>

> ---
>
> ## szöveg kiíratása
>
> ---
>
> Kiírja a képernyőre a szoveg-et:
>
> ```shell
> echo szoveg
> ```
>
> ---
>
> a szoveg-et file-ba írja:
>
> ```shell
> echo szoveg > file
> ```
>
> ---
>
> $HOME nevű változó értékét adja meg, ami az aktuális user home-ja. pl /home/grunghar:
>
> ```shell
> echo $HOME
> ```
>
> ---

</details>

<details>
<summary>touch</summary>

> ---
>
> ## fájl létrehozás
>
> ---
>
> létrehoz egy file nevű üres állományt:
>
> ```shell
> touch file
> ```
>
> ---
>
> A fájl időbélyegeinek dátumát változtatja meg. MM-Hónap DD-Nap HH-Óra mm-Perc:
>
> ```shell
> touch -t MMDDHHmm file
> ```
>
> ---
>
> file időbélyegei alapján állítja be file2 időbélyegeit:
>
> ```shell
> touch -r file file2
> ```
>
> ---
>
> a file létrehozási dátumát állítja Március 9., 13:15-re:
>
> ```shell
> touch -a -t 03091315 file
> ```
>
> ---
>
> a file módosítási dátumát állítja Március 9., 13:15-re:
>
> ```shell
> touch -m -t 03091315 file
> ```
>
> ---
>
> dir nevű mappa összes állományának módosítási dátumát megváltoztatja az aktuális dátumra:
>
> ```shell
> find dir/ -name "*.*" -exec touch {} \;
> ```
>
> ---

</details>

<details>
<summary>du</summary>

> ---
>
> ## Az aktuális könyvtár fájljainak méretét adja meg
>
> ---
>
> Olvashatóbb formátumban írja ki a méreteket (MByte, GByte, stb.):
>
> ```shell
> - du -H
> ```
>
> ---
>
> A -h helyett már ezt a kapcsolót ajánlatos használni:
>
> ```shell
> - du --si
> ```
>
> ---
>
> 1 könyvtár mélységig vizsgál:
>
> ```shell
> du --max-depth=1
> ```
>
> ---

</details>

<details>
<summary>df</summary>

> ---
>
> ## Szabad terület számítása, partíciónként
>
> ---
>
> Olvashatóbb formátumban írja ki a méreteket (MByte, GByte, stb.):
>
> ```shell
> df -H
> ```
>
> ---
>
> A -H helyett már ezt a kapcsolót ajánlatos használni:
>
> ```shell
> df --si
> ```
>
> ---

</details>

<details>
<summary>find</summary>

> ---
>
> ## Keresés
>
> ---
>
> az összes kép keresése a gyökérben, majd az eredmény kiírása:
>
> ```shell
> find / -name "*.jpg" -print
> ```
>
> ---
>
> nincs kis és nagybetű különbség:
>
> ```shell
> find / -iname ...
> ```
>
> ---
>
> minden 777-es joggal rendelkező állomány keresése:
>
> ```shell
> find -perm 777
> ```
>
> ---
>
> Az összes SUID joggal rendelkező állományt keres:
>
> ```shell
> find -perm 4000
> ```
>
> ---
>
> 500kb-nál nagyobb állományok keresése a /home-ban:
>
> ```shell
> find /home -size +1024
> ```
>
> ---
>
> különböző típusú fájlokat keres:
>
> ```shell
> find -type "kapcsoló"
> ```
>
> ---
>
> szimbólikus link:
>
> ```shell
> find -type l
> ```
>
> ---
>
> könyvtárak:
>
> ```shell
> find -type d
> ```
>
> ---
>
> fájlok:
>
> ```shell
> find -type f
> ```
>
> ---
>
> Az /etc könyvtárban lévő üres könyvtárakat írja ki, a jogosultságaival együtt:
>
> ```shell
> find /etc -empty -maxdepth 1 -printf "%p-%m\n"
> ```
>
> ---
>
> 512kb-nál nagyobb,maximum 365*24 órája módosított állományokat, valamint a file parancs kimenetét -exec file{} \; jelenti, hogy az exec után levő parancsnak adja át az eredményt.
>
> ```shell
> find /home -size +1024 \( -mtime +365 -o -atime +365 \) -ls -exec file{} \;
> ```
>
> ---
>
> Keresési feltételek.: mkv kiterjesztésű ÉS 1000MB fölötti, VAGY ISO kiterjesztéső ÉS 500MB fölötti file-ok. Kis-nagy betű nem számít a kiterjesztésben:
>
> ```shell
> find -iname *.mkv -a -size +1000M -o -iname *.ISO -a -size +500M
> ```
>
> ---
>
> a gyökérben olyan txt állományokat keres, melyek tartalmában szerepel a "kifejezés" kifejezés:
>
> ```shell
> find . -name "*.txt" -print | xargs grep "kifejezés"
> ```
>
> ---
>
> adott DIR mappában a file-okra 660 jogot állít be, még akkor is ha szóköz van a nevében:
>
> ```shell
> find DIR/ -type f | xargs -I {} chmod -R 660 "{}"
> ```
>
> ---
>
> ugyanaz mint az előző, csak a szóközök nem mennek:
>
> ```shell
> find "DIR/" -type f | xargs chmod -v 660
> ```
>
> ---
>
> Mappákat keresi és azokra állít be 770 jogot:
>
> ```shell
> find "DIR/" -type d | xargs chmod -v 770
> ```
>
> ---

</details>

<details>
<summary>chmod</summary>

---

> ## Fájlokra, könyvtárakra vonatkozó jogok állíthatóak be ezzel a paranccsal
>
> ---
>
> Rekurzívan változtatja meg a jogosultságokat:
>
> ```shell
> chmod -R
> ```
>
> ---
>
> DAC (háromszintű diszkrécionális maszk) szerinti beállítás:
>
> - r-read (olvasás), w-write (írás), x-executable (futtatás) jogot jelent
> - Általános jogosultság lista felépítése: (ls -la paranccsal lekérdezhető)
> - tulajdonos (jele:U) | csoport felhasználó (jele:G) | mindenki más (jele:O)
> - A sor elején található "d" a directory, "-" a file jele.
> - Jogok nem csak szimbólikus jelekkel de számokkal is meghatározhatóak.
> - Számokkal.: 4-read, 2-write, 1-executable jog, összeadva, külön U,G,O-nak 
> - chmod 777 file : UGO-nak egyaránt minden jog. (4+2+1 4+2+1 4+2+1)
> - chmod 751 file : U-nak minden, G-nek írási és futtatási, O-nak futtatási jog.
>
> ---
>  
> Betűkkel: kinek+mit
>
> - chmod u+rwx file : Tulajdonosnak (U) r,w,x jog adása az adott file-ra.
> - chmod g+rx file  : Csoport felhasználónak (G) r,x jog beáll.
> - chmod a-rwx      : Mindenkitől (A-all) elveszünk minden jogot.
>
> ---

</details>

<details>
<summary>umask</summary>

> ---
>
> ## A file és könyvtár jogok beállításánál érdemes megemlíteni a umask-ot.
>
> ---
>
> - Az umask meghatározza, hogy milyen jogosultságot kapjanak az újonnan létrehozott file-ok, mappák.
> - Értéke alapértelmezés szerint 022. 
> - Jelentése.: File-ok 644-et, Mappák 755 jogokat kapnak. 
> - File-ok esetén 666-ból, 
> - Mappák esetében pedig 777-ből kell levonni a 022-t, így kapjuk meg a jogokat.
>
> ---

</details>

<details>
<summary>chown</summary>

> ---
>
> ## Fájlok, könyvtárak tulajdonosának (létrehozójának változtatása)
>
> ---
>
> Rekurzívan változtatja meg a tulajdonos(oka)t:
>
> ```shell
> chown -R
> ```
>
> ---
>
> Nem küld vissza hibaüzenetet a rendszer, ha valami nem sikerült:
>
> ```shell
> chown -f
> ```
>
> ---
>
> Szimbólikus linkeknél a link jogosultságainak beállítása:
>
> ```shell
> chown --no-dereference
> ```
>
> ---
>
> Szimbólikus linkeknél a file (amire a link mutat) jogok változtathatóak meg:
>
> ```shell
> chown --dereference
> ```
>
> ---

</details>

<details>
<summary>chgrp</summary>

> ---
>
> ## chgrp - Fájlok tulajdonosi csoportjának megváltoztatása
>
> ---
>
> Rekurzívan változtatja meg a csoportokat:
>
> ```shell
> chgrp -R
> ```
>
> ---
>
> Nem kapunk vissza hibaüzenetet, ha valami nem sikerült:
>
> ```shell
> chgrp -f
> ```
>
> ---
>
> csak azokat a file-okat írja ki, amelyeknek valóban megváltozott a csoportjuk:
>
> ```shell
> chgrp -c
> ```
>
> ---

</details>

<details>
<summary>lsattr</summary>

> ---
>
> ## Fájlok, könyvtárak attribútumát mutatja meg
>
> ---
>
> Rekurzívan mutatja meg az attribútumokat:
>
> ```shell
> lsattr -R
> ```
>
> ---
>
> minden file-t kilistáz, beleértve a .-al kezdődőeket is:
>
> ```shell
> lsattr -a
> ```
>
> ---

</details>

<details>
<summary>chattr</summary>

> ---
>
> ## Fájlok, könyvtárak attribútumát változtatja
>
> ```shell
> chattr +tulajdonság file
> ```
>
> ---
>
> Tulajdonságok:
> - A
>    - Nem változtatja meg a fájlok utolsó módosításának dátumát. (rendszergyorsító hatás)
> - a
>    - Csak hozzáfűzni tudunk a fájlhoz
> - c
>    - Automatikusan tömörítve kerül a lemezre, és kitömörítve kerül beolvasásra
> - d
>    - Ezekről az állományokról nem készül biztonsági másolat a dump parancs futtatásakor
> - s
>    - Paranoia mód. Törléskor azonnal megsemmisül minden bit-je.
> - S
>    - Minden változtatás azonnal lemezre íródik (sync hatás)
> - u
>    - A Fájl törlésekor az adat megmarad, később visszaállítható
>
> ---

</details>

<details>
<summary>cmp</summary>

> ---
>
> ## fájlok tartalmát hasonlítja össze
>
> ---
>
> Összehasonlítja a file1 és file2 fájlok tartalmát
>
> ```shell
> cmp file1 file2
> ```
>
> ---

</details>

<details>
<summary>diff</summary>

> ---
>
> ## Összehasonlítja a fájlok tartalmát, a különbséget pedíg az eredmény-be írja
>
> ---
>
> ```shell
> diff -u file1 file2 > eredmeny
> ```
>
> ---
>
> file1 és file2 összehasonlítása, az eredményt két egymás melletti oszlopba írja, de az egyezőségeket csak a bal oszlopban tűnteti fel:
>
> ```shell
> diff –y -–left-column file1 file2
> ```
>
> ---

</details>

<details>
<summary>cut</summary>

> ---
>
> ## Bement (stdin), vagy paraméterként megadott fájl minden sorának egy megadott részét vágja ki
>
> ---
>
> második mező értéke:
>
> ```shell
> cut -c2 fájl
> ```
>
> ---
>
> harmadik, ötödik mező, sorrend nem számít:
>
> ```shell
> cut -c3,5
> ```
>
> ---
>
> negyedik mezőig és a hatodiktól:
>
> ```shell
> cut -c-4,6-
> ```
>
> ---
>
> Kettősponttal elválasztott sorokban az első helyen lévő adatot adja vissza:
>
> ```shell
> cut -d: -f1
> ```
>
> ```shell
> echo Helló:nagy:Világ | cut -d: -f1
> ```
>
> Eredmény:
>
> ```shell
> Helló
> ```
>
> ---

</details>

<details>
<summary>colrm</summary>

> ---
>
> ## colrm - Fájlból oszlopokat távolít el
>
> ---
>
> adott bemeneti állomány első oszloptól az harmadikig töröl minden sorból:
>
> ```shell
> cat file | colrm 1 3
> ```
>
> eredmény:
>
> ```shell
> grunghar@uby:~/Documents/temp$ cat cat-test.txt 
> helló világ
> 1234
> 5678
> 9012
> 3456
> 7890
> 1234
> 5678
> 9012
> grunghar@uby:~/Documents/temp$ cat cat-test.txt | colrm 1 3
> ló világ
> 4
> 8
> 2
> 6
> 0
> 4
> 8
> 2
> ```
>
> ---

</details>

<details>
<summary>tr</summary>

> ---
>
> ## karakterek lecserélése, változtatása adott karaktersorban
>
> ---
>
> a vegyes szóban a kis betűket nagyra cseréli:
>
> ```shell
> echo vegyes | tr a-z A-Z
> ```
>
> ---
>
> az egyesek szóból kitörli az e betűket:
>
> ```shell
> echo egyesek | tr -d e
> ```
>
> ---
>
> ha a file.txt több szóból álló szöveget tartalmaz, a szavak mögötti szóközt újsor karakterre cseréli, azaz minden szó új sorba kerül egymás alá, a file2.txt-be irányítva
>
> ```shell
> cat file.txt | tr -cs '[a-zA-Z0-9]' '[\n*]' > file2.txt
> ```
>
> ---
>
> Ha a file.txt-ben több üres sor is van, az összes újsor karaktert összevonja, azaz üres sorokat töröl.
>
> ```shell
> cat file.txt | tr -s '\n' > file2.txt
> ```
>
> ---
>
> A file-ban a vesszők helyét új sor karakterre cseréli.
>
> ```shell
> tr , '\n' < file
> ```
>
> ---

</details>

<details>
<summary>fgrep</summary>

> ---
>
> ## Fájlokban, vagy stdin-ben keresek szöveget
>
> ---
>
> Megkeresi az összes olyan sort a file.txt-ben, ami tartalmat "abc"-t:
>
> ```shell
> fgrep "abc" file.txt
> ```
>
> ---

</details>

<details>
<summary>grep</summary>

> ---
>
> ## Szövegrészleteket keres fájlokban, valamint a kimenetben. A kapcsolók után kell megadni a file-t.
>
> ---
>
> - nem tesz különbséget kis és nagybetűk között
>    - -i
> - nem az előfordulási sorokat, hanem csak a fájl neveket listázza
>    - -l
> - azokat a fájl neveket adja meg, melyben nem szerepel a "minta".
>    - -L
> - azokat a sorokat adja meg, amikben nem szerepel a keresett szó
>    - -v
> - "-" -el kezdődő minta keresésekor hasznos kapcsoló. (nélküle érvénytelen kapcsoló hibát dob.)
>    - -e
> - csak teljes sorokkal való illeszkedést vizsgál
>    - -x
> - azokat a sorokat adja meg, melyekben a "B" és az "r" között bármilyen karakter szerepel.
>    - B.r
> - a kimenetben találhatóak meg azok a találatok, melyekben szerepel "h" vagy "a" betű.
>    - [ha]
> - azon sorok megadása, melyben szerepel 15,16,17,18
>    - 1[5678]
> - azon sorok megadása, melyben szerepel 15,16,17,18
>    - 1[5-8]
> - minden sor megtalálható a kimenetben, kivéve amelyben szerepel a "sajt" kifejezés.
>    - [^sajt]
> - Azokat a sorokat adja meg, melyek üresek.
>    - ^$
> - A sor elején található kis "h" betűre illeszkedik.
>    - ^h
> - olyan sorokat ad vissza, melyben A-4 karaktersor szerepel
>    - A[-]4
>
> ---
>
> - ertek1 vagy ertek2 -re keresése a file-ban, kis és nagybetű különbség nélkül.
>    - -i -E '(ertek1|ertek2)' file
> - ertek1 vagy ertek2 -re keresése a file-ban, kis és nagybetű különbség nélkül.
>    - -i -E 'ertek1|ertek2' file
> - ertek1 vagy ertek2 -re keresése a file-ban, kis és nagybetű különbség nélkül.
>    - -i -e ertek1 -e ertek2 file
>
> ---
>
> - a file-ban az ertek-et tartalmazó sorokat adja meg úgy, hogy az egyel előtte és utána levő sorokat is kiírja
>    - -A1 B1 ertek file
>
> ---
>
> - azon fájlok elérését és illeszkedő sorait adja meg a /etc-n belül, melyben szerepel a minta.
>    - -r minta /etc
>
> ---
>
> smb.conf tartalmának kiíratása úgy, hogy a # ÉS ; jelekkel kezdődő sorokat nem írja ki.
>
> ```shell
> grep '^[^#;]' /etc/samba/smb.conf
> ```
>
> ---

</details>

<details>
<summary>head</summary>

> ---
>
> ## Szűrő eszköz
>
> ---
>
> A fájl első 10 sorát írja ki:
>
> ```shell
> head
> ```
>
> ---
>
> A fájl első 100 sorát adja meg:
>
> ```shell
> head -n 100 file
> ```
>
> ---
>
> utolsó 7 sort már nem írja ki:
>
> ```shell
> head -n-7 file
> ```
>
> ---
>
> A fájl első 4 sorát írja ki. (megadható "-n 4"-el és "-n4"-el is. Az előjel mindig pozitív.):
>
> ```shell
> -n+4 file
> ```
>
> ---
>
> mindkét fájl első 4 karakterét írja ki:
>
> ```shell
> head -c4 file1 file2
> ```
>
> ---

</details>

<details>
<summary>tail</summary>

> ---
>
> ## Szűrő eszköz. A fájl utolsó sorait írja ki.
>
> ---
>
> A fájl tartalmát a második sortól mutatja meg:
>
> ```shell
> tail -n+2 file
> ```
>
> ---
>
> Egy fájl harmadik sorát így lehet kiíratni:
>
> ```shell
> tail -n+3 fájl | head -n1
> ```
>
> vagy
>
> ```shell
> head -n3 fájl | tail -n1
> ```
>
> ---

</details>

<details>
<summary>paste</summary>

> ---
>
> ## Fájlok vízszintes egyesítésére szolgál (párhuzamos egyesítés)
>
> ---
>
> Az egyes megadott fájlokból tabulátorral elválasztott sorokat ad ki a szabványos kimenetre.
> Ha nincs megadva fájl, vagy kötőjelet ("-") tesz a fájlnév helyett, a beillesztés a szabványos bemenetről olvassa be, és a kimenetet úgy adja meg, ahogy van, amíg meg nem ad egy megszakítási parancsot [Ctrl-c].
>
> ```shell
> paste fname lname
> ```
>
> Eredmény:
>
> ```shell
> grunghar@uby:~/Documents/temp$ paste fname lname 
> Géza	Kiss
> Éva	Nagy
> Gábor	Szabó
> Elek	Teszt
> Júlia	Jakab
> Áron	Kántor
> grunghar@uby:~/Documents/temp$
> ```
>
> ---
>
> Elválasztás "|" jellel:
>
> ```shell
> paste -d "|" fname lname
> ```
>
> Eredmény:
>
> ```shell
> grunghar@uby:~/Documents/temp$ paste -d "|" fname lname 
> Géza|Kiss
> Éva|Nagy
> Gábor|Szabó
> Elek|Teszt
> Júlia|Jakab
> Áron|Kántor
> grunghar@uby:~/Documents/temp$
> ```
>
> ---
>
> Elválasztás ":" jellel:
>
> ```shell
> paste -d ':' fname lname
> ```
>
> Eredmény:
>
> ```shell
> grunghar@uby:~/Documents/temp$ paste -d ":" fname lname 
> Géza:Kiss
> Éva:Nagy
> Gábor:Szabó
> Elek:Teszt
> Júlia:Jakab
> Áron:Kántor
> grunghar@uby:~/Documents/temp$
> ```
>
> ---

</details>

<details>
<summary>sed</summary>

> ---
>
> ## Stream editor, folyamatszerkesztő. A bemenetet a kimenetre másolja miközben megszerkeszti.
>
> ---
>
> Az "i" betűket "V" betűkre cseréli:
>
> ```shell
> echo "bicikli" | sed 's/i/V/g'
> ```
>
> kimenete:
> - bVcVklV
>
> ---
>
> a file-ból kiszűri a kommenteket és az üres sorokat:
>
> ```shell
> sed '/ *#/d; /^ *$/d' file
> ```
>
> ---
>
> file ban található /mnt/test elérési útvonalakat cseréli \\server\share -re az out file-ba irányítva.
>
> ```shell
> sed 's:/mnt/test:\\\\server\\share:g' file > out
> ```
>
> ---
>
> file tartalmának kiíratása úgy, hogy a DST= karaktersort kihagyja:
>
> ```shell
> sed s/DST=// file
> ```
>
> ---
>
> adott file-ban a kezdő "aaa" és végző "cdn" sorok közötti sorokat adja meg, beleértve a kezdő és végző sort is.
> **FONTOS**, hogy az "aaa" illeszkedni fog "aaaa" vagy "aaaaa"-ra is!
>
> ```shell
> sed -n '/aaa/,/cdn/p' file
> ```
>
> - a file tartalma:
>
> ```shell
>            zdk
>            aaa
>            b12
>            cdn
>            dke
>            kdn
> ```
>
> - a fenti parancs kimenete:
>
> ```shell
>            aaa
>            b12
>            cdn
> ```
>
> - ugyanez awk-val:
>
> ```shell
> awk '/aaa/,/cdn/' file
> ```
>
> ugyanaz mint a fenti sed parancs, annyi különbséggel, hogy a kezdő és végző karaktersor pontosan az lehet ami, tehát itt már az "aaa" nem fog illeszkedni az "aaaa"-ra.
>
> ```shell
> sed -n '/^aaa$/,/^cdn$/p' file
> ```
>
> ---

</details>

<details>
<summary>sort</summary>

> ---
>
> ## Sorba rendezés
>
> ---
>
> ABC sorrendbe rendezi a fájlt, az eredményt a kimenetbe írja:
>
> ```shell
> sort -b file
> ```
>
> ---
>
> fordított sorrendben rendez:
>
> ```shell
> sort -r file
> ```
>
> ---
>
> a sor elején levő számok szerint rendez:
>
> ```shell
> sort -n file
> ```
>
> ---
>
> az azonos sorokat csak egyszer írja ki:
>
> ```shell
> sort -u file
> ```
>
> ---
>
> 2 oszlopos file-ban a második oszlop alapján rendezi sorba:
>
> ```shell
> sort -k 2 file
> ```
>
> ---
>
> a fájl 2. oszlopának második karaktere alapján rendez:
>
> ```shell
> sort -k 2.2 file
> ```
>
> ---
>
> a fájl 3. oszlopának 3,4 és 5. karaktere alapján rendez:
>
> ```shell
> sort -k 3.3,3.5 file
> ```
>
> ---

</details>

<details>
<summary>rev</summary>

---

> ## (reverse lines) adott állományban a karakterek sorrendjének megfordítása
>
> ---
>
> cat abcNums
>> Fájl tartalma:
>
> ```shell
> abcdefghijklmnopqrstvwxyz
> 0123456789
> ```
>
> ---
>
> rev abcNums
>> kimenet:
>
> ```shell
> zyxwvtsrqponmlkjihgfedcba
> 9876543210
> ```
>
> ---

</details>

<details>
<summary>uniq</summary>

> ---
>
> ## Több sorból álló szövegben az ismétlődő sorokkal kezd valamit
>
> ---
>
> az egymás utáni azonos sorokból egyet hagy meg, és kiírja a sorok elején hogy hányszor ismétlődött az adott sor:
>
> ```shell
> uniq -c file
> ```
>
> ---

</details>

<details>
<summary>nl</summary>

> ---
>
> ## (number lines of files)  file-ok soronkénti beszámozása.
>
> ---
>
> sorszámozás balra zárt, nullák nélkül:
> - -n ln
>
> ---
>
> sorszámozás jobbra zárt, nullák nélkül:
> - -n rn
>
> ---
>
> sorszámozás jobbra zárt, nullázva:
> - -n rz
>
> ---
>
> rz kapcsolóval együtt a nullák számát lehet megadni:
> - -w4
>
> ---
>
> Elválasztó (separator) ":"
> - -s:
>
> ---
>
> Példa:
>
> ```shell
> nl -n rz -w4 -s: file
> ```
>
> kimenet:
>
> ```shell
> 0001:Linux
> 0002:Windows
> 0003:Macintosh
> ```
>
> ---

</details>

<details>
<summary>wc</summary>

> ---
>
> sor, szó, karakterek számítása
>
> ---
>
> a fájlban lévő karakterek száma:
>
> ```shell
> wc -m file
> ```
>
> ---
>
> a fájlban lévő bájtok száma:
>
> ```shell
> wc -c file
> ```
>
> ---
>
> a fájlban lévő szavak száma:
>
> ```shell
> wc -w file
> ```
>
> ---
>
> a fájlban lévő sorok száma:
>
> ```shell
> wc -l file
> ```
>
> ---

</details>

<details>
<summary>mkisofs</summary>

> ---
>
> Segédprogram ISO-k készítéséhez.
>
> ---
>
> korábbi verziókban cdrtools csomag tartalmazza!
>> ISO készítése a CD lemezünkről
>
> ```shell
> -r -o cd.iso /cdrom/
> ```
>
> ```shell
> mkisofs -J -V "Label" adat/ | sudo cdrecord dev=0,0,0 speed=32 -data -v > -eject driveropts=burnfree -
> ```
>
> ---

</details>

---

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---