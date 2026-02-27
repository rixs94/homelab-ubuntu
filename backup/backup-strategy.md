## Backup & Restore Strategie

Für mein Homelab ist **Datenintegrität und Ausfallsicherheit** entscheidend.  
Deshalb habe ich ein klares Backup- und Restore-Konzept geplant, auch wenn die Automatisierung noch implementiert werden muss.

### Ziele

- **RPO (Recovery Point Objective): 24h**  
  Datenverlust soll maximal auf 24 Stunden begrenzt sein.

- **RTO (Recovery Time Objective): <2h**  
  Nach einem Ausfall sollen alle kritischen Dienste innerhalb von 2 Stunden wieder verfügbar sein.

### Zu sichernde Komponenten

- **Nextcloud-Daten:**  
  Persistente Volumes enthalten alle Dateien und Dokumente.

- **MariaDB-Daten:**  
  Volumes oder regelmäßige Dumps sichern die Datenbank zuverlässig.

- **Pi-hole Konfiguration:**  
  Blocklisten, Filterregeln und Einstellungen werden gesichert, um DNS-Schutz sofort wiederherstellen zu können.

- **Portainer-Daten:**  
  Volumes enthalten alle Container-Stacks und Einstellungen.

### Status & Mehrwert

- Backups sind aktuell **geplant**, werden dokumentiert und nach Implementierung regelmäßig getestet.  
- **Vorteile dieses Konzepts:**  
  - Sicherer Betrieb ohne Datenverlust  
  - Reproduzierbarkeit: Volumes + Dumps → einfache Wiederherstellung  
  - Transparenz: Jeder Schritt dokumentiert, sodass Dritte die Strategie nachvollziehen können

> Ziel: Die Backup-Strategie zeigt, dass ich **kritische Daten im Homelab zuverlässig schützen** und im Notfall schnell wiederherstellen kann.
