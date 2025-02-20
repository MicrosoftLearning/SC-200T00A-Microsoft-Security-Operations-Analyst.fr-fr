---
lab:
  title: "Exercice\_1 – Modifier une règle de sécurité Microsoft"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 1 - Modifier une règle de sécurité Microsoft

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à détecter et à atténuer les menaces à l’aide de Microsoft Sentinel. Tout d’abord, vous devez filtrer les alertes provenant de Defender pour le cloud dans Microsoft Sentinel, par gravité.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 10 minutes

### Tâche 1 : activer une règle de sécurité Microsoft

Dans cette tâche, vous allez activer une règle de sécurité Microsoft.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Dans la zone Configuration, sélectionnez **Analyses**.

1. Sélectionnez le bouton ** + Créer** dans la barre de commandes, puis sélectionnez **Règle de création d’incident Microsoft**.

1. Sous *Nom*, entrez **Créer des incidents basés sur Defender pour le cloud**.

1. Faites défiler vers le bas et, sous *Service de sécurité Microsoft*, sélectionnez **Microsoft Defender pour le cloud**.

1. Sous *Filtrer par gravité*, sélectionnez l’option *Personnalisé*, puis **Bas**, **Moyen** et **Élevé** pour le niveau de gravité, et revenez à la règle.

1. Sélectionnez le bouton **Suivant : Réponse automatique**, puis le bouton **Suivant : Vérifier et créer**.

1. Passez en revue les modifications apportées et sélectionnez le bouton **Enregistrer**. La règle analytique est enregistrée et les incidents sont créés s’il existe une alerte dans Defender pour le cloud.

1. Vous disposez désormais d’un type d’alerte *Fusion* et d’un type d’alerte *sécurité Microsoft*.

## Passez à l’exercice 2
