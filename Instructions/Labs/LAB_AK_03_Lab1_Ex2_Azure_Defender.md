---
lab:
  title: "Exercice\_2\_: atténuer les menaces avec Microsoft\_Defender\_pour\_le\_cloud"
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Chemin d’apprentissage 3 - Labo 1 - Exercice 2 - Atténuer les menaces avec Microsoft Defender pour le cloud

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex2.png)

Vous êtes analyste des opérations de sécurité dans une entreprise qui a implémenté Microsoft Defender pour le cloud. Vous devez examiner les recommandations et les alertes de sécurité générées par Microsoft Defender pour le cloud.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20threats%20using%20Microsoft%20Defender%20for%20Cloud)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : explorer la conformité réglementaire

Dans cette tâche, vous passez en revue la configuration de conformité réglementaire dans Microsoft Defender pour le cloud. 

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez les références de nom de machine virtuelle.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au Portail Azure à l’adresse (https://portal.azure.com).

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du Portail Azure, tapez *Defender*, puis sélectionnez **Microsoft Defender pour le cloud**.

1. Dans *Sécurité du cloud*, sélectionnez **Conformité réglementaire** parmi les éléments du menu de gauche.

1. Sélectionnez **Gérer les normes de conformité** sur la barre d’outils.

1. Sélectionnez votre abonnement.

    >**Conseil :** Sélectionnez **Tout développer** pour trouver votre abonnement si vous avez une hiérarchie Groupes d’administration.

1. Sous *Paramètres*, sélectionnez **Stratégie de sécurité** dans le menu du portail.

1. Défilez vers le bas et passez en revue les « Normes de sécurité » à votre disposition par défaut.

1. Utilisez la zone de recherche pour rechercher la norme *ISO 27001:2013*.

1. Sélectionnez et déplacez le curseur **État** vers la droite de *ISO 27001:2013* vers **Activé**.

    >**Remarque :** Certaines normes vous obligent à attribuer une initiative Azure Policy.

1. Sélectionnez **Actualiser** dans le menu de la page pour confirmer que *ISO 27001:2013* est définie sur *Activé* pour votre abonnement.

1. Fermez la page des *Stratégies de sécurité* en sélectionnant le « X » en haut à droite de la page pour revenir aux **Paramètres d’environnement**.

    >**Remarque :** revenez ultérieurement à la *Conformité réglementaire* pour passer en revue les nouveaux contrôles et recommandations standard.

### Tâche 2 : explorer la posture de sécurité et les recommandations

Dans cette tâche, vous passez en revue la gestion de la posture de sécurité cloud.  Le calcul des informations relatives au Niveau de sécurité peut prendre 24 heures. Il est recommandé d’effectuer à nouveau cette tâche dans 24 heures.

1. Dans *Sécurité du cloud*, sélectionnez **Posture de sécurité** parmi les éléments du menu de gauche.

1. Le *Score de sécurité* est défini par défaut sur l’*Environnement Azure*.

1. Sous l’onglet *Environnement*, sélectionnez le lien **Afficher les recommandations >**.

1. Sélectionnez **Ajouter un filtre**, puis **Type de ressource**.

1. Cochez la case **Machines - Azure Arc**, puis sélectionnez le bouton **Appliquer**.

    >**Remarque :** Si vous ne voyez pas **Machines - Azure Arc**, vérifiez que vous avez terminé le Parcours d’apprentissage 3 - Labo 1 - Exercice 1 Tâche 4.

1. Sélectionnez une recommandation où l’état n’est pas *« Terminé »*.

1. Passez en revue la recommandation et, dans l’onglet **Prendre des mesures**, défilez vers le bas jusqu’à **Délégué**, puis sélectionnez **Attribuer un propriétaire et définir la date d’échéance**.

1. Dans la fenêtre **Créer une affectation**, conservez la définition du *Type* sur *Defender pour le cloud* et développez les **Détails d’affectation**.

1. Dans la zone *Adresse e-mail* `Set owner`, tapez votre e-mail d’administrateur. **Conseil :** copiez l’adresse e-mail à partir des instructions de l’onglet *Ressources*.

1. Explorez les options *Définir la période de correction* et *Définir les notifications par e-mail*, puis sélectionnez **Créer**.

    >**Remarque :** si le message d’erreur suivant s’affiche *Échec de la création des attributions demandées*, réessayez plus tard.

1. Fermez la page des recommandations en cliquant sur le bouton X en haut à droite de la fenêtre.


### Tâche 3 : atténuer les alertes de sécurité

Dans cette tâche, vous chargez des exemples d’alertes de sécurité et passez en revue les détails des alertes.


1. Dans le portail du menu, sous *Général*, sélectionnez **Alertes de sécurité**.

1. Dans la barre de commandes, sélectionnez **Exemples d’alertes**. **Conseil :** Vous devrez peut-être sélectionner le bouton de points de suspension (...) dans la barre de commandes.

1. Dans le volet Créer des exemples d’alertes (préversion), vérifiez que votre abonnement est sélectionné et que tous les exemples d’alertes sont sélectionnés dans la zone *Plans Defender pour le cloud*.

1. Sélectionnez **Créer des exemples d’alertes**.  

    >**Remarque :** cet exemple de processus de création d’alerte peut prendre quelques minutes, attendez la notification *« Exemples d’alertes créés avec succès ».*

1. Une fois l’opération terminée, sélectionnez **Actualiser** (si nécessaire) pour voir les alertes sous la zone *Alertes de sécurité*.

1. Choisissez une alerte intéressante avec un *Niveau de gravité* *Élevé* et effectuez les actions suivantes :

    - Cochez la case de l’alerte pour faire apparaître le volet des détails la concernant. Sélectionnez **Afficher les détails complets**.

    - Vérifiez et consultez l’onglet *Détails de l’alerte*.

    - Sélectionnez l’onglet **Agir** ou faites défiler vers le bas et sélectionnez le bouton **Suivant : Agir** à la fin de la page.

    - Passez en revue les informations *Entreprendre une action*. Notez que les sections disponibles pour entreprendre des actions dépendent du type d’alerte : inspecter le contexte de ressource, atténuer la menace, empêcher les futures attaques, déclencher une réponse automatique et supprimer des alertes similaires.

## Vous avez terminé le labo.
