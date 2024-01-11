---
lab:
  title: "Exercice\_4 – Explorer l’analyse du comportement des entités"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 7 – Labo 1 – Exercice 4 – Explorer l’analyse du comportement des entités

## Scénario du labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous avez déjà créé des règles planifiées et analytiques de sécurité Microsoft. 


Vous devez configurer Microsoft Sentinel pour effectuer une analyse du comportement des entités pour détecter les anomalies et fournir des pages d’analyse des entités.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Explore%20entity%20behavior%20analytics)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 

### Tâche 1 : explorer le comportement des entités 

Dans cette tâche, vous allez explorer l’analyse du comportement des entités dans Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Sélectionnez la page **Comportement des entités**.

1. Dans la fenêtre contextuelle à partir des *paramètres de comportement des entités*, sélectionnez **Définir l’UEBA**.

1. Sur la page suivante, sélectionnez **Définir l’UEBA**.

1. Passez en revue les trois étapes préalables requises pour activer l’analyse du comportement des entités.

1. Fermez la page *Configuration de comportement des entités* en sélectionnant « x » en haut à droite de la page.

1. Faites défiler la page *Paramètres* et consultez le paragraphe *Anomalies*.

1. Sélectionnez **Accéder à l’analyse pour configurer les anomalies**.


### Tâche 2 : confirmer et vérifier les règles d’anomalies

Dans cette tâche, vous allez confirmer que les règles analytiques des anomalies sont activées.

1. Vous devez maintenant vous trouver dans l’onglet *Anomalies* de la page *Analyse*.

1. Vérifiez que la colonne de statut des règles est *activée*.

1. Sélectionnez une règle, puis **Modifier** dans le panneau de la règle.

1. Passez en revue les informations de l’onglet *Général*. Notez que le *mode* est **production**, puis sélectionnez **Suivant : Configuration**.

1. Passez en revue les informations de l’onglet *Configuration*. Notez que vous ne pouvez pas modifier le **seuil du score d’anomalie**.

1. Sélectionnez ensuite **X** dans le coin supérieur droit pour quitter l’Assistant Règle analytique.

1. Faites défiler la page vers la droite jusqu’à la règle analytique que vous avez sélectionnée, puis repérez et sélectionnez l’icône représentant des points de suspension **(…)**.

1. Sélectionnez **Dupliquer** et faites défiler la page vers la gauche pour passer en revue la nouvelle règle avec l’onglet **FLGT** au début du nom.

1. Sélectionnez la règle **FLGT**, puis **Modifier** dans le panneau de la règle.

1. Passez en revue les informations de l’onglet *Général*. Notez que le *mode* est **Distribution de version d’évaluation**, puis sélectionnez **Suivant : Configuration**.

1. Passez en revue les informations de l’onglet *Configuration*. Notez que vous pouvez maintenant modifier le **seuil du score d’anomalie**.

1. Définissez la valeur sur **1**, puis sélectionnez **Suivant : Envoyer des commentaires**.

1. Sélectionnez **Suivant : Vérifier**, puis **Enregistrer** pour mettre à jour la règle.

    >**Remarque :** vous pouvez mettre à niveau la règle **Distribution de versions d’évaluation** vers **Production** en modifiant le paramètre de cette règle et en enregistrant les modifications. La règle **Production** deviendra ensuite la règle **Distribution de versions d’évalaluation**.
    

## Passez à l’exercice 5
