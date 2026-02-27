# Nextcloud

**Zweck:** Filesharing & Collaboration für private und familiäre Nutzung  

**Aufbau:**  
- Container läuft isoliert, Daten liegen in persistentem Volume `nextcloud_data`  
- Kommuniziert nur mit MariaDB Container über internes Docker-Netzwerk  

**Zugriff:**  
- LAN/VPN-only, Port 8080 intern erreichbar  
- SSL & Authentifizierung über Nextcloud-Konfiguration  

**Besonderheiten & Mehrwert:**  
- Volumes ermöglichen einfache Backups  
- Containerisierung sorgt für sauberen, reproduzierbaren Betrieb  
- Monitoring über Netdata für Ressourcenauslastung und Healthchecks  

> Ziel: stabile, sichere und wartbare File-Collaboration-Lösung
