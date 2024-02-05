---
lab:
  title: "Exercice\_9\_: créer des analyseurs ASIM"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Chemin d’apprentissage 7 - Labo 1 - Exercice 9 - Déployer des analyseurs ASIM

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex9.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez modéliser les analyseurs ASIM pour un événement de Registre Windows spécifique. Ces analyseurs simplifiés seront finalisés ultérieurement après les [Informations de référence de schéma de normalisation d’événement du registre Advanced Security Information Model (ASIM)](https://docs.microsoft.com/en-us/azure/sentinel/registry-event-normalization-schema).

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20Advanced%20Security%20Information%20Model%20Parsers)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 

### Tâche 1 : Déployer les analyseurs ASIM du schéma de Registre

Dans cette tâche, vous allez déployer les analyseurs de schéma de registre à partir du référentiel GitHub Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Dans le navigateur Edge, ouvrez un nouvel onglet (Ctrl+T) et accédez à la page Microsoft Sentinel GitHub ASIM <https://github.com/Azure/Azure-Sentinel/tree/master/ASIM>.

    <!--- 1. On the right pane, select the **Onboard community content** link. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel). --->

    >**Remarque :** Dans le dossier **ASIM**, vous pouvez déployer des modèles qui contiennent tous les analyseurs ASIM, mais nous allons nous concentrer ici sur le schéma de Registre uniquement.

1. Faites défiler vers le bas et en regard du **Registre**, sélectionnez le bouton **Déployer sur Azure**.

1. Pour le *Groupe de ressources*, sélectionnez **RG-Defender** où réside votre espace de travail Sentinel.

1. Pour l’*Espace de travail*, tapez le nom de votre espace de travail Sentinel, comme *nomuniqueDefender*.

1. Laissez le reste des valeurs par défaut, puis sélectionnez **Vérifier + créer**.

1. Sélectionnez **Créer** pour déployer le modèle. Notez les noms des différentes ressources.

1. Une fois le déploiement terminé, revenez à l’onglet *Microsoft Sentinel*.

1. Dans le menu de gauche *Général*, sélectionnez **Journaux**.

1. Ouvrez le volet *Schéma et filtre* en sélectionnant **>>** si nécessaire.

1. Sélectionnez l’onglet **Fonctions** (en regard des onglets Tables et Requêtes). **Conseil :** vous devrez peut-être sélectionner l’icône de points de suspension **(...)** pour sélectionner l’onglet.

1. Développez **Fonctions d’espace de travail**. Notez que les noms correspondent aux modèles que vous venez de déployer.

1. Pointez sur l’*analyseur d’espace de travail* **vimRegistryEventMicrosoftSecurityEvents**, puis sélectionnez **Charger le code de fonction** dans la fenêtre contextuelle.

1. Passez en revue l’instruction KQL qui analyse l’ID d’événement 4657 pour simplifier votre analyse des données dans l’espace de travail Microsoft Sentinel.

1. **Exécutez** la requête. Vous ne devriez obtenir aucun résultat ni aucune erreur, l’objectif étant juste de valider.

1. Revenez au volet *Schéma et filtre* et placez le curseur sur l’*analyseur* **inRegistry**, puis sélectionnez **Charger le code de la fonction**.

1. Notez que les analyseurs d’unification utilisent l’opérateur d’*union* pour exécuter tous les analyseurs d’espace de travail à la fois. Si vous développez un analyseur pour le schéma de registre, vous devez l’ajouter ici.

1. **Exécutez** la requête. Vous ne devez pas obtenir de résultat ni d’erreur, la requête est uniquement exécutée à des fins de validation.

1. Cet analyseur d’unification peut maintenant être utilisé pour les règles analytiques ou les requêtes de repérage.

## Passez à l’exercice 10