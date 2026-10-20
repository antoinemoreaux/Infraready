# Procédure de Maintenance et Mises à Jour - InfraReady

## 1. Maintenance Automatisée Linux (LINUX01)

### Précautions :
- Réaliser un snapshot VMware de la VM `LINUX01`.
- S'assurer de la viabilité des services avant exécution.

### Exécution Ansible :
```bash
ansible-playbook -i inventory/hosts.yml playbooks/maintenance.yml -K
