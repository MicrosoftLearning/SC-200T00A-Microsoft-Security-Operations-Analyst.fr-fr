---
lab:
  title: "Exercice\_2\_: atténuer les menaces avec Microsoft\_Defender\_pour\_le\_cloud"
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Chemin d’apprentissage 3 - Labo 1 - Exercice 2 - Atténuer les menaces avec Microsoft Defender pour le cloud

## Scénario de l’exercice

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex2.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui a implémenté Microsoft Defender pour le cloud. Vous devez examiner les recommandations et les alertes de sécurité générées par Microsoft Defender pour le cloud.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20threats%20using%20Microsoft%20Defender%20for%20Cloud)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : explorer la conformité réglementaire

Dans cette tâche, vous allez examiner la configuration de conformité réglementaire dans Microsoft Defender pour le cloud. 

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez les références de nom de machine virtuelle.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Edge, ouvrez le portail Azure à l’adresse (https://portal.azure.com).

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du Portail Azure, tapez *Defender*, puis sélectionnez **Microsoft Defender pour le cloud**.

1. Dans le menu du portail, sous  *Sécurité cloud*, sélectionnez **Conformité réglementaire**.

1. Sélectionnez **Gérer les stratégies de conformité** dans la barre d’outils.

1. Sélectionnez votre abonnement.

1. Dans le menu du portail, sous *Paramètres de stratégie*, sélectionnez **Stratégie de sécurité**.

1. Faites défiler vers le bas et passez en revue les « normes sectorielles et réglementaires » disponibles par défaut. Notez que la norme *ISO 27001* est obsolète.

1. Sélectionnez **Ajouter d’autres normes** pour ajouter la norme réglementaire ISO 27001:2013 mise à jour.

1. Sélectionnez le bouton **Ajouter** en regard de *ISO 27001:2013*.

1. Une nouvelle page s’ouvre pour attribuer l’initiative Azure Policy. Vérifiez que votre abonnement est sélectionné sous *Étendue*, puis cliquez sur **Vérifier et créer**.

1. Sélectionnez **Créer** pour attribuer l’initiative Azure Policy à votre abonnement.

1. Sélectionnez Microsoft Defender pour le cloud en dessous de la zone de recherche pour revenir au volet principal.

    >**Remarque :** revenez ultérieurement à la *Conformité réglementaire* pour passer en revue les nouveaux contrôles et recommandations standard.


### Tâche 2 : explorer la posture de sécurité et les recommandations

Dans cette tâche, vous allez examiner la gestion de la posture de sécurité cloud.  Le calcul des informations relatives au Niveau de sécurité peut prendre 24 heures. Il est recommandé d’effectuer cette tâche à nouveau dans 24 heures.

1. Dans le menu du portail, sous *Sécurité cloud*, sélectionnez **Posture de sécurité**.

1. Le niveau de sécurité doit afficher *N/A*, dans l’attente du nouveau calcul des données.

1. Dans le menu du portail, sous *Général*, sélectionnez **Recommandations**.

1. Consultez les recommandations fournies pour votre abonnement et WINServer (serveur Arc).

1. Sélectionnez une recommandation dont l’état n’est pas *« Terminé »* pour WINServer.

1. Lisez la recommandation, faites défiler vers le bas et **cochez** la case WINServer. **Conseil :** vous devrez peut-être sélectionner les **Ressources affectées** pour l’afficher.

1. Sélectionnez **Attribuer un propriétaire**, puis **Ajouter un propriétaire**.

1. Dans la zone *Adresse e-mail*, saisissez l’adresse e-mail de l’administrateur. **Conseil :** copiez l’adresse e-mail à partir des instructions de l’onglet *Ressources*.

1. Sélectionnez **Précédent**, remplacez la *Date d’échéance* par celle de votre choix, puis cliquez sur **Enregistrer**.

    >**Remarque :** si le message d’erreur suivant s’affiche *Échec de la création des attributions demandées*, réessayez plus tard.

1. Fermez la page des recommandations en cliquant sur le bouton X en haut à droite de la fenêtre.


### Tâche 3 : atténuer les alertes de sécurité

Dans cette tâche, vous allez charger des exemples d’alertes de sécurité et examiner les détails de l’alerte.


1. Dans le portail du menu, sous *Général*, sélectionnez **Alertes de sécurité**.

1. Dans la barre de commandes, sélectionnez **Exemples d’alertes**. **Conseil :** vous devrez peut-être sélectionner le bouton en forme de points de suspension (…) dans la barre de commandes.

1. Dans le volet Créer des exemples d’alertes (préversion), vérifiez que votre abonnement est sélectionné et que tous les exemples d’alertes sont sélectionnés dans la zone *Plans Defender pour le cloud*.

1. Sélectionnez **Créer des exemples d’alertes**.  

    >**Remarque :** cet exemple de processus de création d’alerte peut prendre quelques minutes, attendez la notification *« Exemples d’alertes créés avec succès ».* 

1. Une fois l’opération terminée, sélectionnez **Actualiser** pour afficher les alertes sous la zone *Alertes de sécurité*.

1. Pour les alertes qui ont attiré votre attention, effectuez les actions suivantes :

    - Sélectionnez l’alerte. Des informations à son sujet devraient apparaître. Sélectionnez **Afficher les détails complets**.

    - Vérifiez et consultez l’onglet *Détails de l’alerte*.

    - Sélectionnez l’onglet **Entreprendre une action** ou sélectionnez le bouton **Suivant : Entreprendre une action** en bas de la page.

    - Passez en revue les informations *Entreprendre une action*. Notez que les sections disponibles pour entreprendre des actions dépendent du type d’alerte : inspecter le contexte de ressource, atténuer la menace, empêcher les futures attaques, déclencher une réponse automatique et supprimer des alertes similaires.

## Vous avez terminé le labo.
