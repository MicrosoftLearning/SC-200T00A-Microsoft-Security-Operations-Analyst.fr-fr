---
lab:
  title: 'Exercice 1 : explorer les cas d’usage de Microsoft Security Copilot'
  module: Learning Path 2 - Mitigate threats using Microsoft Security Copilot
---

# Parcours d’apprentissage 2 - Labo 1 - Exercice 1 - Explorer Microsoft Security Copilot

## Scénario de labo

L’organisation pour laquelle vous travaillez souhaite augmenter l’efficacité et les capacités de ses analystes des opérations de sécurité afin d’améliorer les résultats de sécurité. Pour soutenir cet objectif, le bureau du CISO a déterminé que le déploiement de Microsoft Security Copilot constitue une étape clé vers cet objectif. En tant qu’Administrateur de la sécurité de votre organisation, vous êtes chargé de configurer Copilot.

Dans cet exercice, vous passez en revue la *première expérience d’exécution* de Microsoft Security Copilot pour approvisionner Copilot avec une unité de calcul de sécurité (SCU).

>**Note :** l’environnement de cet exercice est une simulation générée à partir du produit. Comme c’est une simulation limitée, les liens d’une page peuvent ne pas être activés et les entrées texte qui ne sont pas prises en compte dans le script spécifié ne sont pas prises en charge. Un message contextuel indiquant « Cette fonctionnalité n’est pas disponible dans la simulation » s’affiche. Lorsque cela se produit, sélectionnez OK et poursuivez les étapes de l’exercice.  
> :::image type="content" source="../Media/simulation-pop-up-error.png" alt-text="Capture d’écran d’une fenêtre contextuelle indiquant que cette fonctionnalité n’est pas disponible dans la simulation.":::

### Temps estimé pour terminer ce labo : 45 minutes

### Tâche 1 : configurer et approvisionner Microsoft Security Copilot

Pour cet exercice, vous êtes connecté en tant que Avery Howard et vous avez le rôle d’administrateur général dans Microsoft Entra. Vous allez travailler à la fois dans le portail Azure et dans Microsoft Security Copilot.

Vous devriez terminer cet exercice en **15** minutes environ.

>**Note :** lorsqu’une instruction de labo nécessite l’ouverture d’un lien dans l’environnement simulé, il est généralement recommandé d’ouvrir le lien dans une nouvelle fenêtre de navigateur afin de voir simultanément les instructions et l’environnement de l’exercice. Pour ce faire, cliquez avec le bouton droit de la souris et sélectionnez l’option adaptée.

Avant que les utilisateurs puissent commencer à utiliser Copilot, les administrateurs doivent approvisionner et allouer la capacité. Pour approvisionner la capacité :

- Vous devez disposer d’un abonnement Azure.
- Vous devez au moins être un propriétaire ou contributeur Azure au niveau d’un groupe de ressources.

Dans cette tâche, vous allez passer en revue le processus permettant de vérifier que vous avez les autorisations de rôle appropriées. Cela commence par activer la gestion des accès pour les ressources Azure.

Une fois que vous avez affecté le rôle Administrateur d’accès utilisateur dans Azure, vous pouvez affecter à un utilisateur l’accès nécessaire pour approvisionner des références SKU pour Copilot.  Dans le cadre de cet exercice uniquement, qui consiste à vous montrer les étapes impliquées, vous vous attribuerez l’accès nécessaire.  Les étapes qui suivent vous guideront tout au long du processus.

1. Ouvrez l’environnement simulé en sélectionnant ce lien : **[Portail Azure](https://app.highlights.guide/start/6373500f-1f10-4584-a14e-ca0b4aa7399f?link=1&token=40f793d4-2956-40a4-b11a-6b3d4f92557f&azure-portal=true)**.

1. Vous allez commencer par activer la gestion des accès pour les ressources Azure. Pour accéder à ce paramètre :
    1. Dans le portail Azure, sélectionnez **Microsoft Entra ID**.
    1. Dans le volet de navigation de gauche, développez **Gérer**.
    1. Dans le volet de navigation de gauche, faites défiler vers le bas et sélectionnez **Propriétés**.
    1. Activez le bouton bascule associé à **Gestion de l’accès pour les ressources Azure**, puis sélectionnez **Enregistrer**.

1. Maintenant que vous pouvez afficher toutes les ressources et attribuer l’accès dans n’importe quel abonnement ou groupe d’administration de l’annuaire, attribuez-vous le rôle Propriétaire pour l’abonnement Azure.
    1. Dans la bannière bleue en haut de la page, sélectionnez **Microsoft Azure** pour revenir à la page d’accueil du portail Azure.
    1. Sélectionnez **Abonnements**, puis sélectionnez l’abonnement **Woodgrove - GTP Demos (Exernal/Sponsored)**.
    1. Sélectionnez **Contrôle d’accès (IAM)** .
    1. Sélectionnez **Ajouter**, puis **Ajouter une attribution de rôle**.
    1. Sous l’onglet Rôle, sélectionnez **Rôles d’administrateur privilégiés**.
    1. Sélectionnez **Propriétaire**, puis **Suivant**.
    1. Sélectionnez **+ Sélectionner des membres**.
    1. Avery Howard est le premier nom de cette liste. Sélectionnez le signe **+** à droite du nom.  Avery Howard apparaît désormais sous les membres sélectionnés. Sélectionnez le bouton **Sélectionner**, puis **Suivant**.
    1. Sélectionnez **Autoriser l’utilisateur à attribuer tous les rôles, à l’exception des rôles d’administrateur privilégiés, Propriétaire, UAA, RBAC (Recommandé)**.
    1. Sélectionnez **Vérifier + attribuer**, puis **Vérifier + attribuer** une dernière fois.

En tant que propriétaire de l’abonnement Azure, vous pouvez désormais approvisionner la capacité dans Copilot.

#### Sous-tâche 1 : approvisionner la capacité

Dans cette tâche, vous allez suivre les étapes de l’approvisionnement de la capacité pour votre organisation. Il existe deux options pour l’approvisionnement de la capacité :

- Capacité de provisionnement dans Security Copilot (recommandé)
- Approvisionnement de la capacité via Azure

Pour cet exercice, vous provisionnez la capacité via Security Copilot. Lorsque vous ouvrez Security Copilot pour la première fois, un assistant vous guide à travers les étapes de configuration de la capacité de votre organisation.

1. Ouvrez l’environnement simulé en sélectionnant ce lien : **[Copilot de sécurité Microsoft](https://app.highlights.guide/start/6373500f-1f10-4584-a14e-ca0b4aa7399f?link=0&token=40f793d4-2956-40a4-b11a-6b3d4f92557f&azure-portal=true)**.

1. Suivez les étapes de l’Assistant et sélectionnez **Démarrage**.
1. Dans cette page, vous configurez votre capacité de sécurité. Pour chacun des champs énumérés ci-dessous, vous pouvez sélectionner l'icône d'information pour obtenir plus d'informations.
    1. Abonnement Azure : Dans la liste déroulante, sélectionnez **Woodgrove : Démonstrations GTP (externes ou parrainées)**.
    1. Groupe de ressources : Dans la liste déroulante, sélectionnez **RG-1**.
    1. Nom de capacité : Entrez un nom de capacité.
    1. Demander l'emplacement de l'évaluation [Geo] : Sélectionnez votre région dans la liste déroulante.
    1. Vous pouvez choisir de sélectionner l’option « Si le trafic de cet emplacement est trop dense, autoriser Copilot à évaluer les prompts n’importe où dans le monde (recommandé pour des performances optimales).
    1. La région de la capacité est définie en fonction de l’emplacement sélectionné.
    1. Calcul de sécurité : Ce champ est automatiquement rempli avec les unités SCU minimales requises, qui est de 1. Laissez le champ contenant la valeur **1**.
    1. Cochez la case **« Je reconnais avoir lu et compris les conditions générales, et je les accepte**.
    1. Sélectionnez **Continuer** dans le coin en bas à droite de la page.

1. L'assistant affiche des informations sur l'endroit où vos données clients seront stockées. La région affichée est basée sur la région que vous avez sélectionnée dans le champ d'évaluation de l'invite. Sélectionnez **Continuer**.

1. Vous pouvez sélectionner des options pour améliorer Copilot. Vous pouvez sélectionner le bouton bascule en fonction de vos préférences.  Sélectionnez **Continuer**.

1. Dans le cadre de la configuration initiale, Copilot fournit par défaut un accès Contributeur à tout le monde et ajoute les administrateurs généraux et les administrateurs de sécurité en tant que propriétaires de Copilot. Dans votre environnement de production, vous pouvez modifier qui a accès à Copilot une fois la configuration initiale terminée. Sélectionnez **Continuer**.
1. Vous êtes prêt à commencer ! Sélectionnez **Terminer**.
1. Fermez l'onglet du navigateur, car l'exercice suivant utilisera un lien distinct vers l'environnement de type laboratoire.

### Tâche 2 : explorer l’expérience autonome de Microsoft Security Copilot.

L’administrateur de la sécurité de votre organisation a approvisionné Copilot. Étant donné que vous êtes l’analyste principal de l’équipe, l’administrateur vous ajoute en tant que propriétaire de Copilot et vous demande de vous familiariser avec la solution.

Dans cet exercice, vous explorez tous les points clés sur la page d’accueil de l’expérience autonome de Microsoft Security Copilot.

Vous êtes connecté sous le nom d’Avery Howard avec le rôle de propriétaire Copilot. Vous travaillerez dans l’expérience autonome de Microsoft Security Copilot.

Vous devriez terminer cet exercice en **15** minutes environ.

#### Sous-tâche 1 : explorer les options de menu

Dans cette tâche, vous démarrez votre exploration dans le menu d’accueil.

1. Ouvrez l’environnement simulé en sélectionnant ce lien : **[Microsoft Security Copilot](https://app.highlights.guide/start/2cac767e-42c4-4058-afbb-a9413aac461d?link=0&token=40f793d4-2956-40a4-b11a-6b3d4f92557f&azure-portal=true)**.

1. Sélectionnez l’icône de **Menu** ![icône de menu d’accueil](../Media/home-menu-icon.png), parfois appelée icône hamburger.

1. Sélectionnez **Mes sessions** et notez les options disponibles.
    1. Sélectionnez récent pour afficher les sessions les plus récentes.
    1. Sélectionnez filtre et notez les options disponibles, puis fermez le filtre.
    1. Sélectionnez l’icône du menu d’accueil pour ouvrir le menu d’accueil.

1. Sélectionnez **Bibliothèque promptbook**.
    1. Sélectionnez Mes promptbooks. Une tâche suivante explore les promptbooks de manière plus approfondie.
    1. Sélectionnez Woodgrove.
    1. Sélectionnez Microsoft.
    1. Sélectionnez filtre pour afficher les options disponibles, puis sélectionnez le X pour fermer.
    1. Sélectionnez l’icône du menu d’accueil pour ouvrir le menu d’accueil.

1. Sélectionnez les **Paramètres de propriétaire**. Ces paramètres vous sont disponibles en tant que propriétaire Copilot. Les contributeurs Copilot n’ont pas accès à ces options de menu.
    1. Pour les plug-ins Security Copilot, sélectionnez la liste déroulante pour « Qui peut ajouter et gérer ses propres plug-ins personnalisés » afin d’afficher les options disponibles.
    1. Sélectionnez la liste déroulante pour « Qui peut ajouter et gérer des plug-ins personnalisés pour tous les membres de l’organisation » afin d’afficher toutes les options disponibles. Notez que cette option est grisée si « Qui peut ajouter et gérer ses propres plug-ins personnalisés » est défini sur propriétaires uniquement.
    1. Sélectionnez l’icône d’information en regard de « Autoriser Security Copilot à accéder aux données de vos services Microsoft 365 ».  Ce paramètre doit être activé si vous souhaitez utiliser le plug-in Microsoft Purview. Vous utiliserez ce paramètre lors d’un exercice ultérieur.
    1. Sélectionnez la liste déroulante « Qui peut charger des fichiers » afin d’afficher les options disponibles.
    1. Sélectionnez l’icône du menu d’accueil pour ouvrir le menu d’accueil.

1. Sélectionnez **Attribution de rôle**.
    1. Sélectionnez Ajouter des membres, puis fermez.
    1. Développez le propriétaire.
    1. Développez le contributeur.
    1. Sélectionnez l’icône du menu d’accueil pour ouvrir le menu d’accueil.

1. Sélectionnez **Suivi de l’utilisation**.
    1. Sélectionnez le filtre de date pour afficher les options disponibles.
    1. Sélectionnez l’icône du menu d’accueil pour ouvrir le menu d’accueil.

1. Cliquez sur **Paramètres**.
    1. Sélectionnez les préférences. Défilez vers le bas pour afficher les options disponibles.
    1. Sélectionnez données et confidentialité.
    1. Sélectionnez À propos de.
    1. Sélectionnez le X pour fermer la fenêtre des préférences.

1. Sélectionnez **Woodgrove** en bas à gauche du menu d’accueil.
    1. Quand vous sélectionnez cette option, vous voyez vos locataires. C’est ce que l’on appelle le sélecteur de locataire. Dans ce cas, Woodgrove est le seul locataire disponible.
    1. Sélectionnez **Accueil** pour revenir à la page d’accueil.

#### Sous-tâche 2 : explorer l’accès aux sessions récentes

Au centre de la page d’arrivée se trouvent des cartes qui symbolisent vos sessions les plus récentes.

1. La plus grande carte est votre dernière session. Sélectionnez le titre d’une carte de session pour accéder à ladite session.
1. Sélectionnez **Afficher toutes les sessions** pour accéder à la page Mes sessions.
1. Sélectionnez **Microsoft Copilot pour la sécurité** en regard de l’icône du menu d’accueil pour revenir à la page d’arrivée.

#### Sous-tâche 3 : explorer l’accès aux promptbooks

La section suivante de la page d’arrivée Copilot concerne les promptbooks. La page d’arrivée affiche des vignettes pour certains promptbooks de Sécurité Microsoft. Ici, vous explorez l’accès aux promptbooks et la bibliothèque des promptbooks. Dans un exercice ultérieur, vous explorez la création et l’exécution d’un promptbook.

1. À droite du dialogue « Prise en main de ces promptbooks » se trouvent des touches de flèches gauche et droite qui vous permettent de faire défiler les vignettes des promptbooks de Sécurité Microsoft. Sélectionnez la **flèche droite >**.

1. Chaque vignette affiche le titre du promptbook, une courte description, le nombre d’invites et une icône d’exécution. Sélectionnez le titre de l’une des vignettes de séquence de prompts pour ouvrir la séquence de prompts correspondante. Sélectionnez par exemple **Évaluation de l’impact des vulnérabilités**.
    1. La fenêtre du promptbook sélectionné fournit des informations, notamment la personne qui a créé le promptbook, les balises, une courte description, les entrées nécessaires pour exécuter le promptbook et un référencement des invites.
    2. Notez les informations sur la séquence de prompts et les options disponibles. Pour cette simulation, vous ne pouvez pas démarrer une nouvelle session. Vous le ferez dans un exercice ultérieur. 
    1. Sélectionnez le **X** pour fermer la fenêtre.

1. Sélectionnez **Afficher la bibliothèque de promptbooks**.
    1. Pour afficher les promptbooks qui vous appartiennent, sélectionnez Mes promptbooks.
    1. Sélectionnez Woodgrove pour obtenir la liste des promptbooks appartenant à Woodgrove, le nom d’une organisation imaginaire.
    1. Pour afficher les promptbooks appartenant à/développés par Microsoft, sélectionnez Microsoft.
    1. Sélectionnez l’icône de filtre. Ici, vous pouvez filtrer en fonction des balises affectées au classeur. Fermez la fenêtre de filtre en sélectionnant le X dans l’onglet Nouveau filtre.
    1. Sélectionnez **Microsoft Copilot pour la sécurité** en regard de l’icône du menu d’accueil pour revenir à la page d’arrivée.

#### Sous-tâche 4 : explorer les icônes de prompts et de sources dans la barre de prompt

La barre de prompt se trouve en bas au centre de la page. La barre de prompt inclut les icônes des prompts et des sources que vous explorez dans cette tâche. Dans les exercices suivants, vous saisirez les entrées directement dans la barre de prompt.

1. Dans la barre de prompt, vous pouvez sélectionner l’icône de prompts pour choisir un prompt intégré ou une séquence de prompts. Sélectionnez l’**icône de prompts** ![icône de prompts](../Media/prompt-icon.png).
    1. Sélectionner **Afficher tous les promptbooks**
        1. Défilez pour afficher tous les promptbooks disponibles.
        1. Sélectionnez la **flèche arrière** à côté de la barre de recherche pour revenir en arrière.
    1. Sélectionnez **Afficher toutes les fonctionnalités système**. La liste affiche toutes les fonctionnalités système disponibles (ces fonctionnalités sont en réalité des invites que vous pouvez exécuter). De nombreuses fonctionnalités système sont associées à des plug-ins spécifiques et ne sont répertoriées que si le plug-in correspondant est activé.
        1. Défilez pour afficher tous les promptbooks disponibles.
        1. Sélectionnez la **flèche arrière** à côté de la barre de recherche pour revenir en arrière.

1. Sélectionnez l’**icône de sources** ![icône de sources](../Media/sources-icon.png).
    1. L’icône des sources ouvre la fenêtre pour gérer les sources. Vous pouvez accéder aux plug-ins ou aux fichiers à partir de cette fenêtre. L’onglet **Plug-ins** est sélectionné par défaut.
        1. Indiquez si vous souhaitez afficher tous les plug-ins, ceux qui sont activés ou ceux qui sont désactivés.
        1. Développez/réduisez la liste des plug-ins Microsoft, non-Microsoft et personnalisés.
        1. Certains plug-ins nécessitent la configuration de paramètres. Sélectionnez le bouton **Configurer** du plug-in Microsoft Sentinel pour afficher la fenêtre des paramètres. Cliquez sur **annuler** pour fermer la fenêtre des paramètres. Dans un autre exercice, vous configurez le plug-in.
    1. Vous devriez toujours vous trouver dans la fenêtre Gérer les sources. Sélectionnez **Fichiers**.
        1. Passez en revue la description.
        1. Les fichiers peuvent être chargés et utilisés comme base de connaissances par Copilot. Dans un exercice ultérieur, vous travaillerez sur les chargements de fichiers.
        1. Sélectionnez le **X** pour fermer la fenêtre Gérer les sources.

#### Sous-tâche 5 : explorer la fonctionnalité d’aide

L’icône d’aide se trouve en bas à droite de la fenêtre. Elle vous permet d’accéder facilement à la documentation et de trouver des solutions aux problèmes courants. L’icône d’aide vous permet également d’envoyer un cas de support à l’équipe de support Microsoft si vous avez les autorisations de rôle appropriées.

1. Sélectionnez l’icône **Aide (?)**.
    1. Sélectionnez **Documentation**. Cette sélection ouvre un nouvel onglet de navigateur pour afficher la documentation Microsoft Security Copilot. Revenez à l’onglet du navigateur de Microsoft Security Copilot.
    1. Sélectionnez **Aide**.
        1. Toute personne avec un accès à Security Copilot peut accéder au widget d’auto-assistance en sélectionnant l’icône d’aide, puis en sélectionnant l’onglet Aide. Ici, vous pouvez trouver des solutions aux problèmes courants en indiquant un aspect du problème.
        1. Les utilisateurs disposant d’un rôle minimal d’Administrateur de service ou d’Administrateur du support technique peuvent soumettre des cas de support à l’équipe de support technique Microsoft. Si vous avez ce rôle, une icône de casque est affichée. Fermez la page pour contacter le support technique.

### Tâche 3 : explorer l’expérience incorporée de Microsoft Security Copilot

Dans cet exercice, vous investiguez un incident dans Microsoft Defender XDR. Dans le cadre de l’investigation, vous explorez les principales fonctionnalités de Microsoft Copilot dans Microsoft Defender XDR, notamment le récapitulatif d’incident, le récapitulatif d’appareil, l’analyse de script, etc. Vous redirigez également votre investigation sur l’expérience autonome et utilisez le tableau d’épinglage pour partager les détails de votre investigation avec vos collègues.

Vous êtes connecté sous le nom d’Avery Howard avec le rôle de propriétaire Copilot. Vous travaillerez dans Microsoft Defender, en utilisant la plateforme d’opérations de sécurité unifiée, pour accéder aux capacités Copilot incorporées dans Microsoft Defender XDR. À la fin de l’exercice, vous basculez sur l’expérience autonome de Microsoft Security Copilot.

Cet exercice devrait prendre environ **30** minutes.

#### Sous-tâche 1 : explorer le résumé d’incident et les réponses guidées

1. Ouvrez l’environnement simulé en sélectionnant ce lien : **[Portail Microsoft Defender](https://app.highlights.guide/start/f4f590f6-8937-40f9-91ec-632de546ab98?token=40f793d4-2956-40a4-b11a-6b3d4f92557f&azure-portal=true)**.

1. Dans le portail Microsoft Defender :
    1. Développez **Enquêtes et réponses**.
    1. Développez **Incidents et alertes**.
    1. Sélectionnez **Incidents**.

1. Sélectionnez le premier incident dans la liste, **ID d’incident : 30342** dénommé « Une attaque par ransomware opérée par un humain a été lancée depuis une ressource compromise (interruption de l’attaque).

1. Il s’agit d’un incident complexe. Defender XDR fournit une grande quantité d’informations, mais avec 72 alertes, ce n’est pas toujours facile d’orienter votre attention. À droite de la page de l’incident, Copilot génère automatiquement un **récapitulatif d’incident** qui vous aide à orienter votre attention et votre réponse. Cliquez sur **Afficher plus**.
    1. Le récapitulatif de Copilot décrit comment cet incident a évolué, notamment l’accès initial, le mouvement latéral, la collecte, l’accès des informations de connexion et l’exfiltration. Il identifie des appareils spécifiques, indique que l’outil PsExec a été utilisé pour lancer des fichiers exécutables, etc.
    1. Il s’agit de tous les éléments que vous pouvez utiliser pour une investigation plus approfondie. Vous explorez certains de ces éléments dans les tâches suivantes.

1. Faites défiler le panneau Copilot vers le bas et juste en dessous du récapitulatif vous avez les **Réponses guidées**. Les réponses guidées recommandent des actions en faveur du triage, de l’isolement, de l’investigation et de la correction.
    1. Le premier élément de la catégorie de triage permet de Classifier cet incident. Sélectionnez **Classifier** pour voir les options. Passez en revue les réponses guidées dans les autres catégories.
    1. Sélectionnez le bouton **État** en haut de la section des réponses guidées, puis filtrez sur **Terminé**. Deux activités terminées s’affichent avec l’étiquette Interruption d’attaque. L’interruption automatique des attaques est conçue pour enrayer les attaques en cours, limiter l’impact sur les ressources d’une organisation et fournir plus de temps aux équipes de sécurité pour corriger complètement l’attaque.
1. Laissez la page de l’incident ouverte, vous en avez besoin pour la tâche suivante.

#### Sous-tâche 2 : explorer le résumé des appareils et identités

1. Dans la page de l’incident, sélectionnez la première alerte **Suspicious URL clicked**.

1. Copilot génère automatiquement un **Résumé de l’alerte**, qui fournit une multitude d’informations pour une analyse plus approfondie. Par exemple, le récapitulatif identifie l’activité suspecte, des activités de collecte de données, l’accès à des informations d’identification, un programme malveillant, des activités de découverte, etc.

1. Comme il y a beaucoup d’informations dans la page, pour obtenir une meilleure vue de cette alerte, sélectionnez la **page Ouvrir l’alerte**. Il se trouve dans le troisième volet de la page de l’alerte, à côté du graphique de l’incident et sous le titre de l’alerte.

1. En haut de la page, vous voyez la fiche de l’appareil parkcity-win10v. Sélectionnez les points de suspension et notez les options. Sélectionnez **Résumer**. Copilot génère un **Récapitulatif de l’appareil**. Notez qu’il existe de nombreuses façons d’accéder au récapitulatif de l’appareil et que celle utilisée ici est simplement une méthode pratique. Le récapitulatif montre que l’appareil est une machine virtuelle, identifie le propriétaire de l’appareil, il affiche son état de conformité par rapport aux stratégies Intune, etc.

1. À côté de la fiche de l’appareil, vous avez la fiche du propriétaire de l’appareil. Sélectionnez **parkcity\jonaw**. Le troisième panneau de la page passe de l’affichage des détails de l’alerte à l’affichage des informations sur l’utilisateur Jonathan Wolcott, un chargé de compte, dont la gravité du risque Microsoft Entra ID et du risque interne est classée comme élevée. Ce n’est pas surprenant compte tenu de ce que vous avez appris dans les récapitulatifs d’alerte et d’incident Copilot. Sélectionnez les points de suspension, puis **Résumer** pour obtenir un résumé de l’identité généré par Copilot.

1. Laissez la page d’alerte ouverte, vous en avez besoin pour la tâche suivante.

#### Sous-tâche 3 : explorer l’analyse de script

1. Concentrons-nous sur l’histoire de l’alerte. Sélectionnez **Agrandir ![icône Agrandir](../Media/maximize-icon.png)**, qui se trouve dans le panneau principal de l’alerte, juste sous la carte intitulée « partycity\jonaw » pour obtenir une meilleure vue de l’arborescence des processus. Dans la vue agrandie, vous commencez à avoir une vue plus claire de la façon dont cet incident est arrivé. De nombreux éléments de ligne indiquent que powershell.exe a exécuté un script. Étant donné que l’utilisateur Jonathan Wolcott est un chargé de compte, il est raisonnable de supposer que l’exécution de scripts PowerShell n’est pas quelque chose que cet utilisateur est susceptible d’effectuer régulièrement.

1. Développez la première instance de **powershell.exe execute a script**, c’est celle qui indique l’horodatage 4:57:11 AM. Copilot a la possibilité d’analyser les scripts. Sélectionnez **Analyser**.
    1. Copilot génère une analyse du script et suggère qu’il peut s’agir d’une tentative d’hameçonnage ou qu’il est utilisé pour distribuer du code malveillant basé sur le web.
    1. Sélectionnez **Afficher le code**. Le code montre une URL neutralisée.

1. Il y a plusieurs autres éléments qui indiquent que powershell.exe a exécuté un script. Développez l’étiquette **powershell.exe -EncodedCommand...** avec l’horodatage 5:00:47 AM. Le script d’origine était encodé en base 64, mais Defender l’a décodé pour vous. Pour la version décodée, sélectionnez **Analyser**. L’analyse met en évidence la sophistication du script utilisé dans cette attaque.

    >**Remarque :** l’horodatage sera ajusté pour refléter le fuseau horaire du navigateur de l’utilisateur. Le fuseau horaire de la simulation est défini sur Heure du Pacifique.

1. Fermez la page d’histoire de l’alerte en sélectionnant le **X** (le X à gauche du panneau Copilot). Utilisez maintenant la barre de navigation pour revenir à l’incident. Sélectionnez **Human-operated ransomware attack was launched from a compromised asset (attack disruption)**.

#### Sous-tâche 4 : explorer l’analyse de fichier

1. Vous êtes à nouveau dans la page de l’incident. Dans le récapitulatif de l’alerte, Copilot a identifié le fichier Rubeus.exe, qui est associé au programme malveillant « Kekeo ». Vous pouvez utiliser la fonctionnalité d’analyse de fichier dans Defender XDR pour voir les autres insights que vous pouvez obtenir. Il existe plusieurs moyens d’accéder aux fichiers. En haut de la page, sélectionnez l’onglet **Preuve et réponse**.

1. À gauche de l’écran, sélectionnez **Fichiers**.
1. Sélectionnez le premier élément de la liste avec l’entité nommée **Rubeus.exe**.
1. Dans la fenêtre qui s’ouvre, sélectionnez **Analyser**. Copilot génère un récapitulatif.
1. Passez en revue l’analyse détaillée des fichiers générée par Copilot.
1. Fermez la fenêtre d’analyse de fichier.

#### Sous-tâche 5 : passer à l’expérience autonome

Cette tâche est complexe et nécessite l’implication d’analystes plus expérimentés. Dans cette tâche, vous redirigez votre investigation et exécutez la séquence de prompts d’incident Defender pour que les autres analystes puissent démarrer rapidement l’investigation. Vous épinglez des réponses au tableau d’épinglage et générez un lien vers cette investigation afin de la partager avec des membres plus avancés de l’équipe pour qu’ils participent à l’investigation.

1. Revenez à la page d’incident en sélectionnant l’onglet **Histoire de l’attaque** en haut de la page.

1. Sélectionnez les points de suspension à côté du récapitulatif d’incident de Copilot, puis sélectionnez **Ouvrir dans Copilot pour la sécurité**.

1. Copilot s’ouvre dans l’expérience autonome et affiche le récapitulatif de l’incident. Vous pouvez également exécuter d’autres prompts. Dans le cas présent, vous allez exécuter la séquence de prompts pour un incident. Sélectionnez l’**icône de prompts** ![icône de prompts](../Media/prompt-icon.png). 
    1. Sélectionnez **Voir toutes les séquences de prompts**.
    1. Sélectionnez **Investigation d’incident Microsoft 365 Defender**.
    1. La page de la séquence de prompts s’ouvre et demande l’ID d’incident Defender. Entrez **30342**, puis sélectionnez **Exécuter**.
    1. Examinez les informations fournies. En basculant vers l’expérience autonome et en exécutant la séquence de prompts, l’investigation est en mesure d’appeler les fonctionnalités d’une solution de sécurité plus large définie, au-delà de Defender XDR, en fonction des plug-ins activés.

1. Sélectionnez l’**icône de boîte ![icône de boîte](../Media/box-icon.png)** en regard de l’icône d’épingle pour sélectionner toutes les prompts et réponses correspondantes, puis sélectionnez l’**icône d’épingle ![icône d’épingle](../Media/pin-icon.png)** pour enregistrer ces réponses dans le tableau d’épinglage.

1. Le tableau d’épinglage s’ouvre automatiquement. Le tableau d’épinglage contient vos prompts et réponses enregistrés, ainsi qu’un récapitulatif de chacun d’eux. Vous pouvez ouvrir et fermer le tableau d’épinglage en sélectionnant l’**icône de tableau d’épinglage ![icône de tableau d’épinglage](../Media/pinboard-icon.png)**.

1. En haut de la page, sélectionnez **Partager** pour voir vos options. En partageant l’incident via un lien ou un e-mail, les personnes de votre organisation qui ont un accès Copilot peuvent voir cette session. Fermez la fenêtre en sélectionnant le **X**.

1. Vous pouvez maintenant fermer l’onglet de navigateur pour quitter la simulation.

## Résumé et ressources complémentaires

Dans cet exercice, vous avez exploré la première expérience d’exécution de Microsoft Security Copilot, approvisionné la capacité, puis exploré les expériences autonomes et incorporées de Copilot. Vous avez examiné un incident dans Microsoft Defender XDR, puis exploré notamment le résumé de l’incident, le résumé de l’appareil et l’analyse des scripts. Vous avec également redirigé votre investigation sur l’expérience autonome et avez utilisé le tableau d’épinglage pour partager les détails de votre investigation avec vos collègues.

Pour exécuter d’autres simulations de cas d’utilisation de Microsoft Security Copilot, accédez à [Explorer les simulations de cas d’utilisation de Microsoft Security Copilot](/training/modules/security-copilot-exercises/)
