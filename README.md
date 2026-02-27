# Homelab Ubuntu – Self-Hosting Infrastruktur

<div align="center">
  <img src="./architecture/diagramm.png" alt="Architekturdiagramm" width="400">
</div>

## Motivation

Ich wollte eine **vollständig nachvollziehbare, sichere Self-Hosting-Umgebung**, die stabil läuft, reproduzierbare Deployments ermöglicht und alle wichtigen Dienste containerisiert hostet.

**Problem:** Viele Tutorials zeigen nur Einzelservices, oft öffentlich erreichbar, ohne Monitoring oder Backup.  
**Lösung:** Containerisierte Services, Zugriff **nur über LAN/VPN**, Monitoring mit Netdata, klar dokumentierte Volumes und Backups.  
**Outcome:** Ein stabiles, reproduzierbares Homelab, das alle benötigten Dienste zuverlässig hostet und leicht zu warten ist.

## Server & Specs

| Komponente       | Details |
|-----------------|---------|
| CPU / RAM       | Intel i5 10400 / 32GB RAM |
| Storage         | 1x 2TB SSD |
| OS              | Ubuntu Server 24.04 LTS |
| Netzwerk        | LAN + Tailscale VPN (kein Portforwarding) |
| Container-Host  | Docker & Docker Compose |
| Monitoring      | Netdata (Dashboard & Alerts) |
| Zugriff         | Admin nur LAN/VPN, SSH Passwort (Key optional später) |

## Container-Stacks

| Dienst       | Zweck                       | Zugang            | Daten-Volume          |
|-------------|-----------------------------|-----------------|--------------------|
| Nextcloud    | Files & Collaboration       | LAN/VPN, 8080   | `nextcloud_data`   |
| MariaDB      | Datenbank für Nextcloud     | Intern          | `db_data`          |
| Pi-hole      | DNS-Filtering & Ads Block   | LAN/VPN, 53/8090| `pihole_data`      |
| Portainer    | Container Management        | LAN/VPN, 9443   | `portainer_data`   |

> Alle Container laufen in isolierten Docker-Netzwerken.

## Monitoring (Netdata)

- Echtzeit-Überwachung von CPU, RAM, Disk, Netzwerk  
- Alerts bei kritischen Schwellenwerten  
- Dashboard für schnelle Übersicht & Trendanalyse  

## Praktische Befehle

```bash
# Container Status prüfen
docker compose ps

# Logs einzelner Container in Echtzeit
docker logs -f nextcloud
docker logs -f pihole

# Health-Status aller Container
docker inspect -f '{{.Name}}: {{.State.Health.Status}}' $(docker ps -q)

# Container neu starten
docker compose restart

# Updates ziehen und deployen
docker compose pull
docker compose up -d
