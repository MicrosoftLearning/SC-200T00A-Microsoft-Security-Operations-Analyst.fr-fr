---
lab:
  title: "Exercice\_2 – Repérage des menaces à l’aide de notebooks avec Microsoft\_Sentinel"
  module: Learning Path 8 - Perform threat hunting in Microsoft Sentinel
---

# Parcours d’apprentissage 8 – Labo 1 – Exercice 2 – Repérage des menaces à l’aide de notebooks avec Microsoft Sentinel

## Scénario de l’exercice

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez explorer les avantages du repérage des menaces avec les notebooks Microsoft Sentinel. Vous pouvez utiliser des notebooks pour :

- Effectuer des analyses qui ne sont pas fournies d’emblée dans Microsoft Sentinel, notamment certaines fonctionnalités Python de Machine Learning.
- Créer des visualisations de données qui ne sont pas fournis d’emblée dans Microsoft Sentinel, telles que des chronologies et des arborescences de processus personnalisées.
- Intégrer des sources de données qui ne proviennent pas de Microsoft Sentinel, telles qu’un jeu de données local

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Hunt%20for%20threats%20using%20notebooks%20in%20Microsoft%20Sentinel)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 

### Tâche 1 : explorer les notebooks

Dans cette tâche, vous allez explorer l’utilisation de notebooks dans Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Dans l’espace de travail Microsoft Sentinel, sélectionnez **Notebooks** sous la zone *Gestion des menaces*.

1. Ensuite, vous devez créer un espace de travail AzureML. Sélectionnez **Configurer Azure Machine Learning**, puis le bouton **Créer un espace de travail Azure ML** dans la barre de commandes.

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

1. Une fois l’enregistrement terminé, sélectionnez le bouton **Lancer le notebook**. Vous accéderez à Microsoft Azure Machine Learning Studio.

1. Sélectionnez **Fermer** si une fenêtre d’informations s’affiche dans Microsoft Azure Machine Learning Studio.

1. Dans la barre de commandes, à droite du sélecteur **Instance de calcul :**, sélectionnez le symbole **+** pour créer une instance de calcul. **Conseil :** il peut être masqué à l’intérieur de l’icône représentant des points de suspension **(…)**.

     >**Remarque :** vous pouvez obtenir plus d’espace d’écran en masquant le panneau gauche d’Azure ML Studio en sélectionnant les 3 lignes en haut à gauche, ainsi que les fichiers Notebooks en sélectionnant l’icône <<****.

1. Dans le champ *Nom du calcul*, tapez un nom unique. Vous identifierez ainsi l’instance de calcul.

1. Faites défiler la page vers le bas et sélectionnez la première option disponible. **Conseil :** type de charge de travail : développement sur notebooks et tests légers.

1. Sélectionnez le bouton **Créer** en bas de l’écran. Fermez toutes les fenêtres de commentaires qui peuvent s’afficher. Cela prend quelques minutes. Une notification (icône en forme de cloche) s’affiche une fois l’opération terminée et l’icône de gauche *Instance de calcul * passe du bleu au vert.

1. Une fois le calcul créé et en cours d’exécution, vérifiez que le noyau à utiliser est *Python 3.8 - AzureML*. **Conseil :** ceci s’affiche à droite de la barre de commandes.

1. Cliquez sur le bouton **Authentifier** et patientez jusqu’à la fin de l’authentification.

1. Effacez tous les résultats du notebook en sélectionnant **Effacer toutes les sorties** dans la barre de commandes et suivez le tutoriel *Prise en main*. **Conseil :** vous pouvez le trouver dans la barre de commandes en sélectionnant les points de suspension (…).

>**Remarque** : si vous ne pouvez pas effectuer les étapes ci-dessus pour accéder au notebook, vous pouvez le suivre sur sa page de visualisation GitHub à la place. [Prise en main des notebooks Azure ML et de Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb) 

## Vous avez terminé le labo.
