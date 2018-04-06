# Test Google Cloud

Il y a plusieurs services qui m'interesse pour le Big Data:

* Google Storage: file system, comme HDFS
* Google Big Query: SQL sur du Big Data, comme Hive
* Google DataProc: Spark as a Service
* Google DataLab: Notebook as a Service

![](img/Menu.png)


## Google Storage

Facile à manipuler, il suffit de créer des "buckets" et d'y déposer des dossiers/fichiers

![](img/Buckets.png)

J'ai déposé un CSV tout simplement (qui provient de https://eddb.io/api )

## BigQuery

L'IHM est sommaire, mais ça permet de requêter la data en SQL.

On peut créer un "dataset" qui est une sorte de base, et des tables dans le dataset.
On peut créer des tables internes, ou externes. Pour les tables externes ça peut pointer sur Google Storage avec une url gs://bucket/folder/*

![](img/BigQuery_Create_Table.png)

J'ai alors fait une table sur le CSV avec détection du schéma, et ça a marché.
A noter qu'on peut faire des tables sur du Avro ou Parquet.

![](img/BigQuery_Format.png)

J'ai ensuite fait un "Create Table as Select" pour créer une table interne à partir d'un "select \*" de la table externe.

![](img/BigQuery_CTAS.png)

On peut voir ici les tables/schémas/preview:

![](img/BigQuery_Table.png)

![](img/BigQuery_Schema.png)

![](img/BigQuery_preview.png)

On peut faire des requêtes avec réponses imédiate (interactive) ou schédulé dans une file d'attente pour du batch (moins cher).
On a l'historique des requêtes:

![](img/BigQuery_query.png)

![](img/BigQuery_query_details.png)

On peut faire des UDF en Javascript on dirait...

![](img/BigQuery_UDF.png)

J'ai ensuite testé MicroStrategy Desktop, qui possède un connecteur natif et qui fonctionne très bien.

![](img/Microstrategy_BigQuery.png)

![](img/Microstrategy_Preview.png)

![](img/Microstrategy_Dashboard.png)

Comme l'IHM de BigQuery est pas très sexy, j'ai cherché autre chose et j'ai trouvé https://www.metabase.com/

Ca scan les tables des datasets BigQuery et ça permet de faire des requêtes SQL ou avec un éditeur de query sympa.

Dans la partie d'administration, on peut documenter les tables, les colonnes, ajouter des "segments" (filtre pré-défini pour avoir un sous-ensemble de la table), ajouter des métrics (colonne numérique sur laquel on peut aggréger).

![](img/Metabase_Schema.png)

On peut ensuite requêter les données, ou comme ils le disent "poser une question":

![](img/Metabase_Tables.png)

![](img/Metabase_Table.png)

![](img/Metabase_Table_questions.png)

![](img/Metabase_Table_preview.png)

![](img/Metabase_Table_Questions.png)

On peut afficher le résultat de la question sous forme de table, mais aussi sous forme de graph.

![](img/Metabase_Interactive.png)

Et si l'éditeur de requête n'est pas suffisant, on peut écrire le SQL directement:

![](img/Metabase_Query_SQL.png)

On peut ensuite créer des dashboard à partir de ça (et même rafraichir régulièrement et publier le rapport par email/slack)

![](img/Metabase_Dashboard.png)

![](img/Metabase_Dashboard_Edit.png)

## DataLab

## DataProc









