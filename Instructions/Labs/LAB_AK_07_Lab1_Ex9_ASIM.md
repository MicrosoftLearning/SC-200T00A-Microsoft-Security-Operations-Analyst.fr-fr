---
lab:
  title: "Exercice\_9\_: créer des analyseurs ASIM"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Chemin d’apprentissage 7 - Labo 1 - Exercice 9 - Déployer des analyseurs ASIM

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex9.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez modéliser les analyseurs ASIM pour un événement de Registre Windows spécifique. Ces analyseurs seront finalisés ultérieurement à la suite de la [référence de schéma de normalisation des événements de Registre ASIM (Advanced Security Information Model)](https://docs.microsoft.com/en-us/azure/sentinel/registry-event-normalization-schema).

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20Advanced%20Security%20Information%20Model%20Parsers)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 

### Tâche 1 : Déployer les analyseurs ASIM du schéma de Registre

Dans cette tâche, vous passez en revue les analyseurs de schéma de Registre inclus dans le déploiement de Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

<!--- 1. In the Edge browser, open a new tab (Ctrl+T) and navigate to the Microsoft Sentinel GitHub ASIM page <https://github.com/Azure/Azure-Sentinel/tree/master/ASIM>.

 1. On the right pane, select the **Onboard community content** link. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel).

    >**Note:** In the **ASIM** folder you can deploy templates that contain all ASIM parsers, but we will only focus on the Registry Schema.

1. Scroll down and next to **Registry Event**, select the **Deploy to Azure** button.

1. For *Resource Group*, select **RG-Defender** where your Sentinel workspace resides.

1. For *Workspace*, type your Sentinel workspace name, like *uniquenameDefender*.

1. Leave the other default values and select **Review + create**.

1. Select **Create** to deploy the template. Notice the Names of the different resources. 

1. After the deployment completes return to the *Microsoft Sentinel* tab. --->

1. Dans le menu de gauche *Général*, sélectionnez **Journaux**.

1. Ouvrez le volet *Schéma et filtre* en sélectionnant **>>** si nécessaire.

1. Sélectionnez l’onglet **Fonctions** (en regard des onglets Tables et Requêtes). **Conseil :** vous devrez peut-être sélectionner l’icône de points de suspension **(...)** pour sélectionner l’onglet.

1. Dans la barre de *Recherche*, tapez **Registre**, faites défiler les fonctions d’analyseur ASIM jusqu’à ce que vous voyiez *_Im_RegistryEvent_MicrosoftWindowsEventxxx* pour Microsoft Windows sous le titre *Microsoft Sentinel*.

    >**Remarque :** Nous utilisons xxx dans le nom de la fonction d’analyseur ASIM pour tenir compte des modifications de version. Au moment où ce labo a été mis à jour, la fonction était _Im_RegistryEvent_MicrosoftWindowsEvent*V02*.

1. Pointez sur la fonction ASIM **_Im_RegistryEvent_MicrosoftWindowsEventxxx**, puis sélectionnez **Charger le code de la fonction** dans la fenêtre contextuelle.

1. Passez en revue l’instruction KQL qui analyse l’ID d’événement 4657 pour simplifier votre analyse des données dans l’espace de travail Microsoft Sentinel.

    >**Conseil :** Tapez Ctrl+f dans la fenêtre de code pour afficher *Rechercher* et simplifier la recherche de *EventID : 4657*.

1. Revenez au panneau *Schéma et Filtre*, puis pointez sur **_Im_RegistryEvent_MicrosoftWindowsEventxxx**, *analyseur de filtrage ASIM de l’événement de Registre pour les événements Microsoft Windows et les événements de sécurité*, puis sélectionnez **Utiliser dans l’éditeur**.

1. **Exécutez** la requête de fonction ASIM. Vous ne devez pas obtenir de résultat ni d’erreurs, il s’agit simplement d’une validation.

## Passez à l’exercice 10