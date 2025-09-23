# Module 10 : gérer les incidents dans Microsoft Defender XDR

## Gérer les incidents dans Microsoft Defender XDR

Dans cette tâche, vous allez explorer les fonctionnalités de gestion des incidents dans Microsoft Defender XDR, notamment l’enquête sur les incidents, les actions de réponse et les fonctionnalités de collaboration.

>**Important :** Ce labo est conçu pour être exécuté dans l’environnement de démonstration *Zava/Alpine Ski House*. Des informations d’identification appropriées sont requises pour y accéder.

### Principaux domaines couverts

- Tableau de bord des incidents
- Enquête sur les incidents
- Preuves et actions de réponse
- Flux de travail de gestion des incidents
- Collaboration et documentation

1. Si vous n’êtes pas déjà sur le portail Microsoft Defender dans votre navigateur, accédez au portail Microsoft Defender à l’adresse (<https://security.microsoft.com>) et connectez-vous à l’aide de vos informations d’identification affectées.

1. Dans le volet de navigation gauche, développez la section **Enquête et réponse**, puis sélectionnez **Incidents et alertes** > **Incidents**. Cela affichera la file d’attente des incidents affichant tous les incidents actifs dans votre environnement.

1. Passez en revue l’interface de file d’attente des incidents :
   - Options de filtre (État, Affecté à, Balises, etc.)
   - Indicateurs de priorité et de gravité des incidents
   - Sources de service (Defender for Endpoint, Office 365, etc.)
   - Horodatages de la dernière activité

1. Sélectionnez un incident dans la liste pour ouvrir la page détaillant cet incident. Notez l’aperçu de l’incident affichant :
   - Chronologie de l’incident
   - Ressources affectées (utilisateurs, appareils, boîtes aux lettres)
   - Détails et corrélation des alertes
   - Tactiques et techniques MITRE ATT&CK

## Processus d’enquête sur les incidents

1. Dans les détails de l’incident, explorez l’onglet **Alertes** pour voir toutes les alertes liées qui composent cet incident.
   - Passer en revue la corrélation des alertes et le regroupement automatique
   - Examinez les preuves et artefacts des alertes
   - Notez les niveaux de confiance et les sources de détection

1. Sélectionnez l’onglet **Appareils** pour afficher tous les points de terminaison affectés :
   - Niveau de risque de l’appareil
   - Scorings de priorité d’enquête
   - Chronologie des activités des appareils
   - Actions de réponse disponibles

1. Accédez à l’onglet **Utilisateurs** pour passer en revue les comptes d’utilisateur affectés :
   - Évaluations du risque des utilisateurs
   - Activités de connexion et anomalies
   - Indicateurs de compromission de compte

1. Examinez l’onglet **Boîtes aux lettres** (le cas échéant) pour les incidents liés aux e-mails :
   - Flux des emails et détails de livraison
   - Analyse des pièces jointes et des URL
   - Évaluation de l’impact sur les destinataires

## Analyse des preuves et actions de réponse

1. Dans l’onglet **Preuves**, passez en revue toutes les preuves collectées :
   - Fichiers et hachages de fichiers
   - Adresses IP et domaines
   - Clés de registre et processus
   - Messages électroniques et URL

1. Pour chaque élément de preuve, explorez les actions disponibles :
   - **Soumettre pour analyse** : envoyez les fichiers suspects à Microsoft pour une analyse approfondie
   - **Ajouter aux indicateurs** : créez des indicateurs de menace personnalisés
   - **Bloquer/Autoriser** : prenez des mesures de protection immédiates

1. Démontrez les actions de réponse en sélectionnant un appareil et en choisissant parmi les actions disponibles :
   - **Isoler l’appareil** : déconnectez l’appareil du réseau tout en maintenant la connectivité à Defender
   - **Lancer l’analyse antivirus** : démarrez une analyse complète ou rapide
   - **Collecter le package d’enquête** : rassembler les données d’analyse numérique
   - **Restreindre l’exécution des applications** : limitez l’exécution des applications sur l’appareil

## Gestion des incidents et flux de travail

1. Pratiquez l’affectation et la gestion des incidents :
   - **Affecter un incident** : affectez à un analyste ou à une équipe de sécurité spécifique
   - **Modifier le statut** : passez du statut Actif au statut Résolu ou à un autre statut
   - ** Ajouter des balises** : appliquez des balises personnalisées pour la catégorisation et le suivi
   - **Définir la classification** : marquez comme Vrai positif, Faux positif ou Informatif

1. Explorer le flux de travail de gestion des incidents :
   - Consultez l’onglet **Commentaires** pour la collaboration des analystes
   - Vérifiez l’onglet **Historique** pour toutes les actions entreprises
   - Utilisez l’onglet **Résumé** pour le reporting exécutif

1. Démontrez le processus de classification des incidents :
   - **Vrai positif** : activité malveillante confirmée nécessitant une réponse
   - **Informatif** : activité attendue qui a déclenché la détection
   - **Faux positif** : activité bénigne marquée d’un indicateur à tort

## Fonctionnalités avancées des incidents

1. Explorez les résultats de l’**Analyse automatisée** (si disponible) :
   - Passez en revue les conclusions de l’analyse générées par l’IA
   - Examinez les actions recommandées
   - Approuvez ou rejetez la correction automatisée

1. Accédez à l’intégration **Analyse des menaces** :
   - Associez les incidents à des campagnes de menaces connues
   - Passez en revue le contexte de la veille des menaces
   - Accédez aux rapports des analystes et aux IOC

1. Démontrez l’impact des **Règles de détection personnalisées** :
   - Montrez comment les règles personnalisées contribuent à la création d’incidents
   - Passez en revue l’efficacité des règles et les possibilités de réglage
   - Accédez aux options de modification et de test des règles

## Reporting et métriques des incidents

1. Accédez aux fonctionnalités de reporting des incidents :
   - Accédez à **Rapports** > **Rapport de sécurité**
   - Passez en revue les tendances et statistiques des incidents
   - Générez des rapports synthétiques pour la direction

1. Explorez les métriques et KPI des incidents :
   - Temps moyen de détection (MTTD)
   - Temps moyen de réponse (MTTR)
   - Tendances du volume des incidents
   - Taux de faux positifs

1. Configurez les notifications d’incident :
   - Configurez les alertes par email pour les incidents prioritaires
   - Configurez l’intégration des équipes pour la réponse collaborative
   - Créez des règles de notification personnalisées en fonction des critères d’incident

## Meilleures pratiques pour la gestion des incidents

1. **Stratégie de hiérarchisation** :
   - Priorisez d’abord les incidents de haute gravité
   - Tenez compte de l’impact sur l’activité et de la criticité des ressources
   - Utilisez le scoring de risque pour orienter les efforts d’enquête

1. **Normes de documentation** :
   - Tenez à jour des notes détaillées sur l’enquête
   - Documentez toutes les actions de réponse effectuées
   - Enregistrez les leçons apprises et les pistes d’amélioration

1. **Collaboration en équipe** :
   - Utilisez des schémas de marquage et de classification cohérents
   - Mettez en place des procédures d’escalade claires
   - Mettez en œuvre des processus réguliers de révision des incidents

1. **Amélioration continue :**
   - Passez régulièrement en revue les taux de faux positifs
   - Ajustez les règles de détection en fonction des résultats des incidents
   - Mettez à jour les playbooks en fonction des conclusions

## Intégration avec Microsoft Sentinel

1. Si Microsoft Sentinel est connecté, démontrez une gestion unifiée des incidents :
   - Corrélation des incidents multiplateformes
   - Expérience d’enquête unifiée
   - Partage de la veille des menaces et des indicateurs

1. Démontrez les fonctionnalités d’incidents spécifiques à Sentinel :
   - Visualisation graphique de l’enquête
   - Automatisation des playbooks personnalisés
   - Repérage avancé à travers les environnements

## Vous avez terminé la démonstration

---

**Ressources supplémentaires :**

- [Gestion des incidents Microsoft Defender XDR](https://docs.microsoft.com/microsoft-365/security/defender/manage-incidents)
- [Guides opérationnels de réponse aux incidents](https://docs.microsoft.com/security/compass/incident-response-playbooks)
- [Infrastructure MITRE ATT&CK](https://attack.mitre.org/)
