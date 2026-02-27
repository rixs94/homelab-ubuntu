# Pi-hole

**Zweck:** DNS-Filter / Werbung blockieren im gesamten LAN  

**Aufbau:**  
- Container läuft isoliert, bindet nur die notwendigen Ports (53, 8090)  
- DNS-Anfragen aus dem LAN/VPN werden gefiltert  

**Zugriff:**  
- Admin-UI nur LAN/VPN, keine öffentliche Exposition  

**Besonderheiten & Mehrwert:**  
- Containerisierung erlaubt einfaches Update und Rollback  
- Konfiguration über persistentes Volume gesichert  
- Schützt alle Endgeräte im Netzwerk automatisch  

> Ziel: Schutz vor Werbung und Tracking bei gleichzeitig nachvollziehbarem Betrieb
