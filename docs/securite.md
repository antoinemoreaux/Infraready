# Politique de Sécurité - InfraReady
- Aucun mot de passe en clair dans le dépôt Git.
- Utilisation d'**Ansible Vault** pour chiffrer les variables sensibles (`group_vars/windows.yml`).
- Validation syntaxique automatisée via GitHub Actions à chaque push.
