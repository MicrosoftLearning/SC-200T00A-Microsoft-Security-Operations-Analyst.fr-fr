---
lab:
  title: 'Exercice 1 : explorer Microsoft Defender XDR'
  module: Learning Path 1 - Mitigate threats using Microsoft Defender XDR
---

# Parcours d’apprentissage 1 - Laboratoire 1 - Exercice 1 - Explorer Microsoft Defender XDR

## Scénario de labo

![M365 Defender](../Media/SC-200-Lab_M1_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Defender XDR. Vous devez attribuer des stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Explore%20Microsoft%20365%20Defender)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques.

>**Remarque :****Locataires WWL - Conditions d’utilisation** Si un locataire est fourni dans le cadre d’une formation dispensée par un instructeur, notez qu’il est mis à votre disposition dans le seul but de prendre en charge les labos pratiques de la formation. Vous ne devez ni partager ni utiliser les locataires en dehors des labos pratiques. Le locataire utilisé dans ce cours est un locataire d’essai. Au terme de la classe, le locataire ne pourra pas faire l’objet d’une prolongation et vous ne pourrez plus l’utiliser ni y accéder. Vous n’êtes pas autorisé à convertir un locataire en abonnement payant. Les locataires obtenus dans le cadre de ce cours sont la propriété de Microsoft Corporation. Nous nous réservons le droit d’y accéder et d’en reprendre possession à tout moment. 


### Tâche 1 : obtenir vos informations d’identification Microsoft 365

Une fois que vous avez lancé le labo, un locataire d’essai gratuit sera mis à votre disposition dans l’environnement de labo virtuel Microsoft. Ce locataire reçoit automatiquement un nom d’utilisateur et un mot de passe uniques. Vous devez récupérer ce nom d’utilisateur et ce mot de passe pour vous connecter à Azure et Microsoft 365 dans l’environnement de labo virtuel Microsoft. 

Comme ce cours peut être proposé par des partenaires d’apprentissage utilisant différents fournisseurs d’hébergement de labo autorisés (ALH), la procédure de récupération de l’ID de locataire associé à votre locataire peut varier. Par conséquent, votre instructeur vous fournira les instructions nécessaires pour récupérer ces informations pour votre cours. Les informations dont vous aurez besoin pour le cours sont les suivantes :

- **ID de suffixe du locataire.** Cet identifiant de compte onmicrosoft.com vous permettra de vous connecter à Microsoft 365 pendant les labos. Il est au format **{username}@ZZZZZZ.onmicrosoft.com**, où ZZZZZZ est votre ID de suffixe de locataire unique, fourni par votre fournisseur d’hébergement de labo. Enregistrez cette valeur ZZZZZZ  pour une utilisation ultérieure. Lorsque vous êtes invité à vous connecter au portail Microsoft 365 durant le labo, vous devez entrer cette valeur ZZZZZZ.
- **Mot de passe du locataire.** Il s’agit du mot de passe du compte d’administrateur communiqué par votre fournisseur d’hébergement de labo.

### tâche 2 : appliquer des stratégies de sécurité prédéfinies pour Microsoft Defender pour Office 365.

Dans cette tâche, vous allez attribuer des stratégies de sécurité prédéfinies pour Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 dans le portail de sécurité Microsoft 365.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Microsoft Defender XDR à l’adresse (https://security.microsoft.com).

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de messagerie du locataire associé au nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrez le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

    >**Remarque :** si le message suivant s’affiche « Impossible d’effectuer l’opération. Veuillez réessayer plus tard. Si le problème persiste, contactez le support technique Microsoft ». cliquez sur **OK** pour continuer.  

1. Si elle s’affiche, fermez la fenêtre contextuelle de visite guidée rapide de Microsoft Defender XDR. **Conseil :** Plus loin dans ce labo, vous devez attendre que l’espace de travail Defender soit approvisionné, vous pouvez prendre ce temps pour parcourir les visites guidées pour en savoir plus sur Microsoft Defender XDR.

1. Dans le menu de navigation, dans la zone *E-mail et collaboration*, sélectionnez **Stratégies et règles**.

1. Dans le tableau de bord *Stratégie et règles*, sélectionnez **Stratégies contre les menaces**.

1. Dans le tableau de bord *Stratégies contre les menaces*, sélectionnez **Stratégies de sécurité prédéfinies**.

    >**Remarque :** si vous recevez le message *« Erreur du client - Erreur lors de l’obtention de la règle bip »*, sélectionnez **OK** pour continuer. L’erreur est due à l’état d’hydratation de votre locataire sur Office 365, qui n’est pas activé par défaut.

    >**Remarque :** si vous recevez le message *« Erreur du client - Une erreur s’est produite lors de la récupération des stratégies de sécurité prédéfinies. Réessayez plus tard »* sélectionnez **OK** pour continuer. Actualisez votre navigateur à l’aide du raccourci clavier **Ctrl + F5**.

1. Dans la page *contextuelle* **Découvrez les stratégies de sécurité prédéfinies**, sélectionnez **Fermer**.

1. Sous *Protection standard*, sélectionnez **Gérer les paramètres de protection**. **Conseil :** si cette option est grisée, actualisez votre navigateur à l’aide de **Ctrl + F5**.

1. Dans la section *Appliquer Exchange Online Protection*, sélectionnez **Destinataires spécifiques** et sous **Domaines**, commencez à écrire le nom de domaine de votre locataire, sélectionnez-le, puis cliquez sur **Suivant**.

    >**Conseil :** le nom de domaine de votre locataire est identique à celui du compte d’administrateur (semblable à *WWLx#####.onmicrosoft.com*. Notez que cette configuration applique des stratégies anti-courrier indésirable, de filtrage du courrier indésirable sortant, anti-programme malveillant et anti-hameçonnage.

1. Dans la section *Appliquer la protection Defender pour Office 365*, effectuez la même configuration que l’étape précédente et sélectionnez **Suivant**. Notez que cette configuration applique des stratégies anti-hameçonnage, de pièces jointes fiables et de liens fiables.

1. Dans la section *Protection de l’emprunt d’identité*, sélectionnez **Suivant** quatre fois (4x) pour continuer.

1. Dans la section *Mode de stratégie*, vérifiez que la case d’option **Activer la stratégie une fois terminé** est sélectionnée, puis cliquez sur **Suivant**.

1. Lisez le contenu sous *Examinez et confirmez vos modifications* et sélectionnez **Confirmer** pour appliquer les modifications, puis cliquez sur **Terminé**.

    >**Remarque :** si vous recevez le message suivant *« L’URI https://outlook.office365.com/psws/service.svc/AntiPhishPolicy n’est pas valide pour l’opération PUT. L’URI doit pointer vers une seule ressource pour les opérations PUT. »* sélectionnez **OK**, puis **annuler** pour revenir à la page principale. Vous verrez que la *Protection standard est activée*.

1. Sous *Protection stricte*, sélectionnez **Gérer les paramètres de protection**. **Conseil :***la protection stricte* se trouve sous « E-mail & Collaboration - Stratégies et règles - Stratégies contre les menaces - Stratégies de sécurité prédéfinies ».

1. Dans *Appliquer Exchange Online Protection*, sélectionnez **Destinataires spécifiques** et sous **Groupes**, commencez à écrire **Leadership**, sélectionnez-le, puis cliquez sur **Suivant**. Notez que cette configuration applique des stratégies anti-courrier indésirable, de filtrage du courrier indésirable sortant, anti-programme malveillant et anti-hameçonnage.

1. Dans la section *Appliquer la protection Defender pour Office 365*, effectuez la même configuration que l’étape précédente et sélectionnez **Suivant**. Notez que cette configuration applique des stratégies anti-hameçonnage, de pièces jointes fiables et de liens fiables.

1. Dans la section *Protection de l’emprunt d’identité*, sélectionnez **Suivant** quatre fois (4x) pour continuer.

1. Dans la section *Mode de stratégie*, vérifiez que la case d’option **Activer la stratégie une fois terminé** est sélectionnée, puis cliquez sur **Suivant**.

1. Lisez le contenu sous *Examinez et confirmez vos modifications* et sélectionnez **Confirmer** pour appliquer les modifications, puis cliquez sur **Terminé**.

    >**Remarque :** si vous recevez le message suivant *« L’URI https://outlook.office365.com/psws/service.svc/AntiPhishPolicy n’est pas valide pour l’opération PUT. L’URI doit pointer vers une seule ressource pour les opérations PUT. »* sélectionnez **OK**, puis **annuler** pour revenir à la page principale. Vous verrez que la *Protection stricte est activée*.

### Tâche 3 : Préparation de l’espace de travail Microsoft Defender XDR

1. Dans le portail **Microsoft Defender**, dans le menu de navigation, sélectionnez **Accueil** à gauche.

    >**Remarque :** vous devrez peut-être faire défiler jusque tout en haut du menu.

1. Sur la page portail **d’accueil**, la **bannière Obtenir votre SIEM et XDR dans un seul emplacement** s’affiche.

1. Faites défiler les éléments de menu vers **Ressources** et sélectionnez **Appareils**.

1. Le processus de déploiement de l’espace de travail Defender XDR doit commencer et vous devez voir les messages indiquant *le chargement et l’initialisation* brièvement affichés en haut de la page, puis vous verrez une image d’une tasse de café et un message qui lit : **Tenez bon ! Nous préparons de nouveaux espaces pour vos données et nous les connectons.** Cette opération va prendre environ 5 minutes. *Laissez la page ouverte et assurez-vous qu’elle se termine correctement, car elle est requise pour le labo suivant.*

    >**Remarque :** si le message « Attendez ! Nous préparons de nouveaux espaces pour vos données et les connectons ne s’affiche pas, ou la page « Paramètres > Microsoft Defender > Compte » s’ouvre, mais vous voyez le message « Échec du chargement de l’emplacement de stockage des données. Réessayez ultérieurement » s’affiche, ouvrez le menu « Général » et sélectionnez « Paramètres du service d’alerte » ou accédez au menu de navigation, faites défiler jusqu’à la section « Ressources » et sélectionnez « Appareils ».

1. Une fois le nouvel espace terminé, vous verrez les paramètres généraux de Microsoft Defender XDR pour le compte, les notifications par e-mail, les paramètres du service d’alerte, les autorisations et les rôles et l’API streaming. L’option **Fonctionnalités en préversion** est également activée.

## Vous avez terminé le labo
