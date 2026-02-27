# Monitoring mit Netdata – Homelab Ubuntu

Für mein Homelab setze ich **Netdata** ein, um **alle wichtigen System- und Service-Ressourcen in Echtzeit** zu überwachen.  
Ziel ist ein **stabiler Betrieb, frühzeitige Fehlererkennung und schnelle Analyse**, ohne dass manuelle Eingriffe ständig nötig sind.

## Ziele

- **Echtzeit-Überwachung**: CPU, RAM, Festplatte, Netzwerk, Prozesse  
- **Alerts bei kritischen Schwellenwerten**, um Ausfälle oder Engpässe zu vermeiden  
- **Zentrales Dashboard** für schnelle Übersicht aller Services  
- **Logs und Trendanalyse** zur Fehlerdiagnose und präventiven Optimierung

## Praxis & Funktionen

- **Systemressourcen**: Netdata zeigt CPU-Auslastung, Arbeitsspeicher, Swap, Disk I/O, Netzwerktraffic  
- **Service-Monitoring**: Dienste wie Nextcloud, Pi-hole und Portainer werden überwacht  
- **Alerts & Benachrichtigungen**: Kritische Zustände (z. B. hoher RAM-Verbrauch, Storage Engpässe) lösen sofort Warnungen aus
- **Dashboard-Zugriff**: Über LAN/VPN erreichbar, keine öffentliche Freigabe  
- **Historische Daten**: Langzeittrends analysieren, Kapazitätsplanung erleichtern  

## Mehrwert

- **Proaktives Monitoring**: Probleme werden erkannt, bevor sie kritisch werden  
- **Transparenz & Übersicht**: Alle Ressourcen und Services zentral sichtbar  
- **Troubleshooting**: Trends, Logs und Alerts erlauben gezielte Analysen  
- **Sicherer Betrieb**: Zugriff nur über LAN/VPN, keine externe Exposure  
