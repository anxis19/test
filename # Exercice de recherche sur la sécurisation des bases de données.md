# Exercice de recherche  sur la sécurisation des Bases de données 

## Partie 1 : Attaques et types d'attaques liées aux bases de données

|Type d'attaque    |Attaque        |
|-------- |----------    |
|  Modification |Abus de privilège excessif , Elevation de privilège
|Interruption |déni de service| 
|Fabrication |Exploitation des failles des bases de données vulnérables ou mal configurées, Injection SQL,Copies non autorisées de données sensibles


## Partie 2 : Politique de sécurité de l'ITSEC
Les ITSEC définissent la politique de 
sécurité comme l’ensemble des lois règles 
ou pratiques qui régissent la façon dont 
l’information sensible et les autres 
ressources sont gérées, protégées et 
distribuées à l’intérieur d’un système 
d’information.

## Partie 3 : Fichiers dans lesquels sont stockés les données dans les systèmes de gestion de bases de données MYSQL,POSTGRESSQL,SQLSERVER ,ORACLE

### MYSQL
  Les fichiers correspondant aux bases de données créées se trouvent dans le répertoire d'installation de MySQL, dans le sous répertoire "data". Ce sont des fichiers .frm et .ibd, mais ils ne sont pas lisibles et exploitables en l'état,

Ici nous allons voir comment MySQL enregistre les données physiquement sur le disque dur.

Premier point, il n'y a pas de généralité là dessus, en fait cela dépend du moteur de base de données que vous utilisez. Donc on ne va aborder que les 2 moteurs les plus utilisés : MyISAM et InnoDB.

MyISAM et les fichiers .MYD, .MYI
Commençons par MyISAM, le moteur de table par défaut.

1. MySQL stocke les tables MyISAM dans un dossier portant le nom de la base de données. Par exemple la table wp_options d'une base nommée pstutosera stockée dans 3 fichiers :

      C:\EasyPHP\mysql\data\pstuto\wp_options.frm
C:\EasyPHP\mysql\data\pstuto\wp_options.MYD
C:\EasyPHP\mysql\data\pstuto\wp_options.MYI
Le fichier .frm contient la définition de la table, c'est-à-dire sa structure, aussi appelée schéma (en gros c'est la liste des colonnes, leur type...).

     Le fichier .MYD contient les données de la table, les tuples (D comme Data).Le fichier .MYI contient les indexes (qui servent à optimiser les performances en lecture)

     Cette séparation entre les différentes bases et les différentes bases est très pratique, elle permet même de faire ce qu'on appelle des "hot backup" ou "hot restore", c'est-à-dire sauvegarder ou restaurer directement ces fichiers, plutôt que de passer un import/export SQL.



1. InnoDB et le fichier ibdata1
InnoDB a un fonctionnement totalement différent. C'est bien simple : InnoDB stocke tout dans un seul et même fichier : bases, tables, indexes... absolument tout !

Ce fichier s'appelle ibdata1, vous le trouverez au même endroit que les fichiers MyISAM :

C:\EasyPHP\mysql\data\ibdata1
Généralement ce fichier a une taille assez importante au regard de son contenu, car MySQL "réserve" l'espace disque. Cela permet d'éviter la fragmentation et d'améliorer les performances, au détriment de l'espace disque.

D'ailleurs cette technique d'allocation est aussi utilisée, par exemple, pour le fichier de swap (pagefile.sys) ou les fichiers de disque vmware.

3. Sous Windows et avec WampServer, votre base de données se trouve ici : "c:\Wamp\bin\mysql\mysql5.7.13\data".
Si votre base se nomme 'essai', vous aurez un répertoire de nom 'essai'.
Vous trouverez dedans toutes les tables de votre base.


### SQLSERVER

SQL Server bases de données ont trois types de fichiers, comme indiqué dans le tableau suivant.

|   Fichier|Description      |
|-------- |----------    |
|Principal |Contient les informations de démarrage de la base de données et pointe vers les autres fichiers de la base de données. Chaque base de données comprend un fichier de données primaire. L'extension de fichier recommandée est .mdf.|
|Secondary |Fichier de données facultatif défini par l'utilisateur. Les données peuvent être réparties sur plusieurs disques en plaçant chaque fichier sur un lecteur de disque différent. L'extension de fichier recommandée est .ndf.| 
|Journal des transactions|Ce journal contient les informations utilisées pour la récupération de la base de données. Chaque base de données doit posséder au moins un fichier journal. L'extension de fichier recommandée pour les journaux des transactions est .ldf

Moteur de base de données fichiers de données: \Program Files\Microsoft SQL Server\MSSQL{nn}.<ID_Instance>


### POSTGRESSQL 

Traditionnellement, les fichiers de configuration et les fichiers de données utilisés par une instance du serveur sont stockés ensemble dans le répertoire des données, habituellement référencé en tant que PGDATA (d'après le nom de la variable d'environnement qui peut être utilisé pour le définir). Un emplacement courant pour PGDATA est /var/lib/pgsql/data


### ORACLE 

Le répertoire /var/opt/SUNWscor/oracle_server contient les fichiers journaux du serveur Oracle Database.

Le répertoire /var/opt/SUNWscor/oracle_listener contient les fichiers journaux du listener Oracle Database.

Le répertoire /var/opt/SUNWscor/oracle_asm contient le fichier journal d'Oracle ASM.



## Partie 4 :

CE DANGEREUX MALWARE ANDROID VIDE LE COMPTE BANCAIRE DE SES VICTIMES
Pour infiltrer les smartphones de leurs victimes, les pirates récupèrent des applications légitimes sur le Play Store afin d'y intégrer un morceau de code malveillant. Ces applications vérolées sont ensuite proposées au téléchargement sur des magasins d'applications alternatifs. Il s'agit en général de jeux, de réseaux sociaux ou d'applications bancaires populaires.

Une fois installé sur le smartphone, le malware va garder un oeil sur les SMS reçus. Ainsi, le logiciel malveillant peut rester dormant pendant plusieurs années jusqu'au jour où un SMS en provenance d'une banque sera repéré. Il va alors s'emparer des données (identifiants et mot de passe) transmises en clair par les services bancaires. Parfois, le malware récupère aussi les coordonnées bancaires en affichant une fenêtre de connexion factice. Les utilisateurs entrent alors machinalement leurs identifiants. C'est là que les pirates obtiennent ce qu'ils souhaitent. Selon Avast, le maliciel est capable d'imiter l'interface de cinq banques d'Europe de l'Est.