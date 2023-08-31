# Huhnitor
* Tools by spacehuhn for hacking a wifi
* Could be used as scan, deauthentication, fake ap with evilportal
* Devices : NodeMCU, ESP8266, deauther DSTIKE, deauther Watch DSTIKE
* Tested devices : NodeMCU
# Installing driver of USB (could be CP21x, FT23X, CH340G, PL23X)
(In my case, it's [CP21x](https://drive.google.com/file/d/18dX5ws61_A4EaHKuIYNDSMMeMPuJHZG5/view?usp=drive_link))
* [CH34xG](https://www.wch-ic.com/downloads/CH341SER_ZIP.html)
* [FTDI and FT232RL](https://ftdichip.com/drivers/)
* [CP210x](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)

# Finding port of NodeMCU
* Plug NodeMCU
* search : "devices manager" and click it
* click "Ports (COM and LTP)"
* remind the number of port come noted as COMX
* click on COMx and click "all parameters" memories the baudrates note as Y 
* Close all

# Downloading firmeware of deauther (v2 or v3)
* [v2](https://drive.google.com/file/d/1SDlyzD_QpOFj55N8Bah1HXs3y6TlexMn/view?usp=drive_link)
* [v3](https://drive.google.com/file/d/1WL7oKunPQWnsbr8DNvbqR_WbKbHOmUb9/view?usp=drive_link)
  
# Installing  NodeMCU flash imager
* Download [NodeMCU_flash_imager](https://drive.google.com/file/d/1M3NqRjzG0mOo1vpVfecNPRZFp75qAmy6/view?usp=drive_link)
* Install nodemcu_imager 

# Flashing deauther 
* Connect D3 with GND
* Run NodeMCU flasher at  :
  nodemcu-flasher-master\nodemcu-flasher-master\Win64\Release\ESP8266Flasher.exe
  or
  nodemcu-flasher-master\nodemcu-flasher-master\Win32\Release\ESP8266Flasher.exe
* In operation, Change port com as COMx
* In config, change with the firmeware v2 or v3
* In Advanced, change bauderate as Y at the first step
* After successfull flashing, don't connect D3 with GND anymore
  
# Installing huhnitor
(in my case, I use ubuntu 22.04)  
```
sudo snap install huhnitor --edge --devmode  
```

# Testing huhnitor command
use command :  
```
Huhnitor
```
```
scan  
```
```
ap -s fakenet  
```

# Remark about deauther v2 (it's possible to use fonctionnality using web app)
SSID : spacehuhn or pwned  
Password : deauther  
1.Scan for WiFi networks.  
2.Connect to pwned with the password deauther.  
3.Open 192.168.4.1 (or deauth.me)  
* [scan](http://deauth.me/scan.html)
* [ssids](http://deauth.me/ssids.html)
* [attack](http://deauth.me/attack.html)

[using](https://github.com/SpacehuhnTech/esp8266_deauther/wiki/Web)  



# Container and Huhnitor
```
lxc launch images:ubuntu/jammy/amd64 Huhnitor
```
```
lxc exec Huhnitor -- bash
```
```
apt update 
```
```
apt-get install snap snapd
```
```
snap install huhnitor --edge --devmode
```
```
reboot
```
```
lxc exec Huhnitor -- bash
```
For mine : 
Instance published with fingerprint: e76e32fa59919dca732bdf5b46b3ab47559cd0862931be8dd67964a6ebd4b9dd

# Exporiting Huhnitor LXC

```
lxc publish Huhnitor --alias Huhnitor -f
```
```
lxc image export Huhnitor .
```
```
e76e32fa59919dca732bdf5b46b3ab47559cd0862931be8dd67964a6ebd4b9dd.tar.gz
```
For mine 
d653c47b031144436ea03ead1f05d2f8  e76e32fa59919dca732bdf5b46b3ab47559cd0862931be8dd67964a6ebd4b9dd.tar.gz


# Importing Huhnitor LXC
[huhnitor image](https://drive.google.com/file/d/1QTrw_xwmDjhrvSVFCb4rZHBCsixaisAO/view?usp=drive_link)
using wget
```
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1QTrw_xwmDjhrvSVFCb4rZHBCsixaisAO' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1QTrw_xwmDjhrvSVFCb4rZHBCsixaisAO" -O e76e32fa59919dca732bdf5b46b3ab47559cd0862931be8dd67964a6ebd4b9dd.tar.gz  && rm -rf /tmp/cookies.txt  
```
```
lxc import image e76e32fa59919dca732bdf5b46b3ab47559cd0862931be8dd67964a6ebd4b9dd.tar.gz
```
```
lxc launch e76e32fa5991 Huhnitor
```





# Documentations : 
* https://blog.spacehuhn.com/difference-between-the-deauther-v2-and-v3
* https://www.pololu.com/docs/0J7/all
* https://github.com/nodemcu/nodemcu-flasher
* https://github.com/SpacehuhnTech/Huhnitor
* https://deauther.com/docs/version3/
* https://github.com/SpacehuhnTech/esp8266_deauther/tree/v3
* https://blog.spacehuhn.com/install-deauther
* https://github.com/SpacehuhnTech/esp8266_deauther/releases
* https://github.com/SpacehuhnTech/esp8266_deauther/wiki/Installation
* https://github.com/SpacehuhnTech/nightly-deauther/releases/tag/nightly
