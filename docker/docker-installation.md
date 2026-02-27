# Docker & Docker Compose Installation – Homelab Ubuntu

Dieser Abschnitt dokumentiert, wie ich **Docker und Docker Compose auf meinem Ubuntu Server 24.04 LTS** eingerichtet habe.  
Ziel ist, eine **stabile, sichere und reproduzierbare Umgebung** für alle Homelab-Services bereitzustellen.  
Die Installation dient **nicht nur dem Start der Container**, sondern zeigt auch, dass ich **komplexe Self-Hosting-Umgebungen professionell plane und betreibe**.

## Überblick

- **Containerisierung für Reproduzierbarkeit**: Alle Dienste laufen isoliert in eigenen Netzwerken  
- **Sichere Verwaltung**: Admin-Zugänge nur über LAN/VPN  
- **Volumensicherung**: Persistente Daten für Nextcloud, Pi-hole, Portainer  
- **Wartungsfreundlich**: Logs, Healthchecks, Updates einfach durchführbar

## Wichtige Schritte & Befehle

```bash
# System updaten
sudo apt update && sudo apt upgrade -y

# Abhängigkeiten für HTTPS-Repository installieren
sudo apt install -y ca-certificates curl gnupg lsb-release

# Docker GPG-Key hinzufügen
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Docker Repository hinzufügen
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Docker Engine installieren
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Version prüfen
docker --version
docker compose version

# Docker starten & beim Boot aktivieren
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker

# Benutzer zur Docker-Gruppe hinzufügen
sudo usermod -aG docker $USER
# Danach Docker-Befehle ohne sudo möglich
docker ps
