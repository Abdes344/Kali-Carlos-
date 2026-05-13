# Guia d'Exploració de Xarxa amb Netdiscover i Nmap

## 1. Mode actiu amb Netdiscover
Primer iniciarem sessio en el kali 

![netdiscover active mode](/AA4/IMG/1.png)

Abans de començar, mirem l'ajuda de netdiscover -h per conèixer les opcions com -r per definir el rang o -p per mode passiu.

![netdiscover help](/AA4/IMG/2.png)

Executem sudo netdiscover -r 192.168.2.0/24. Aquest mode envia peticions ARP i ens mostra IPs, MACs i fabricants dels dispositius detectats.

![netdiscover active scan result](/AA4/IMG/3.png)

## 2. Mode passiu amb Netdiscover

Executem sudo netdiscover -p. Aquí només escoltem el trànsit ARP sense enviar res.

![netdiscover passive mode result](/AA4/IMG/4.png)

## 3. Diferències entre els dos modes

El mode actiu descobreix més hosts perquè força respostes. El passiu és més discret però només detecta els dispositius que han generat trànsit de manera natural.

## 4. Exploració amb Nmap

Fem un ping sweep amb nmap -sn 192.168.2.0/24 per detectar hosts actius.

![nmap help options](/AA4/IMG/5.png)

El resultat mostra 4 hosts actius: 192.168.2.8, 192.168.2.11 i 192.168.2.13.

![nmap ping sweep result](/AA4/IMG/6.png)

## 5. Ports del router i servidor

Escanejarem el servidor amb nmap -O -sV 192.168.2.13. -O detecta el SO i -sV les versions dels serveis.

Resultat: ports 22 (SSH), 80 (HTTP), 443 (HTTPS) i 8080 (proxy) oberts. SO: Linux Ubuntu 22.04.

![nmap OS and services scan result](/AA4/IMG/7.png)
