
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

### kellemetlen rendszerhangok, sípolások kikapcsolása arch rendszeren

| Leírás | Parancs |
| :----- | :------ |
| fájl módosítása, létrehozása | ```sudo nano /etc/modprobe.d/nobeep.conf``` |
|  ezeket a sorokat kell beleírni: | ```blacklist pcspkr```<br>```blacklist snd_pcsp``` |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---