# Firewall-Konfiguration mit UFW

Für mein Homelab setze ich **UFW (Uncomplicated Firewall)** ein, um den Zugriff **streng auf interne Netzwerke und VPNs** zu beschränken.  
Alle Ports sind gezielt freigegeben, **Standardzugriffe blockiert**.

## Grundprinzip

- **Default deny incoming**: Alle eingehenden Verbindungen standardmäßig blockieren  
- **Default allow outgoing**: Ausgehende Verbindungen standardmäßig erlauben  
- **Gezielte Freigaben**: Nur für interne Netzwerke und VPN-Bereiche  

## Beispielkonfiguration

```bash
# Standardrichtlinien
sudo ufw default deny incoming
sudo ufw default allow outgoing

# SSH Zugriff nur aus internen Netzen
sudo ufw allow from 192.168.X.0/24 to any port 22
sudo ufw allow from 10.X.X.0/24 to any port 22

# DNS (Pi-hole) nur intern
sudo ufw allow from 192.168.X.0/24 to any port 53
sudo ufw allow from 10.X.X.0/24 to any port 53

# HTTP/HTTPS nur intern
sudo ufw allow from 192.168.X.0/24 to any port 80
sudo ufw allow from 192.168.X.0/24 to any port 443
sudo ufw allow from 10.X.X.0/24 to any port 80
sudo ufw allow from 10.X.X.0/24 to any port 443

# Weitere Services / Web-UIs nur intern
sudo ufw allow from 192.168.X.0/24 to any port 8080
sudo ufw allow from 10.X.X.0/24 to any port 8080
sudo ufw allow from 192.168.X.0/24 to any port 9443
sudo ufw allow from 10.X.X.0/24 to any port 9443
sudo ufw allow from 192.168.X.0/24 to any port 19999
sudo ufw allow from 10.X.X.0/24 to any port 19999

# Firewall aktivieren
sudo ufw enable

# Status prüfen
sudo ufw status verbose
