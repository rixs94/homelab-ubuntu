# Homelab Ubuntu – Self-Hosting Infrastruktur

Eigenständig geplantes und betriebenes **Linux Homelab** auf **Ubuntu Server 24.04 LTS**, mit Fokus auf:

- **Stabilität & Betriebssicherheit**
- **Reproduzierbare Container-Deployments**
- **Zugriff nur über LAN/VPN** (keine öffentliche Exposure)
- **Dokumentierte Wartungsprozesse**

---

## Ergebnis

- Produktiv genutzte Container-Stacks:
  - **Nextcloud** – Files/Collaboration
  - **MariaDB** – Datenbank für Nextcloud
  - **Pi-hole** – DNS-Blocking
  - **Portainer** – Container-Management
- Admin-Zugriff ausschließlich über LAN oder VPN
- Monitoring etabliert für Ressourcen, Verfügbarkeit und Trends
- Betriebsdokumentation: Start/Update/Logs, Wartung, Troubleshooting

---

## Tech-Stack

- Ubuntu Server 24.04 LTS
- Docker & Docker Compose
- Netdata (Monitoring)
- Tailscale (VPN, MagicDNS)

---

## Verantwortungsbereiche

- **Build & Run:** Provisionierung, Container-Deployments, Updates  
- **Stabilität:** Health-Checks, Log-Analyse, Kapazitätsüberwachung  
- **Security by Design:** Minimierung Angriffsfläche, getrennte Admin-Zugänge  
- **Betriebsprozesse:** Wartungsroutinen, Backup & Restore

---

> Hinweis: Dieses Repo enthält **nur Dokumentation und Beispiel-Konfigurationen**, keine echten Passwörter oder Daten. 
