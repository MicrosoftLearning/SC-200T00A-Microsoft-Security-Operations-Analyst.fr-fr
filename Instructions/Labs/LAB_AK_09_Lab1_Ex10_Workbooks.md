---
lab:
  title: "Exercice\_10 : créer des classeurs"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 10 - Créer des classeurs

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex10.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Une fois que vous avez connecté vos sources de données à Microsoft Sentinel, vous pouvez visualiser et surveiller les données à l'aide de l'adoption par Microsoft Sentinel des classeurs Azure Monitor, qui offrent une grande souplesse dans la création de tableaux de bord personnalisés. 

Microsoft Sentinel vous permet de créer des workbooks personnalisés à partir de vos données. Il est également fourni avec des modèles de classeurs intégrés qui vous permettent d'obtenir rapidement des informations sur vos données dès que vous connectez une source de données.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : explorer les modèles de classeur

Dans cette tâche, vous allez explorer les modèles de classeur Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez **Classeurs** dans la section *Gestion des menaces* du menu de navigation.

1. Sélectionnez l’onglet *Modèles*, puis recherchez et sélectionnez le classeur de modèle **Activité Azure**.

1. Dans le volet d’informations de droite, faites défiler vers le bas et sélectionnez le bouton **Afficher le modèle**.

1. Passez en revue le contenu du classeur. Il affiche des informations sur vos opérations d’abonnement Azure en collectant et en analysant les données à partir du journal d’activité.

1. Fermez le classeur en sélectionnant **X** en haut à droite.

### Tâche 2 : enregistrer et modifier un modèle de classeur

Dans cette tâche, vous allez enregistrer un modèle de classeur et le modifier.

1. Vous devez revenir dans **Microsoft Sentinel | Classeurs | Onglet Modèles** avec le classeur *Activité Azure* toujours sélectionné.

1. Faites défiler vers le bas et sélectionnez le bouton **Enregistrer** dans le volet d’informations du classeur *Activité Azure*.

1. Laissez **USA Est** comme valeur par défaut pour la *Région*, puis sélectionnez **OK**.

1. Sélectionnez le bouton **Afficher le classeur enregistré**.

1. Sélectionnez **Modifier** dans la barre de commandes pour activer les modifications dans le classeur.

1. Faites défiler jusqu’à la zone *Activités de l’appelant* et observez la couleur de la colonne *Activités*. Nous allons en effet mettre en forme ces colonnes. Sélectionnez le bouton **Modifier** sous la grille.

1. Sélectionnez le bouton **Paramètres de colonne**, situé à droite de la barre de commandes *Exécuter la requête*. **Conseil :** ce bouton s’affiche uniquement s’il existe des données de la requête KQL.

1. Dans le panneau *Modifier les paramètres de colonne* qui s’affiche, sous *Colonnes*, sélectionnez **Activités**.

1. Remplacez la valeur du *Convertisseur de colonne* par **Carte thermique**. Pour la *Palette de couleurs*, faites défiler vers le bas pour sélectionner **Catégories en 32 couleurs**.

1. Sélectionnez **Appliquer**, puis **Enregistrer et fermer**. Notez la modification dans la colonne *Activités*.

1. En bas de la requête (et non dans le menu supérieur), sélectionnez **Modification effectuée**.

1. Dans le menu supérieur, sélectionnez **Modification effectuée**, puis l’icône **Enregistrer**. 

1. Fermez le classeur en sélectionnant **X** en haut à droite.


### Tâche 3 : créer un classeur

Dans cette tâche, vous allez créer un classeur avec des visualisations avancées.

1. Vous devez revenir à la zone **Classeurs** du portail Microsoft Sentinel.

1. Sélectionnez **+ Ajouter un classeur** pour créer un classeur. 

    >**Remarque :** bien qu’il s’agit d’un nouveau classeur, un modèle de démarrage est utilisé.

1. Pour modifier le classeur, sélectionnez **Modifier**.

1. Sélectionnez le bouton **Modifier** sous le premier paragraphe du classeur.

1. Tapez *# Mon classeur* dans une nouvelle ligne en haut de *## Nouveau classeur*.

1. En bas de cette section, *Élément de modification de texte : texte - 2*,sélectionnez **Modification effectuée**. Notez que la taille de votre en-tête a augmenté et que votre nom a été modifié.

1. Sous le seul graphique à barres visible, sélectionnez **Modifier**.

1. Passez en revue l’instruction KQL qui fournit une instruction *union* de nombres dans toutes les tables.

1. Dans le menu inférieur, faites défiler vers le bas et sélectionnez **Modification effectuée**, pour l’*élément Modification de requête : requête - 2*.

1. En regard du bouton *Modifier* du graphique à barres, sélectionnez les points de suspension **…**, puis **+ Ajouter**, et **Ajouter une requête**.

1. Dans la zone de requête, tapez **SecurityEvent** 

1. Changez l’*Intervalle de temps* et définissez-le sur **Dernière heure**.

1. Changez la *Visualisation* et définissez-la sur **Graphique temporel**.

1. Dans la barre de commandes de la requête, sélectionnez l’onglet **Style**.

1. Sélectionnez la case à cocher **Convertir cet élément en une largeur personnalisée**.

1. Définissez la *Largeur en pourcentage* sur **25** et la *Largeur maximale* sur **25**.

1. Dans la barre de commandes de la requête, sélectionnez maintenant l’onglet **Paramètres avancés**.

1. Sélectionnez la case à cocher **Afficher l’icône d’actualisation en dehors du mode d’édition**.

1. Dans le menu inférieur, faites défiler vers le bas et sélectionnez **Modification effectuée**, pour le nouvel *élément Modification de requête : requête - 2*.

1. Faites défiler vers le bas et en bas du classeur, sélectionnez **+ Ajouter**, puis **Ajouter une requête**.

1. Dans la zone de requête, tapez **SecurityEvent** 

1. Changez l’*Intervalle de temps* et définissez-le sur **Dernière heure**.

1. Changez la *Visualisation* et définissez-la sur **Grille**.

1. Dans la barre de commandes de la requête, sélectionnez **Style**.

1. Sélectionnez la case à cocher **Convertir cet élément en une largeur personnalisée**.

1. Définissez la *Largeur en pourcentage* sur **75** et la *Largeur maximale* sur **75**.

1. Faites défiler vers le bas et sélectionnez **Modification effectuée** dans le menu inférieur, pour le nouvel *élément Modification de requête : requête - 3*.

1. Dans la barre de commandes supérieure du classeur, sélectionnez **Modification effectuée** 

1. Sélectionnez l’icône **Enregistrer**, remplacez le *Titre* par **Mon classeur**.

1. Sélectionnez le groupe de ressources **RG-Defender** si nécessaire et laissez les autres valeurs par défaut.

1. Sélectionnez **Appliquer** pour enregistrer les modifications. 

1. Fermez le classeur en haut à droite en sélectionnant **X** ou dans le portail Microsoft Sentinel en sélectionnant **Classeurs**.

1. De retour à la page *Classeurs*, sélectionnez l’onglet **Mes classeurs**.

1. Sélectionnez le classeur que vous venez de créer, **Mon classeur**.

1. Dans le volet de droite, sélectionnez **Afficher le classeur enregistré** pour passer en revue votre classeur.

## Passez à l’exercice 11
