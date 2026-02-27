# Infrastruktur Allgemein

<div align="center">
  <img src="./diagramm.png" alt="Architekturdiagramm" width="400">
</div>

## Überblick

Ich habe eine **selbstgehostete Infrastruktur aufgesetzt**, die stabil, sicher und nachvollziehbar ist.  
Dieses Dokument zeigt **auf einen Blick**, wie die Umgebung aufgebaut ist, welche Services laufen und welche Überlegungen hinter der Architektur stehen.

## Plattform & Zugang

- **Hostsystem:** Ubuntu Server 24.04 LTS  
- **Containerisierung:** Docker & Docker Compose  
- **VPN & Netzwerk:** Tailscale VPN für sicheren externen Zugriff  
- **LAN-only Zugriff:** keine Ports ins öffentliche Internet  
- **Monitoring:** Netdata zeigt Ressourcen, Auslastung und Trends  

**Warum so:**  
- Nur LAN/VPN-Zugriff reduziert Sicherheitsrisiken  
- Containerisierung ermöglicht isolierte, leicht wartbare Dienste  
- Monitoring sorgt dafür, dass ich Probleme früh erkenne

## Services & Architektur-Flow

Alle Dienste laufen auf **einem zentralen Server**:

1. Zugriff erfolgt über LAN oder VPN  
2. Server verwaltet alle Container: Nextcloud, MariaDB, Pi-hole, Portainer  
3. Container sind isoliert, kommunizieren bei Bedarf miteinander  

**Mehrwert:**  
- Volumes für Daten → einfache Backups  
- Isolierte Netzwerke → Sicherheit & Klarheit  
- Healthchecks → stabiler Betrieb  
