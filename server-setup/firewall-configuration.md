# Firewall (UFW)

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22    # SSH
sudo ufw allow 80    # HTTP (intern)
sudo ufw allow 443   # HTTPS (intern)
sudo ufw enable
sudo ufw status verbose
