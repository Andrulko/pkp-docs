# Quelles données les applications PKP traitent-elles?


Les applications PKP traitent les données personnelles comme un élément fondamental de leurs opérations. La plupart des données sont fournies uniquement par consentement, c.-à-d. par enregistrement manuel de l'utilisateur, bien que certaines données de visite (par exemple les cookies, les journaux d'utilisation) puissent également être enregistrées.

## Données d'inscription de l'utilisateur
Lorsqu'un visiteur crée un compte utilisateur dans une application PKP, les informations personnelles suivantes sont traitées et stockées (avec quelques variations mineures entre OMP et OJS, et de version en version) :

- Civilité
- Prénom*
- Deuxième prénom
- Nom*
- Suffix
- Nom d'utilisateur
- Sexe
- Mot de passe (chiffré)
- Adresse e-mail*
- ORCiD ID
- Site Web
- Adresse postale
- Pays
- Téléphone
- Fax
- Affiliation
- Biographie
- Date d'inscription
- Date de la dernière connexion
- Locales
- Revue des intérêts
- Inscriptions de rôle (auteur, lecteur et/ou réviseur)

Seuls les champs nom d'utilisateur, prénom, nom de famille, email et mot de passe sont requis.

### Stockage

Ces informations sont stockées dans la base de données de l'application. Seul le mot de passe utilisateur est chiffré.

### Disponibilité et accès
Ces informations sont mises à la disposition de l'utilisateur via son profil d'utilisateur (et, à l'exception du nom d'utilisateur et des dates, peuvent être modifiées). Les administrateurs système, les gestionnaires de journaux et les éditeurs peuvent également accéder et modifier ces données (sauf le nom d'utilisateur et les dates) via le backend de l'application. Les données peuvent être téléchargées par les gestionnaires de journaux au format XML. Les données ne sont pas autrement accessibles au public.

### Effacement
Ces données peuvent être effacées par le gestionnaire de journaux à l'aide de l'outil Utilisateurs de Fusion, sans affecter aucun enregistrement éditorial. L’effacement est soumis aux considérations soulevées dans la section « Édition scientifique, confidentialité des données et intérêt public ».

## Métadonnées du contributeur

Lorsqu'un manuscrit est soumis à une application PKP, des renseignements sur les contributeurs sont inclus. Les contributeurs peuvent être des auteurs, des traducteurs, des éditeurs de volume, etc. Ces informations sont conservées sous forme de métadonnées de soumission et sont fournies dans le cadre de tout document manuscrit publié. Les informations suivantes du contributeur sont collectées :

- Civilité
- Prénom*
- Deuxième prénom
- Nom*
- Adresse e-mail*
- Suffix
- ORCiD ID
- Site Web
- Pays*
- Affiliation
- Biographie

Seuls les champs prénom, nom, adresse e-mail et pays sont requis.

### Stockage

Ces informations sont stockées dans la base de données de l'application.

### Disponibilité et accès

Ces renseignements sont accessibles à presque tous les participants à la soumission, avec certaines restrictions pour préserver le processus d’examen aveugle par les pairs. En bref, les auteurs contributeurs, les rédacteurs et les assistants éditoriaux peuvent tous voir ces données ; dans la plupart des cas, seul le personnel éditorial peut modifier ces données après la soumission.

Les rédacteurs en chef peuvent télécharger ces données par l'intermédiaire de l'auteur et des rapports de soumission.

Plus important : une fois qu'une soumission a été publiée, ces données sont rendues publiques en ligne de diverses façons. Il est disponible sur la page d'accueil de la soumission aux lecteurs, est disponible pour les services d'indexation dans les balises de métadonnées, est disponible via un point de terminaison OAI-PMH pour la récolte, et peut être disponible de quelque manière que ce soit via d'autres plugins système.

### Effacement

Ces données peuvent être effacées par n'importe quel éditeur en modifiant les métadonnées d'une soumission. Cela peut être fait à n'importe quel moment du processus de soumission, y compris après publication. Erasure est assujettie aux considérations soulevées dans la section « Édition scolaire, confidentialité des données et intérêt public » ci-dessus.

## Données du flux de travail

Toutes les applications PKP suivent les informations de flux de travail, principalement en tant qu'historique éditorial spécifique aux soumissions. Le système suit :

- Toutes les actions entreprises sur une soumission, et par qui;
- Toutes les notifications envoyées concernant une soumission (y compris qui a envoyé et reçu la notification);
- Toutes les recommandations des réviseurs ;
- Toutes les décisions éditoriales;
- Tous les fichiers téléchargés dans le cadre du processus de soumission, y compris les fichiers qui peuvent avoir des informations d'identification personnelle sous forme de métadonnées de fichier ou dans les fichiers eux-mêmes.

### Stockage

Ces informations sont stockées dans la base de données de l'application, à l'exception de tous les fichiers envoyés qui sont stockées dans le répertoire des fichiers soumis de l'application sur le serveur Web.

### Disponibilité et accès

Les participants à la soumission ont accès à différentes quantités de données de flux de travail selon leur rôle. Les gestionnaires de journaux et les éditeurs peuvent accéder à toutes les données de soumission ; les éditeurs de section et les assistants à la rédaction ne peuvent accéder à toutes les données de soumission que pour les soumissions auxquelles ils ont été assignés ; les auteurs ont un accès limité à leurs propres soumissions, et ne peuvent voir que les données qu'ils ont fournies, ou que les rédacteurs ont explicitement mis à leur disposition.

### Effacement

Ces données ne peuvent être effacées que par l'éditeur, en rejetant et en supprimant purement et simplement la soumission ; ou par un administrateur système via une intervention directe dans la base de données ou le répertoire des fichiers soumis. Erasure est assujettie aux considérations soulevées dans la section « Édition scolaire, confidentialité des données et intérêt public » ci-dessus.

## Informations générales sur le visiteur

Les applications PKP collectent également des données générales d'utilisation des visiteurs, y compris :

- Informations sur les cookies, pour gérer l'historique des sessions. Les cookies sont nécessaires pour maintenir une session de connexion dans les applications PKP.
- Optionnellement, des données détaillées du journal d'utilisation, y compris : adresse IP ; pages visitées ; date visitée ; et les informations du navigateur, dans les fichiers journaux de l'application, dans le cadre du plugin Statistiques d'utilisation. Une option d’anonymisation est disponible pour privatiser ces informations.
- Optionnellement, les informations sur le pays, la région et la ville dans la base de données des métriques. Cette collecte de données nécessite une installation supplémentaire et n'est pas activée par défaut.

D'autres données peuvent être suivies, soit sur le serveur, soit via des tiers :

- Charger un script depuis un serveur CDN ;
- Informations sur l'adresse IP (y compris la date, le navigateur, etc.) dans les logs du serveur web (séparées des fichiers journaux de l'application dans le cadre du plugin Statistiques d'utilisation).

Vous trouverez ci-dessous des instructions détaillées pour limiter la quantité de données que vous collectez et donner votre consentement aux données que vous collectez.

### Stockage

- Cookies : Un cookie (habituellement intitulé « OJSSID » ou « OMPSID ») est créé lors de la première visite d’une application PKP et est stocké sur l’ordinateur du visiteur. Il n'est utilisé que pour stocker un ID de session et pour faciliter les connexions. (Si le visiteur bloque les cookies, OJS fonctionnera toujours correctement, mais il ne pourra pas se connecter.)
- Fichiers journaux des statistiques d'utilisation : Dans le cadre de la structure des statistiques d'utilisation et du plugin, OJS peut stocker les fichiers journaux détaillés de l'application dans le répertoire des fichiers de soumission (configuré en tant que paramètre files_dir dans la configuration OJS. nc.php file), dans un répertoire « usageStats ».
- Données géographiques : Les données d'utilisation filtrées, y compris éventuellement des données géographiques, sont également stockées dans la base de données OJS, dans une table « métriques ».

### Disponibilité et accès

- Cookies: Ces cookies sont disponibles via les paramètres du navigateur du visiteur.
- Fichiers journaux des statistiques d'utilisation : seuls les individus ayant accès au serveur peuvent accéder aux fichiers journaux de l'application.
- Données géographiques : Les gestionnaires de journaux peuvent accéder aux données d'utilisation filtrées en utilisant les plugins de rapport d'utilisation d'OJS.

### Effacement

- Cookies: Ces cookies peuvent être supprimés via le navigateur du visiteur.
- Fichiers journaux des statistiques d'utilisation : Ces fichiers peuvent être effacés par les administrateurs système ayant accès aux fichiers.
- Données géographiques : Ceci ne peut être effacé qu'en supprimant directement les enregistrements de la base de données, ce qui nécessite généralement un accès administrateur système.
