# Liberate Captive Portal Networks with Ubuntu
Liberate access to internet behind captive portals in Airplanes, Airports, etc for free public use. (Tested on Ubuntu 20.04 with airplane wifi)

## 1. Prepare system

Download and install necessary software and scripts before hand on network you already have access to.

### a). Install dependencies:
```
sudo apt -y install sipcalc nmap
```

### b). Get [Hack Captive Portals](https://github.com/systematicat/hack-captive-portals) Script:
```
wget https://raw.githubusercontent.com/systematicat/hack-captive-portals/master/hack-captive.sh
```

### c). Install [Linux Wifi Hotspot](https://github.com/lakinduakash/linux-wifi-hotspot) (Enables hotspot creation on linux machines using same wifi interface as reciever):
```
sudo add-apt-repository ppa:lakinduakash/lwh
sudo apt install linux-wifi-hotspot
```

## 2. Connect to internet with Captive Portal

Connect to public wifi network with entry paywall. 

## 3. Modify permissions and run Hack Captive Portals Script

```
sudo chmod u+x hack-captive.sh
sudo ./hack-captive.sh
```

If script successfully runs move on to step 4. 

## 4. Create open, public wifi hotspot to share free access to internet with others

Replace `Public Freenet` with preferred network name.

```
export WIFI_INTERFACE=$(iw dev | awk '$1=="Interface"{print $2}')
sudo create_ap $WIFI_INTERFACE $WIFI_INTERFACE 'Public Freenet' --freq-band 2.4
```
