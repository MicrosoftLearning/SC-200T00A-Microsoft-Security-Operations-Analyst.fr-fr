---
lab:
  title: "Exercice 2\_-\_Atténuer les attaques avec Micrsoft Defender for Endpoint"
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Parcours d'apprentissage 2 - Labo 1 - Exercice 2 - Atténuer les attaques avec Microsoft Defender for Endpoint

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Defender pour point de terminaison. Votre responsable prévoit d’intégrer quelques appareils afin de fournir des informations sur les modifications requises des procédures de réponse de l’équipe chargée des opérations de sécurité.

Pour explorer les fonctionnalités d’atténuation des risques d’attaque Defender for Endpoint, vous allez vérifier que l’intégration de l’appareil a réussi et examiner les alertes et incidents créés pendant ce processus.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques.

### Tâche 1 : Vérifier l’intégration de l’appareil

Dans cette tâche, vous allez confirmer que l’appareil a été intégré avec succès et créer une alerte de test.

1. Si vous n’êtes pas encore sur le portail Microsoft Defender XDR dans votre navigateur Microsoft Edge, accédez à https://security.microsoft.com) et connectez-vous en tant qu’administrateur pour votre tenant.

1. Dans le menu de gauche, sous la zone **Ressources** , sélectionnez **Appareils**. Veuillez patienter jusqu’à ce que WIN1 apparaisse sur la page Appareils avant de continuer. Sinon, vous devrez peut-être répéter cette tâche pour voir les alertes qui seront générées ultérieurement.

    >**Remarque :** si vous avez terminé le processus d’intégration et que vous ne voyez pas d’appareils sur la liste Appareils au bout d’une heure, cela peut indiquer un problème d’intégration ou de connectivité.

1. Sélectionnez **Paramètres** dans la barre de menus de gauche, puis, sur la page Paramètres, choisissez **Points de terminaison**.

1. Sélectionnez **Intégration** dans la section Gestion des appareils, puis vérifiez si *« Windows 10 et Windows 111 »* est sélectionné comme système d’exploitation. Le message *« Premier appareil intégré »* affiche désormais *Terminé*.

1. Faites défiler la page vers le bas puis, sous la section *« 2. Exécuter un test de détection »,* puis copiez le script de test de détection en sélectionnant le bouton **Copier**.  

1. Dans la barre de recherche Windows de la machine virtuelle WIN1, tapez **CMD** et choisissez **Exécuter en tant qu’administrateur** dans le volet droit de l’application Invite de commandes.

1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » apparaît, sélectionnez **Oui** pour autoriser l’exécution de l’application. 

1. Collez le script en cliquant avec le bouton droit dans les fenêtres d’invite **Administrateur : Invite de commande**, ppuis appuyez sur **Entrée** pour l’exécuter.

    >**Remarque :** La fenêtre se ferme automatiquement après l’exécution du script et, après quelques minutes, les alertes sont générées dans le portail Microsoft Defender XDR.

<!--- ### Task 2: Simulated Attacks

>**Note:** The Evaluation lab and the Tutorials & simulations section of the portal is no longer available. Please refer to the **[interactive lab simulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** for a demonstration of the simulated attacks.

1. From the left menu, under **Endpoints**, select **Evaluation & tutorials** and then select **Tutorials & simulations** from the left side.

1. Select the **Tutorials** tab.

1. Under *Automated investigation (backdoor)* you will see a message describing the scenario. Below this paragraph, click **Read the walkthrough**. A new browser tab opens which includes instructions to perform the simulation.

1. In the new browser tab, locate the section named **Run the simulation** (page 5, starting at step 2) and follow the steps to run the attack. **Hint:** The simulation file *RS4_WinATP-Intro-Invoice.docm* can be found back in portal, just below the **Read the walkthrough** you selected in the previous step by selecting the **Get simulation file** button.

    <!--- 1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Tâche 2 : Examiner les alertes et les incidents

Dans cette tâche, vous allez examiner les alertes et les incidents générés par le script de test de détection d’intégration dans la tâche précédente.

1. Dans le portail Microsoft Defender XDR, sélectionnez **Incidents et alertes** dans le menu de gauche, puis **Alertes**.

1. Dans le volet **Alertes**, sélectionnez l’alerte nommée *Ligne de commande PowerShell suspecte* pour charger ses détails.

1. Passez en revue la chronologie *Historique de l’alerte*, puis les onglets *Détails* et *Recommandations*.

    >**Remarque :** Sous l’onglet *Détails* de l’alerte, vous pouvez faire défiler jusqu’à la section *Détails de l’incident* et sélectionner le lien *Incident d’exécution sur un point de terminaison* pour ouvrir l’incident.

1. Dans le portail Microsoft Defender XDR, sélectionnez **Incidents et alertes** dans le menu de gauche, puis **Incidents**.

1. Un nouvel incident appelé *Incident d’exécution sur un point de terminaison* se trouve dans le volet droit. Sélectionnez le nom de l’incident pour charger ses informations.

1. Sélectionnez le lien **Gérer l’incident** (avec une icône de crayon) et un nouveau panneau de fenêtre s’affiche.

1. Sous **Balises d’incident**, tapez « Simulation », puis sélectionnez **Simulation (Créer)** pour créer une balise.

1. Sélectionnez le bouton bascule **Attribuer à** et ajoutez votre compte d’utilisateur (Moi) en tant que propriétaire de l’incident.

1. Sous **Classification**, développez le menu déroulant.

1. Sous **Informational, activité  attendue**, sélectionnez **Test de sécurité**.

1. Ajoutez des commentaires si vous le souhaitez, puis sélectionnez **Enregistrer** pour mettre à jour l’incident et quitter la page.

1. Passez en revue le contenu des onglets  *Histoire d’attaque, Alertes, Ressources, Investigations, Preuve et réponse* et *Résumé*. Les appareils et les utilisateurs se trouvent sous l’onglet *Ressources*. Dans un vrai incident, l’onglet *Historique de l’attaque* affiche le *graphique de l’incident*. **Conseil :** Certains onglets risquent d’être masqués en raison de la taille de votre écran. Sélectionnez l’onglet représentant des points de suspension (...) pour les afficher.

<!---    >**Warning:** The simulated attacks here are an excellent source of learning through practice. Only perform the attacks in the instructions provided for this lab when using the course provided Azure tenant.  You may perform other simulated attacks *after* this training course is complete with this tenant. --->

## Vous avez terminé le labo
