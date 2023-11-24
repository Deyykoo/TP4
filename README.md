# TP4

## I. DHCP Client
```	
🌞 Déterminer
- commande = ipconfig /all  
Serveur DHCP = 10.33.79.254  
bail obtenu =  vendredi 10 novembre 2023 08:59:04  
bail expirant = samedi 11 novembre 2023 08:59:02  

🌞 Capturer un échange DHCP

🌞 Analyser la capture Wireshark
- c'est la trame "offer" 
```

## II. Serveur DHCP
```	
🌞 Preuve de mise en place

ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.  
64 bytes from 8.8.8.8: icmp_seq=1 ttl=113 time=20.5 ms  
64 bytes from 8.8.8.8: icmp_seq=2 ttl=113 time=18.4 ms  

ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=113 time=19.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=113 time=24.4 ms

traceroute 64.233.160.0
traceroute to 64.233.160.0 (64.233.160.0), 30 hops max, 60 byte packets
gateway (10.4.1.254)  2.230 ms  2.513 ms  2.467 ms
10.0.3.2 (10.0.3.2)  4.854 ms  5.018 ms  4.355 ms

🌞 Rendu
    
- sudo nano /etc/resolv.conf
  ping ynov.com
  sudo dnf -y install dhcp-server
  sudo nano /etc/dhcp/dhcpd.conf


- systemctl status dhcpd
● dhcpd.service - DHCPv4 Server Daemon
     Loaded: loaded (/usr/lib/systemd/system/dhcpd.service; enabled; preset: disabled)
     Active: active (running) since Fri 2023-11-24 12:07:54 CET; 7min 37s ago
       Docs: man:dhcpd(8)
             man:dhcpd.conf(5)
   Main PID: 1501 (dhcpd)
     Status: "Dispatching packets..."
      Tasks: 1 (limit: 4672)
     Memory: 4.6M
        CPU: 28ms
     CGroup: /system.slice/dhcpd.service
             └─1501 /usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid
```	
