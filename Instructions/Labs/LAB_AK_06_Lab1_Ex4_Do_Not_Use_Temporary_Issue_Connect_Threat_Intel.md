 **Ne pas utiliser. Temporairement non opérationnel.**

# Parcours d’apprentissage 6 - Labo 1 - Exercice 4 - Connecter le renseignement sur les menaces à Microsoft Sentinel à l’aide de connecteurs de données

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à connecter des données de journal provenant de nombreuses sources de données dans votre organisation. Enfin, vous connectez un flux de renseignement sur les menaces pour améliorer votre capacité à détecter et à hiérarchiser les menaces connues.

### Tâche 1 : connecter le renseignement sur les menaces

Dans cette tâche, vous allez connecter un fournisseur de renseignements sur les menaces à Renseignement sur les menaces – Connecteur TAXII.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Sous l’onglet Connecteurs de données, recherchez **Renseignement sur les menaces - Connecteur TAXII**.

1. Sélectionnez **Ouvrir la page du connecteur** dans le panneau d’informations du connecteur.

1. Sous la zone *Configuration*, dans le champ **Nom convivial (pour le serveur),** entrez *PhishURLs*

1. Pour l’URL racine de l’API, entrez <https://limo.anomali.com/api/v1/taxii2/feeds/>.

1. Entrez **107** pour l’ID de la collection.

1. Entrez **Invité** pour le nom d’utilisateur.

1. Entrez **Invité** pour le mot de passe.

1. Sélectionnez ensuite le bouton **Ajouter**.  Les URL d’hameçonnage sont extraites et remplissent la table ThreatIntelligenceIndicator.

>**Remarque :** si vous souhaitez ajouter une autre collection, ouvrez <https://limo.anomali.com/api/v1/taxii2/feeds/collections/> dans le navigateur Edge et utilisez le nom d’utilisateur et le mot de passe d’invité pour passer en revue les différents ID disponibles.

## Vous avez terminé le labo
