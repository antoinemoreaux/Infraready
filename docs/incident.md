# Rapport de Diagnostic d'Incident - InfraReady

## 1. Description de l'Incident
- **Composant impacté :** Canal d'alerte Grafana / Webhook Discord.
- **Symptôme :** Les alertes de supervision déclenchées par Prometheus/Grafana ne parviennent plus sur le canal Discord de l'équipe d'administration.

## 2. Démarche de Diagnostic et Investigations
1. **Vérification dans Grafana :**
   - Consultation des logs Grafana (`/var/log/grafana/grafana.log`) et de la section *Alerting > Contact points*.
   - Observation d'erreurs de livraison HTTP vers l'URL du Webhook Discord.

2. **Test de connectivité direct (OPS01) :**
   - Test d'envoi d'un message manuel via `curl` depuis la machine `OPS01` vers le Webhook Discord :
     ```bash
     curl -H "Content-Type: application/json" -X POST -d '{"content":"Test alerte"}' [https://discord.com/api/webhooks/1562011139661897739/gkCjev00UzZgaNS0oZ1AAcx9K8CsXX4-iEiWeRAGDhgggln3QVR_72qaP0vaitoQrr9m](https://discord.com/api/webhooks/1562011139661897739/gkCjev00UzZgaNS0oZ1AAcx9K8CsXX4-iEiWeRAGDhgggln3QVR_72qaP0vaitoQrr9m)
     ```

## 3. Cause Identifiée
- L'URL du Webhook configurée dans le Contact Point Grafana était erronée ou la clé de jeton d'accès avait été réinitialisée, provoquant l'échec de la requête HTTP POST.

## 4. Action Corrective Appliquée
1. Génération d'un nouveau Webhook sur le canal Discord.
2. Mise à jour du paramètre **Contact Point (Discord)** dans l'interface Grafana.
3. Exécution de la commande `curl` de validation depuis `OPS01`.

## 5. Validation du Retour à la Normale
- Réception immédiate du message de test `"Test alerte"` sur le canal Discord de l'équipe (validé le 20/10/2026 à 12:09).
- Déclenchement d'une alerte de test dans Grafana validant la chaîne complète de notification.
