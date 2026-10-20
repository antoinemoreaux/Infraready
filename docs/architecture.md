# Architecture Technique - InfraReady
L'infrastructure repose sur un laboratoire à 3 machines virtuelles :
- **OPS01** : Contrôleur Ansible, superviseur (Prometheus / Grafana).
- **LINUX01** : Serveur d'application Linux (Ubuntu 24.04), Node Exporter.
- **WIN-DC01** : Contrôleur de domaine Windows Server (AD DS, DNS).
