## Netzwerkdesign & Service-Isolation

In meinem Homelab habe ich das Netzwerk so aufgebaut, dass **Sicherheit, Übersicht und Wartbarkeit im Vordergrund stehen**.  

### Zugriff & Schutz

- **LAN/VPN-only Zugriff:**  
  Admin- und Service-Zugriffe erfolgen ausschließlich über das lokale Netzwerk oder über **Tailscale VPN**.  
- **Keine öffentliche Port-Exposition:**  
  Es gibt kein Portforwarding ins Internet. Selbst sensible Services wie Nextcloud oder Portainer sind nur intern erreichbar.  

**Mehrwert:** Minimaler Angriffsvektor, klare Trennung zwischen internen und potentiell externen Zugängen.

### Container-Netzwerke

- Jeder Container läuft in einem **eigenen Docker-Bridge-Netzwerk**.  
- Services wie Nextcloud und MariaDB können **isoliert kommunizieren**, während Pi-hole nur DNS-bezogene Anfragen empfängt.  
- Interne Netzwerke verhindern, dass Services unnötig auf das Hostnetzwerk zugreifen.  

**Mehrwert:** Isolierung erhöht Sicherheit, erleichtert Wartung und zukünftige Erweiterungen.

### Namensauflösung & Erreichbarkeit

- **Tailscale MagicDNS:** Jeder Container/Dienst kann über **eindeutige interne Namen** angesprochen werden, z. B. `nextcloud.local`.  
- Keine IP-Adressen merken oder manuell konfigurieren → weniger Fehleranfälligkeit.  

**Mehrwert:** Schnelle Administration, reproduzierbare Deployments, einfaches Onboarding neuer Dienste oder Nutzer.

### Design-Grundsätze

- **Minimaler Angriffsvektor:** nur interne Kommunikation, keine externen Ports  
- **Service-Isolation:** Containernetzwerke trennen kritische Services voneinander  
- **Transparenz & Dokumentation:** alle Netzwerke und Verbindungen sind dokumentiert, damit auch Nicht-Techniker die Infrastruktur nachvollziehen können  

> Ziel: Eine **sichere, wartbare und nachvollziehbare Infrastruktur**
