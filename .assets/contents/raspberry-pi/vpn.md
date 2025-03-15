
---

```shell
sudo apt update && sudo apt upgrade -y
```

```shell
sudo passwd // if must
```

> vpn install

```shell
sudo apt install openvpn -y // install
```

```shell
cd /etc/openvpn // change directory
```

```shell
sudo wget https://www.privateinternetaccess.com/openvpn/openvpn.zip // download
```

```shell
sudo unzip openvpn.zip // unzipping
```

```shell
sudo openvpn --config ./Netherlands.ovpn
```

```shell
sudo nano login.conf // create new document
```

```shell
sudo chmod 400 login.conf
```

```shell
sudo cp Singapore.ovpn Singapore.conf
```

```shell
sudo nano Singapore.conf
```

```shell
-> auth-user-pass /etc/openvpn/login.conf
-> crl-verify /etc/openvpn/crl.rsa.2048.pem
-> ca /etc/openvpn/ca.rsa.2048.crt

-> Ctrl+x -> y -> [enter]
```

```shell
sudo openvpn Singapore.conf
```

```shell
sudo nano /etc/default/openvpn
```

```shell
-> AUTOSTART="Singapore"
-> Ctrl+x -> y -> [enter]
```

```shell
sudo shutdown -r 0
```

```shell
curl http://ipinfo.io/ip
```

---
