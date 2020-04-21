<p align="center"><img src="https://i.imgur.com/DIpuNTI.jpg"></p>

<p align="center">
<img src="https://img.shields.io/badge/Python-3-brightgreen.svg?style=plastic">
<img src="https://img.shields.io/badge/Docker-✔-blue.svg?style=plastic">
</p>

<p align="center">
  <a href="https://twitter.com/Blackeyenepal"><b>Twitter</b></a>
  <span> - </span>
  <a href="https://t.me/Blackeyenepal"><b>Telegram</b></a>
  <span> - </span>
  <a href="https://Blackeyenepal.github.io"><b>Blackeyenepal's Blog</b></a>
</p>

<p align="center">
  <br>
  <b>Available in</b>
  <br>
  <img src="https://i.imgur.com/1wJVDV5.png">
</p>

Concept behind LocHack is simple, just like we host phishing pages to get credentials why not host a fake page that requests your location like many popular location based websites. Read more on <a href="https://Blackeyenepal.github.io"> Blackeyenepal's Blog </a>.LocHack Hosts a fake website on **In Built PHP Server** and uses **Serveo** to generate a link which we will forward to the target, website asks for Location Permission and if the target allows it, we can get :

* Longitude
* Latitude
* Accuracy
* Altitude - Not always available
* Direction - Only available if user is moving
* Speed - Only available if user is moving

Along with Location Information we also get **Device Information** without any permissions :

* Operating System
* Platform
* Number of CPU Cores
* Amount of RAM - Approximate Results
* Screen Resolution
* GPU information
* Browser Name and Version
* Public IP Address
* IP Address Reconnaissance

**This tool is a Proof of Concept and is for Educational Purposes Only, LocHack shows what data a malicious website can gather about you and your devices and why you should not click on random links and allow critical permissions such as Location etc.**

## How is this Different from IP GeoLocation

* Other tools and services offer IP Geolocation which is NOT accurate at all and does not give location of the target instead it is the approximate location of the ISP.

* LocHack uses HTML API and gets Location Permission and then grabs Longitude and Latitude using GPS Hardware which is present in the device, so LocHack works best with Smartphones, if the GPS Hardware is not present, such as on a Laptop, LocHack fallbacks to IP Geolocation or it will look for Cached Coordinates.  

* Generally if a user accepts location permsission, Accuracy of the information recieved is **accurate to approximately 30 meters**, Accuracy Depends on the Device.

**Note** : On iPhone due to some reason location accuracy is approximately 65 meters.

## Templates

You can choose a template which will be used by LocHack from these : 

* NearYou
* Google Drive (Suggested by @Akaal_no_one)
* WhatsApp (Suggested by @Dazmed707)

## Tested On :

* Kali Linux 2019.2
* BlackArch Linux
* Ubuntu 19.04
* Kali Nethunter
* Termux
* Parrot OS

## Installation

### Kali Linux / Ubuntu / Parrot OS

```bash
git clone https://github.com/Blackeyenepal/LocHack.git
cd LocHack/
chmod 777 install.sh
./install.sh
```

### BlackArch Linux

```bash
pacman -S LocHack
```

### Docker

```bash
docker pull Blackeyenepal/LocHack
```

### Termux

```bash
git clone https://github.com/Blackeyenepal/LocHack.git
cd LocHack/
chmod 777 termux_install.sh
./termux_install.sh
```

## Usage

```bash
python3 LocHack.py -h

usage: LocHack.py [-h] [-s SUBDOMAIN]

optional arguments:
  -h, --help                              show this help message and exit
  -s SUBDOMAIN, --subdomain Subdomain 	  Provide Subdomain for Serveo URL ( Optional )
  -k KML, --kml KML                       Provide KML Filename ( Optional )
  -t TUNNEL, --tunnel TUNNEL              Specify Tunnel Mode [manual]

# Example

# SERVEO 
########
python3 LocHack.py

# NGROK ETC.
############

# In First Terminal Start LocHack in Manual mode like this
python3 LocHack.py -t manual

# In Second Terminal Start Ngrok or any other tunnel service on port 8080
./ngrok http 8080

#-----------------------------------#

# Subdomain
########### 
python3 LocHack.py --subdomain google
python3 LocHack.py --tunnel manual --subdomain zomato

#-----------------------------------#

# Docker Usage
##############

# SERVEO
########
docker run -t --rm Blackeyenepal/LocHack

# NGROK
#######

# Step 1
docker network create ngroknet

# Step 2
docker run --rm -t --net ngroknet --name LocHack Blackeyenepal/LocHack python3 LocHack.py -t manual

# Step 3
docker run --rm -t --net ngroknet --name ngrok wernight/ngrok ngrok http LocHack:8080
```

## Known Problems

* Services like Serveo and Ngrok are banned in some countries such as Russia etc., so if it's banned in your country you may not get a URL, if not then first READ CLOSED ISSUES, if your problem is not listed, create a new issue.

## Demo

<p align="center">
	<a href="https://www.youtube.com/watch?v=FEyAPjkJFrk"><img src="https://i.imgur.com/48yrleF.png"></a>
</p>
