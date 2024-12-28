---
lab:
  title: "Exercice\_8\_: investiguer les incidents"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 8 - Examiner les incidents

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex8.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous avez déjà créé des règles planifiées et analytiques de sécurité Microsoft. Les règles analytiques Fusion et Anomalies sont également activées dans votre environnement. Il est maintenant temps d’examiner les incidents créés ces règles.

Un incident peut inclure plusieurs alertes. Il consiste en une agrégation de toutes les preuves pertinentes pour une investigation spécifique. Les propriétés relatives aux alertes, telles que l’état et la gravité, sont définies au niveau de l’incident. Après avoir informé Microsoft Sentinel des types de menaces que vous recherchez et de comment les trouver, vous pouvez surveiller les menaces détectées en étudiant des incidents.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : investiguer un incident

Dans cette tâche, vous allez investiguer un incident.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez la page **Incidents**.

1. Passez en revue la liste des incidents.

    >**Remarque :** les règles analytiques génèrent des alertes et des incidents sur la même entrée de journal spécifique. N’oubliez pas que cette opération a été effectuée dans la configuration de la *Planification des requêtes* pour générer davantage d’alertes et d’incidents à utiliser dans le labo.
  
1. Sélectionnez l’un des incidents **Démarrage de RegKey**.

1. Passez en revue les détails de l’incident dans le panneau droit qui s’est ouvert. Sélectionnez le bouton **Afficher les détails complets**.

1. Si la fenêtre contextuelle « Nouvelle expérience d’incident » s’affiche, suivez les invites en lisant les informations, puis sélectionnez le bouton **Suivant**.

1. Dans le panneau gauche de l’incident, remplacez l’état par **Actif**, puis sélectionnez **Appliquer**.

1. Faites défiler jusqu’à la zone *Balises*, sélectionnez **+** et tapez **RegKey**, puis cliquez sur **OK**.

1. Faites défiler vers le bas jusqu’à la zone *Écrire un commentaire...* et tapez : *Je vais mener mon enquête*, puis sélectionnez l’icône **>** pour envoyer le nouveau commentaire.

1. Masquez le panneau gauche en sélectionnant l’icône **<<** en regard du propriétaire.

1. Passez en revue la fenêtre **Chronologie de l’incident**. Sélectionnez le bouton **Actions d’incident** en haut à droite, puis **Exécuter le guide opérationnel**. Vous voyez le guide opérationnel *PostMessageTeams-OnIncident*. Cette option vous aide à exécuter manuellement des playbooks.

1. Fermez le panneau *Exécuter le guide opérationnel sur l’incident* en sélectionnant l’icône **x** en haut à droite.

1. Examinez la fenêtre **Entités**. Au moins l’entité *Hôte* que nous avons mappée dans la requête KQL de l’exercice précédent doit apparaître. **Conseil :** si aucune entité n’est affichée, actualisez la page.

1. Sélectionnez le nouveau bouton **Tâches** dans la barre de commandes.

1. Sélectionnez **+ Ajouter une tâche**, tapez **Vérifier qui possède la machine** dans la zone Titre, puis cliquez sur **Enregistrer**.

1. Fermez le volet *Tâches d’incident* en sélectionnant l’icône **x** en haut à droite.

1. Sélectionnez le nouveau bouton **Journal d’activité** dans la barre de commandes.

1. Passez en revue les actions que vous avez effectuées pendant cet exercice.

1. Fermez le volet *Journal d’activité des incidents* en sélectionnant l’icône **x** en haut à droite.

1. Dans le volet gauche presque masqué, sélectionnez l’icône de l’utilisateur nommé **Unassigned**. La nouvelle expérience d’incident permet d’apporter des modifications rapides à partir de cet écran.

1. Sélectionnez **Attribuer à moi-même**, puis faites défiler vers le bas pour sélectionner **Appliquer** et enregistrer les modifications.

1. Développez le panneau gauche en sélectionnant l’icône **>>**, puis sélectionnez le bouton **Étudier**.

    >**Conseil :** si les icônes sont trop petites pour votre écran, sélectionnez **(+)** pour les agrandir.

1. **Pointez** sur l’icône d’entité WINServer et attendez que de nouvelles *requêtes d’exploration* s’affichent. Il semble que les *alertes associées* contiennent plus de données. Sélectionnez le nom de la requête d’exploration **Alertes associées** pour les faire apparaître dans le graphe d’investigation, ou sélectionnez **Événements >** pour les étudier avec une requête KQL.

1. Fermez la fenêtre de requête en sélectionnant l’icône **X** en haut à droite pour revenir à la page *Investigation*.

1. Sélectionnez maintenant l’entité **WINServer**, une fenêtre à droite s’ouvre pour plus d’informations. Passez en revue la page **Informations**.

1. Sélectionnez le bouton **Chronologie**. Pointez sur les incidents et découvrez quels éléments du graphe se sont produits et à quel moment.

1. Sélectionnez le bouton **Entités** et passez en revue les *entités* et *alertes* associées à *WINServer*.

1. Fermez le graphe d’investigation en sélectionnant l’icône **X** en haut à droite de la page.

1. De retour dans la page d’incident, dans le volet gauche, sélectionnez **Statut actif**, puis **Fermé**. 

1. Dans la liste déroulante *Sélectionner une classification*, passez en revue les différentes options. Ensuite, sélectionnez **Vrai positif - activité suspecte**, puis **Appliquer**.

## Passez à l’exercice 9
