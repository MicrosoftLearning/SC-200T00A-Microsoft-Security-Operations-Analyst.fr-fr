---
lab:
  title: "Exercice\_2 – Repérage des menaces à l’aide de notebooks avec Microsoft\_Sentinel"
  module: Learning Path 10 - Perform threat hunting in Microsoft Sentinel
---

# Parcours d’apprentissage 10 - Labo 1 - Exercice 2 - Repérage des menaces à l’aide de notebooks avec Microsoft Sentinel

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez explorer les avantages du repérage des menaces avec les notebooks Microsoft Sentinel. Vous pouvez utiliser des notebooks pour :

- Effectuez des analyses qui ne sont pas fournies prêtes à l’emploi dans Microsoft Sentinel, par exemple certaines fonctionnalités de Machine Learning Python.
- Créez des visualisations des données qui ne sont pas fournies prêtes à l’emploi dans Microsoft Sentinel, par exemple des chronologies et des arborescences de processus personnalisées.
- Intégrer des sources de données qui ne proviennent pas de Microsoft Sentinel, telles qu’un jeu de données local

>**Important :** les exercices de laboratoire du parcours d’apprentissage #10 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : explorer les notebooks

Dans cette tâche, vous allez découvrir l’utilisation des notebooks dans Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Dans l’espace de travail Microsoft Sentinel, sélectionnez **Notebooks** sous la zone *Gestion des menaces*.

1. Vous devez ensuite créer un espace de travail Azure Machine Learning. Sélectionnez **Configurer Azure Machine Learning**, puis le bouton **Créer un espace de travail Azure ML** dans la barre de commandes.

1. Dans la zone « Abonnement », sélectionnez votre abonnement Azure.

1. Sélectionnez **Créer** pour le groupe de ressources, puis entrez *RG-MachineLearning* pour le nom, et sélectionnez **OK**. 

1. Dans la section Détails de l’espace de travail, procédez comme suit :

     - Donnez un nom unique à votre espace de travail.
     - Laissez **USA Est** comme valeur par défaut pour la *région*.
     - Conservez le compte de stockage, le coffre de clés et les informations sur les perspectives d’application par défaut.
     - L’option Registre de conteneurs peut rester **Aucun**.

1. En bas de la page, sélectionnez **Revoir + Créer**. Lorsque vous voyez le message *« Validation réussie »*, sélectionnez **Créer**. 

     >**Remarque :** le déploiement de l’espace de travail Machine Learning peut prendre quelques minutes.

1. Une fois qu’apparaît le message *Votre déploiement a été effectué*, revenez au portail Microsoft Sentinel.

1. Sélectionnez à nouveau **Notebooks**, puis sélectionnez l’onglet **Modèles** dans la barre de commandes centrale. 

1. Sélectionnez **Guide de prise en main des notebooks Microsoft Sentinel ML**.

1. Dans le volet droit, faites défiler la page vers le bas et sélectionnez le bouton **Créer à partir d’un modèle**. Passez en revue les options par défaut, puis sélectionnez **Enregistrer**.

1. Une fois l’enregistrement terminé, sélectionnez le bouton **Lancer le notebook**. Cela vous permet d’accéder à Microsoft Azure Machine Learning studio.

1. Sélectionnez **Fermer** si une fenêtre d’information s’affiche dans Microsoft Azure Machine Learning studio.

1. Dans la barre de commandes, à droite du sélecteur **Calcul :**, sélectionnez le symbole **+** pour créer une instance *Capacité de calcul ML Azure*. **Conseil :** il peut être masqué à l’intérieur de l’icône représentant des points de suspension **(…)**.

     >**Remarque :** Pour disposer de plus d’espace à l’écran, vous pouvez masquer le volet gauche d’Azure ML Studio, sélectionner le *menu Hamburger* (3 lignes horizontales en haut à gauche) ou réduire les fichiers Notebooks en sélectionnant l’icône **<<**.

1. Dans le champ *Nom du calcul*, tapez un nom unique. Cela identifie votre instance de calcul.

1. Faites défiler la page vers le bas et sélectionnez la première option disponible. **Conseil :** Type de charge de travail : Développement sur Notebooks (ou tout autre IDE) et tests légers.

1. Sélectionnez le bouton **Vérifier + créer** au bas de l’écran, faites défiler vers le bas, puis sélectionnez **Créer**. Fermez toutes les fenêtres de commentaires qui peuvent s’afficher. Cela ne prend que quelques minutes. Une notification (icône en forme de cloche) s’affiche une fois l’opération effectuée, et l’icône de gauche de l’*Instance de calcul* passe du bleu au vert.

1. Une fois le calcul créé et en cours d’exécution, vérifiez que le noyau à utiliser est *Python 3.8 - Pytorch et TensorFlow*. **Conseil :** ceci s’affiche à droite de la barre de commandes.

1. Cliquez sur le bouton **Authentifier** et patientez jusqu’à la fin de l’authentification.

1. Effacez tous les résultats du notebook en sélectionnant **Effacer toutes les sorties** (icône Gomme) dans la barre de commandes, puis suivez le tutoriel *Prise en main*. **Conseil :** vous pouvez le trouver dans la barre de commandes en sélectionnant les points de suspension (…).

1. Passez en revue la section *1 Introduction* du notebook, puis passez à la section *2 Initialisation du notebook et de MSTICPy*.

1. Dans la section *2 Initialisation du notebook et de MSTICPy*, passez en revue le contenu relatif à l’initialisation du notebook et à l’installation du package MSTICPy.

1. Exécutez le *code Python* pour initialiser la cellule en sélectionnant le bouton **Exécuter la cellule** (icône Lecture) à gauche du code.

1. L’exécution doit prendre environ 15 secondes. Une fois l’opération effectuée, passez en revue les messages de sortie, et ignorez les avertissements relatifs à la version du noyau Python. Le code s’est exécuté correctement si *msticpyconfig.yaml* a été créé dans le dossier *utils* du volet *Explorateur de fichiers* sur la gauche. L’affichage du fichier peut prendre jusqu’à 30 secondes.

    >**Conseil :** vous pouvez effacer les messages de sortie en sélectionnant les points de suspension (...) à gauche de la fenêtre de code du *menu Sortie* et en sélectionnant l’icône de *sortie Effacer* (carré avec un x*).

1. Sélectionnez le fichier **msticpyconfig.yaml** dans le volet *Explorateur de fichiers* sur la gauche pour passer en revue le contenu du fichier, puis fermez celui-ci.

1. Passez à la section *3 Interrogation des données avec MSTICPy*, puis passez en revue son contenu. N’exécutez pas la cellule de code *Plusieurs espaces de travail Microsoft Sentinel*, car elle échoue. Toutefois, vous pouvez exécuter les autres cellules de code correctement.

>**Remarque** : si vous ne pouvez pas effectuer les étapes ci-dessus pour accéder au notebook, vous pouvez le suivre sur sa page de visualisation GitHub à la place. [Prise en main des notebooks Azure ML et de Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb) 

## Vous avez terminé le labo
