
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Unsnap és Flatpak telepítés

> snap csomagok listázása

```shell
snap list
```

> csomagok törlése ebben a sorrendben

```shell
sudo snap remove --purge firefox
sudo snap remove --purge snap-store
sudo snap remove --purge gnome-3-38-2004
```

```shell
sudo snap remove --purge gtk-common-themes
sudo snap remove --purge snapd-desktop-integration
sudo snap remove --purge bare
sudo snap remove --purge core20
sudo snap remove --purge snapd
```

```shell
sudo apt remove --autoremove snapd
```

> a snap végleges letiltása

```shell
sudo -H gedit /etc/apt/preferences.d/nosnap.pref
```

> beleírni a fájlba

```shell
Package: snapd
Pin: release a=*
Pin-Priority: -10
```

> a rendszer csomagok frissítése

```shell
sudo apt update
```

> a törlések után a megfelelő csomagok visszaállítása snap nélkül

```shell
sudo apt install --install-suggests gnome-software
```

> majd a Firefox telepításe PPA-ból

```shell
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install -t 'o=LP-PPA-mozillateam' firefox
```

> firefox automatikus frissítésének bekapcsolása

```shell
echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
```

> majd létrehozok egy másik preferenciafájlt a Firefox számára, hogy magas prioritást biztosítson a Firefox számára, különben a rendszer automatikusan visszatelepíti a snap-et és egyéb csodás dolgait 

```shell
sudo -H gedit /etc/apt/preferences.d/mozillateamppa
```

> fájlba beleírni

```shell
Package: firefox*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 501
```

---

### Flatpak telepítése

```shell
sudo apt install flatpak
```

> a továbbiakban, hogy ne kelljen mindig termiálból telepíten, hanem a csomagkezelőből is lehessen

```shell
sudo apt install gnome-software-plugin-flatpak
```

> Falthub engedélyezése

```shell
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

> majd végül, újraindítás

```shell
sudo reboot
```

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---