# ASUS_KPN_IPTV
Collection of scripts and links to get your own asus router running on dutch KPN glasfiber internet. 

## Why use your own router?

* the cheapest KPN supplied router (KPN Box 12) is very basic in terms of functionality and in my case, extremely unstable (spontaneously rebooting every 30 mins or so)
* privacy: when you use the KPN router your wireless passwords are sent and stored at KPN servers for some reason.
* if you need more than 4 ethernet ports, the Asus RT-AC88U has 8 ports, versus 4 of the KPN Box 12 (not counting the WAN port).
* It's mandatory (as of December 2016) for internet providers to allow the use of your own router, but they are not extremely helpful about it.

## Manual

### Step 1: configure for internet access

* make sure your router is running a recent asuswrt-merlin firmware (see [asuswrt-merlin](https://www.asuswrt-merlin.net/)
* go to advanced settings - WAN, internet connection tab, then:
  - Basic Config:
    - WAN Connection Type : PPPoE 	
    - Enable WAN : Yes
    - Enable NAT : Yes
    - Enable UPnP : Yes
    - Enable secure UPnP mode : Yes
    - UPNP: Allowed internal port range 1024 to 65535
    - UPNP: Allowed external port range 1 to 65535
  - WAN IP Setting:
    - Get the WAN IP automatically : Yes
  - WAN DNS Setting:
    - Connect to DNS Server automatically :	Yes
    - Forward local domain queries to upstream DNS : No
    - Enable DNS Rebind protection : No
    - Enable DNSSEC support : No
    - Prevent client auto DoH : Auto	
    - DNS Privacy Protocol : None
  - Account Settings :
    - Username : internet
    - Password : internet
    - Disconnect after time of inactivity (in seconds) : 0 	
    - MTU : 1500 	
    - MRU : 1500 	
    - Service Name : empty
    - Access Concentrator Name : empty 	
    - Host-Uniq (Hexadecimal) : empty 	
    - Internet Detection : PPP Echo 	
    - PPP Echo Interval : 6 	
    - PPP Echo Max Failures : 10 	
    - Additional pppd options : empty
* go to advanced settings - LAN, IPTV tab, then:
  - LAN Port:
    - Select ISP Profile : Manual 	
    - Internet 	VID : 6 PRIO 0 
    - LAN Port 4 VID : empty PRIO 0 
    - LAN Port 3 VID : empty PRIO 0
  - Special applications:
    - Use DHCP routes : RFC3442
    - Enable multicast routing : Enable	
    - Enable Fast Leave : Enable
    - Enable efficient multicast forwarding (IGMP Snooping) : Enable 	
    - UDP Proxy (Udpxy) : 0
* Reboot the router

After these steps, you should be able to access the internet via the router.

### Step 2: configure for routed IPTV

* Go to advanced settings - Administration, system tab, then:
  - Service
    - Enable SSH : LAN only
  - Persistent JFFS2 partition:
    - Format JFFS partition at next boot : yes (set to NO after reboot, see below)
    - Enable JFFS custom scripts and configs : yes
* reboot the router to create and initialize the JFFS2 partition, then **MAKE SURE** to disabe JFFS2 formatting for subsequent reboots
* Use putty, ssh or winscp to upload the configs and scripts to the router:
  - upload the contents of .../configs to the routers /jffs/configs
  - upload the contents of .../scripts to the routers /jffs/scripts
* make sure the scripts are executable:
  - in ssh, execute the command `chmod a+rx /jffs/scripts/*`
* reboot and wait 30 seconds before powering on your IPTV settop box

## Script information
The scripts were sourced from [basho's post at tweakers.net](https://gathering.tweakers.net/forum/list_messages/1772709/0), with the following modifications:

* modified the wan-start to automatically locate the router's CPU port (or as stated in the manual, CPU address). This means you no longer have to edit the script, so you can skip that part from the manual.

## Tests
These scripts were verified to result in working internet plus routed IPTV on:

* novoip: ASUS RT-AC88U, using asuswrt-merlin firmware version 386.3_2
* voip: not tested

## links with information on how to configure your router:
* [bas hoogers manual, pdf](https://bashoogers.nl/tweakers/V4_HANDLEIDING_EIGENROUTERKPN.pdf)
* [bas hoogers manual, docx](https://bashoogers.nl/2021/12/03/kpn-glasvezel-openbaring-bronbestand-handleiding/)
* [official KPN information](https://www.kpn.com/service/eigen-modem-instellen-en-gebruiken.htm)
* [tweakers forum: Een eigen Asus router gebruiken](https://gathering.tweakers.net/forum/list_messages/1772709/0)
* [kpn forum: Gebruik een eigen router i.p.v. de Experia Box](https://forum.kpn.com/thuisnetwerk%2D72/gebruik%2Deen%2Deigen%2Drouter%2Di%2Dp%2Dv%2Dde%2Dexperia%2Dbox%2D458609)
* [xs4all (subsidiary of KPN) routed IPTV information](https://www.xs4all.nl/klant/instellingen-routed-mode-televisie-voor-ander-modem/)
* [berthub.eu raspberry pi alternative solution](https://berthub.eu/articles/posts/kpn-interactieve-tv-zelf-doen/)
