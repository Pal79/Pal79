
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Érintőkijelző

---

> Ha nem tudod érintéssel görgetni a webböngésző tartalmát:

| Leírás | Parancs |
| :----- | :------ |
| nyisd meg szerkesztésre a fájlt: | ```sudo nano /etc/security/pam_env.conf``` |
|  majd add hozzá a fájlhoz: | ```MOZ_USE_XINPUT2 DEFAULT=1``` |
| mentés majd újraindítás | ```Ctrl+x >>> y```<br>```sudo shutdown -r now``` |
|  |  |
| ha így sem működik, akkor nyisd meg a vebböngésződ és írd be: | ```about:config``` |
| majd keresd meg ezt | ```dom.w3c_touch_events.enabled=2``` |
|  majd írd át: | ```dom.w3c_touch_events.enabled=1``` |
| ezután indítsd újra a rendszert. |  |

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---