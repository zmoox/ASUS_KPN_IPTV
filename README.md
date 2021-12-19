# ASUS_KPN_IPTV
Collection of scripts and links to get your own asus router running on dutch KPN glasfiber internet. 

## Why use your own router?

* the cheapest KPN supplied router (KPN Box 12) is very basic in terms of functionality and in my case, extremely unstable (spontaneously rebooting every 30 mins or so)
* when you use the KPN router your wireless passwords are sent and stored at KPN servers for some reason.
* It's mandatory (as of December 2016) for internet providers to allow the use of your own router, but they are not extremely helpful about it.

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
