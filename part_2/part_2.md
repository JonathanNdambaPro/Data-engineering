# Qu'est-ce que le cycle de vie de l'ingénierie des données ?

Le cycle de vie de l'ingénierie des données comprend des étapes qui transforment les ingrédients des données brutes en un produit final utile, prêt à être consommé par les analystes, les scientifiques des données, les ingénieurs ML et autres.

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.001.png" />
</p>

Le cycle de vie des données par rapport au cycle de vie de l'ingénierie des données

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.002.png" />
</p>

## Génération : systèmes sources

Un système source est l'origine des données utilisées dans le cycle de vie de l'ingénierie des données

- appareil IoT
- file d'attente de messages d'application
- une base de données transactionnelle
- etc.

Un ingénieur de données consomme les données d'un système source Exemple :

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.003.png" />
</p>

Une base de données d'application

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.004.png" />
</p>

IoT swarm and message queue

Considération :

- Quelles sont les caractéristiques essentielles de la source de données ? Est-ce une application ? Un essaim d'appareils IoT ?
- Comment les données sont-elles conservées dans le système source ? Les données sont-elles conservées à long terme ou sont-elles temporaires et rapidement supprimées ?
- À quelle vitesse les données sont-elles générées ? Combien d'événements par seconde ? Combien de gigaoctets par heure ?
- Quel niveau de cohérence les ingénieurs de données peuvent-ils attendre des données de sortie ? Si vous exécutez des contrôles de qualité des données par rapport aux données de sortie, à quelle fréquence les incohérences de données se produisent-elles ?
- À quelle fréquence les erreurs se produisent-elles ?
- Les données contiendront-elles des doublons ?
- Certaines valeurs de données arriveront-elles en retard, peut-être beaucoup plus tard que d'autres messages produits simultanément ?
- Quel est le schéma des données ingérées ? Les ingénieurs de données devront-ils se joindre à plusieurs tables ou même à plusieurs systèmes pour obtenir une image complète des données ?
- Si le schéma change (par exemple, une nouvelle colonne est ajoutée), comment cela est-il traité et communiqué aux parties prenantes en aval ?
- À quelle fréquence les données doivent-elles être extraites du système source ?
- Pour les systèmes avec état (par exemple, une base de données de suivi des informations de compte client), les données sont-elles fournies sous forme d'instantanés périodiques ou d'événements de mise à jour à partir de modifier la capture de données (CDC) ? Quelle est la logique d'exécution des modifications et comment sont-elles suivies dans la base de données source ?
- Qui/quel est le fournisseur de données qui transmettra les données pour la consommation en aval ?
- La lecture d'une source de données aura-t-elle un impact sur ses performances ?
- Le système source a-t-il des dépendances de données en amont ? Quelles sont les caractéristiques de ces systèmes en amont ?
- Des contrôles de la qualité des données sont-ils en place pour vérifier les données tardives ou manquantes ?

### Schéma : L'organisation des données, descriptif

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.005.png" />
</p>

- Schemaless : le schéma au fur et à mesure que les données sont écrites, que ce soit dans une file d'attente de messages, un fichier plat, un blob ou une base de données de documents
- Schéma fixe : description appliquée dans la base de données, auquel les écritures d'application doivent se conformer

Le schéma est la considération la plus importante à prendre dû à son évolution constante et la possibilité de casser les autres étapes du cycle.

### Stockage

Là les données sont stockées, cette étape est présente dans tout le cycle de données

Plusieurs considérations :

- Les architectures de données s'appuient souvent sur plusieurs solutions de stockage
- Peu de solutions de stockage de données fonctionnent uniquement comme stockage
- Cette étape fréquemment à d'autres étapes, telles que l'ingestion, la transformation et le service
- Cette solution de stockage est-elle compatible avec les vitesses d'écriture et de lecture requises par l'architecture ?
- Le stockage créera-t-il un goulot d'étranglement pour les processus en aval ?
- Comprenez-vous comment fonctionne cette technologie de stockage ? Utilisez-vous le système de stockage de manière optimale ou commettez-vous des actes contre nature ? Par exemple, appliquez-vous un taux élevé de mises à jour d'accès aléatoire dans un système de stockage d'objets ? (Il s'agit d'un anti-modèle avec une surcharge de performances significative.)
- Ce système de stockage gérera-t-il l'échelle future prévue ? Vous devez tenir compte de toutes les limites de capacité du système de stockage : stockage total disponible, taux d'opération de lecture, volume d'écriture, etc.
- Les utilisateurs et les processus en aval pourront-ils récupérer les données dans le contrat de niveau de service (SLA) requis ?
- Capturez-vous des métadonnées sur l'évolution du schéma, les flux de données, le lignage des données, etc. ? Les métadonnées ont un impact significatif sur l'utilité des données. Les métadonnées représentent un investissement dans l'avenir, améliorant considérablement la découvrabilité et les connaissances institutionnelles pour rationaliser les futurs projets et changements d'architecture.
- S'agit-il d'une solution de stockage pur (stockage d'objets) ou prend-elle en charge des modèles de requêtes complexes (c'est-à-dire un entrepôt de données cloud) ?
- Le système de stockage est-il indépendant du schéma (stockage d'objets) ? Schéma flexible (Cassandre) ? Schéma appliqué (un entrepôt de données cloud) ?
- Comment suivez-vous les données de référence, la qualité des données des enregistrements d'or et la lignée des données pour la gouvernance des données ? (Nous avons plus à dire à ce sujet dans "Gestion des données" .)
- Comment gérez-vous la conformité réglementaire et la souveraineté des données ? Par exemple, pouvez-vous stocker vos données dans certaines zones géographiques mais pas dans d'autres ?

### Ingestion

L’étape qui suit après la génération de données, il s’agit de l’intégration des données dans l’architecture de données.

Plusieurs considérations :

- Quels sont les cas d'utilisation des données que j'ingère ? Puis-je réutiliser ces données plutôt que de créer plusieurs versions du même jeu de données ?
- Les systèmes génèrent-ils et ingèrent-ils ces données de manière fiable, et les données sont-elles disponibles quand j'en ai besoin ?
- Quelle est la destination des données après ingestion ?
- À quelle fréquence aurai-je besoin d'accéder aux données ?
- Dans quel volume les données arriveront-elles généralement ?
- Dans quel format sont les données ? Mes systèmes de stockage et de transformation en aval peuvent-ils gérer ce format ?
- Les données source sont-elles en bon état pour une utilisation immédiate en aval ? Si oui, combien de temps et qu'est-ce qui peut le rendre inutilisable ?
- Si les données proviennent d'une source de streaming, doivent-elles être transformées avant d'atteindre leur destination ? Une transformation en cours serait-elle appropriée, où les données sont transformées dans le flux lui-même ?

## Batch versus streaming

Batch : Est un traitement en streaming regroupé en lot puis traiter à des fréquences moindre (1 heure, 1 jour, etc…) pour faciliter l’ingestion

Streaming : Ingère les données en near realtime sans les regrouper en amont, la latence de l’arrivée varie selon les besoins et la source

Considération :

- Si j'ingère les données en temps réel, les systèmes de stockage en aval peuvent-ils gérer le débit de flux de données ?
- Ai-je besoin d'une ingestion de données en temps réel d'une milliseconde ? Ou une approche par micro-lots fonctionnerait-elle, accumulant et ingérant des données, disons, chaque minute ?
- Quels sont mes cas d'utilisation pour l'ingestion de flux ? Quels avantages spécifiques puis-je réaliser en mettant en œuvre le streaming ? Si j'obtiens des données en temps réel, quelles actions puis-je entreprendre sur ces données qui constitueraient une amélioration par rapport au lot ?
- Mon approche axée sur le streaming coûtera-t-elle plus en termes de temps, d'argent, de maintenance, de temps d'arrêt et de coût d'opportunité que de simplement faire du batch ?
- Mon pipeline et mon système de streaming sont-ils fiables et redondants en cas de défaillance de l'infrastructure ?
- Quels outils sont les plus appropriés pour le cas d'utilisation ? Dois-je utiliser un service managé (Amazon Kinesis, Google Cloud Pub/Sub, Google Cloud Dataflow) ou monter mes propres instances de Kafka, Flink, Spark, Pulsar, etc. ? Si je fais ce dernier, qui le gérera? Quels sont les coûts et les compromis ?
- Si je déploie un modèle de ML, quels sont les avantages des prédictions en ligne et éventuellement de la formation continue ?
- Est-ce que je reçois des données d'une instance de production en direct ? Si oui, quel est l'impact de mon processus d'ingestion sur ce système source ?

## Push versus pull

Push : un système source écrit des données vers une cible Pull: les données sont extraites du système source

## Transformation

Apères l’ingestion et le stockage, ce qui signifie que les données doivent être modifiées de leur forme d'origine en quelque chose d'utile pour les cas d'utilisation en aval création de valeur

Consdération :

- Quels sont le coût et le retour sur investissement (ROI) de la transformation ? Quelle est la valeur commerciale associée ?
- La transformation est-elle aussi simple et isolée que possible ?
- Quelles règles métier les transformations prennent-elles en charge ?

## Servir des données

la dernière étape du cycle de vie de l'ingénierie des données. Maintenant que les données ont été ingérées, stockées et transformées en structures cohérentes et utiles, il est temps de valoriser vos données. Les données ont valeur lorsqu'il est utilisé à des fins pratiques

## Analytique

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.006.png" />
</p>

au cœur de la plupart des efforts de données Business intelligence

- BI : collecte des données pour décrire l'état passé et actuel d'une entreprise
- La BI nécessite l'utilisation d'une logique métier pour traiter les données brutes.

## Operational analytics

- Analyse opérationnelle se concentre sur les détails fins des opérations, en promouvant des actions sur lesquelles un utilisateur des rapports peut agir immédiatement
- Peut être une vue en direct de l'inventaire ou un tableau de bord en temps réel de la santé du site Web ou de l'application
- Se concentre sur le présent et ne concerne pas nécessairement les tendances historiques

## Embedded analytics

un peu comme la BI, mais se concentre sur des clients extérieurs à l’entreprise, ce qui conduit à des complexifications

- Les analyses fournies aux clients sur une plate-forme SaaS
- Le taux de demande de rapports et la charge correspondante sur les systèmes d'analyse augmentent considérablement
- Le contrôle d'accès est beaucoup plus compliqué et critique
- Les entreprises peuvent fournir des analyses et des données distinctes à des milliers de clients ou plus
- Chaque client doit voir ses données et uniquement ses données
- Une fuite de données entre clients serait considérée comme un abus de confiance massif, entraînant l'attention des médias et une perte importante de clients

## Machine learning

Consiste à utiliser des modèles statistiques pour l’aide à la prise de décision automatique, les entreprises qui s’y mettent prématurément ont tendance à échouer leur projet

Considération :

- Les données sont-elles de qualité suffisante pour effectuer une ingénierie des fonctionnalités fiable ? Les exigences de qualité et les évaluations sont élaborées en étroite collaboration avec les équipes consommatrices de données.
- Les données sont-elles détectables ? Les data scientists et les ingénieurs ML peuvent-ils facilement trouver des données précieuses ?
- Où sont les frontières techniques et organisationnelles entre l'ingénierie des données et l'ingénierie ML ? Cette question organisationnelle a des implications architecturales importantes.
- L'ensemble de données représente-t-il correctement la vérité terrain ? Est-il injustement biaisé ?

## Reverse ETL

Consiste à réinjecter les données dans les systèmes source comme les systèmes en production ou les plateformes SaaS.

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.007.png" />
</p>

- les entreprises peuvent vouloir pousser des métriques spécifiques de leur entrepôt de données vers une plateforme de données client ou un système CRM.
- Les plateformes publicitaires sont un autre cas d'utilisation courante (Google Ads)

Tout ce qui entoure le cycle de vie de la data ingénierie

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.008.png" />
</p>

## Sécurité

Plusieurs considération :

- La sécurité des données : fournir un accès aux données exactement aux personnes et aux systèmes qui doivent y accéder et uniquement pendant la durée nécessaire à l'exécution de leur travail
- Le principe du moindre privilège : un utilisateur ou un système n'a accès qu'aux données et ressources essentielles pour exécuter une fonction prévue.

## Data Management

- Gouvernance des données, y compris la découvrabilité et la responsabilité
- Modélisation et conception des données
- Lignage des données
- Stockage et opérations
- Intégration et interopérabilité des données
- Gestion du cycle de vie des données
- Systèmes de données pour l'analyse avancée et le ML
- Éthique et confidentialité

## Data governance

La gouvernance des données est, avant tout, une fonction de gestion des données pour assurer la qualité, l'intégrité, la sécurité et la convivialité des données collectées par une organisation.

La gouvernance des données engage les personnes, les processus et les technologies pour maximiser la valeur des données dans une organisation tout en protégeant les données avec des contrôles de sécurité appropriés

## Discoverability

Dans une entreprise axée sur les données, les données doivent être disponibles et découvrables.

## Metadata

Les métadonnées sont"des données sur les données", Les métadonnées sont exactement les données nécessaires pour rendre les données détectables et gouvernables

deux types de metadata :

- générées automatiquement
- généré par l'homme

Méthode et outils de gestion de metadata :

- data catalogs
- data-lineage tracking systems
- metadata management tools

Métadonnées utilisé par le data engineer :

- Business metadata
- Technical metadata
- Operational metadata
- Reference metadata

Business metadata : concernent la manière dont les données sont utilisées dans l'entreprise, y compris les définitions d'entreprise et de données, les règles et la logique des données, comment et où les données sont utilisées, et le(s) propriétaire(s) des données

Technical metadata : décrit les données créées et utilisées par les systèmes tout au long du cycle de vie de l'ingénierie des données

- data model & schema
- data lineage
- field mappings
- pipeline workflows | Pipeline metadata (produit par l’orchestration)

Operational metadata :

Décrit les résultats opérationnels de divers systèmes et comprend des statistiques sur les processus, les ID de travail, les logs d'exécution des applications, les données utilisées dans un processus et les logs d'erreurs. Un ingénieur de données utilise des métadonnées opérationnelles pour déterminer si un processus a réussi ou échoué et les données impliquées dans le processus

Reference metadata :

Les métadonnées de référence sont données utilisées pour classer d'autres données. Ceci est également mentionné comme données de recherche . Des exemples standard de données de référence sont les codes internes, les codes géographiques, les unités de mesure et les normes de calendrier interne. Les données de référence sont essentiellement une norme pour interpréter d'autres données, donc si elles changent, ce changement se produit lentement au fil du temps

## Data accountability

signifie assigner à un individu la gestion d'une partie des données. La personne responsable coordonne ensuite les activités de gouvernance des autres parties prenantes. La gestion de la qualité des données est difficile si personne n'est responsable des données en question.

## Data quality

Puis-je faire confiance à ces données ? Les données doivent être conformes aux attentes des métadonnées d'entreprise. Un ingénieur de données assure la qualité des données tout au long du cycle de vie de l'ingénierie des données. Cela implique d'effectuer des tests de qualité des données et de garantir la conformité des données aux attentes du schéma, l'exhaustivité et la précision des données.

- Accuracy : les données collectées sont-elles factuellement correctes ? Existe-t-il des valeurs en double ? Les valeurs numériques sont-elles exactes ?
- Completeness : les données sont-elles complètes ? Tous les champs obligatoires contiennent-ils des valeurs valides ?
- Timeliness : les données sont-elles arrivées à temps pour répondre au besoin ?

## Data modeling and design

Pour créer de la valeur à partir des données, ces dernières doivent avoir une forme utilisable, c’est le data modeling et design. Beaucoup d’entreprise n’ont au début pas pris en considération cette partie, ce qui a donné naissance au *data swamp*.

## Data lineage

décrit l'enregistrement d'une piste d'audit des données tout au long de leur cycle de vie, en suivant à la fois les systèmes qui traitent les données et les données en amont dont elles dépendent, permet de savoir où ces données sont stockées et ses dépendances

## Data lifecycle management

il s’agit de gérer le cycle de vie de la donnée, quand est-ce qu’elles sont intégrées dans l’architecture de données, comment elles sont stockées et quand les supprimées.

Considération :

- Coût : le stockage infini des données avec la pensée, “elles pourront toujours servie” engendre des dépenses si elles ne sont pas gérées, par exemple sur le cloud, on peut pousser les données dans une classe dites d’archivage dans un datalake où le coût est beaucoup moins chère.
- RGPD : Le droit à l’oublie des clients doit être respecté si ce dernier demande la suppression des données le concernant. (il existe d’autre réglementation en fonction de la zone géographique où l’on se situe, il faut y faire attention)

## Ethics and privacy

Les données ont amené à de la manipulation de masse comme “Cambridge Analytica”, aux vus des nombreux scandales les États ont réagi et demander une rigueur beaucoup plus grande au niveau de l’utilisation des données.

le data engineer doit à son niveau gérer ces problématiques comme le masquage des données PII (adresse, nom, prénom, numéro de carte vitale…)

## DataOps

Mélange de Devops et agilité pour les données, Alors que DevOps vise à améliorer la publication et la qualité des produits logiciels, DataOps fait la même chose pour les produits de données.

<p align="center">
  <img src="Aspose.Words.2b3410a0-5c6f-4572-b855-97a29ab197a1.009.png" />
</p>

## Automation

permet la fiabilité et la cohérence du processus DataOps et permet aux ingénieurs de données de déployer rapidement de nouvelles fonctionnalités de produit et des améliorations aux flux de travail existants.

- Gestion des changements
- Contrôle de l'environnement
- Contrôle du code
- Versionning des données
- Intégration continue/le déploiement continu (CI/CD)
- vérification de la qualité des données
- intégrité des métadonnées

## Observability and monitoring

Consiste à l’observation et la surveillance des données et pipeline, en effet des mauvaises données peuvent amener au mieux à une perte de confiance, aux pires à des décisions stratégiques mauvaise pouvant conduire à la faillite de l’entreprise.

- observability
- monitoring
- logs
- alerting
- tracking

## Incident response

consiste à utiliser les capacités d'automatisation et d'observabilité mentionnées précédemment pour identifier rapidement les causes profondes d'un incident et le résoudre de la manière la plus fiable et la plus rapide possible.

"Tout se casse tout le temps"

- Réponse technologique
- interaction avec les principaux concernés (source et cible)

## Data Architecture

Reflète l'état actuel et futur des systèmes de données qui prennent en charge les besoins et la stratégie de données à long terme d'une organisation.

- Comprendre les besoins de l'entreprise et rassembler les exigences pour de nouveaux cas d'utilisation
- traduire ces exigences pour concevoir de nouvelles façons de capturer et de servir des données
- équilibrées pour le coût et la simplicité opérationnelle

## Orchestration

Le processus de coordination de nombreux travaux pour qu'ils s'exécutent aussi rapidement et efficacement que possible selon une cadence planifiée

un moteur d'orchestration construit des métadonnées sur les dépendances de travail, généralement sous la forme d'un graphe acyclique dirigé (DAG). Le DAG peut être exécuté une fois ou programmé pour s'exécuter à un intervalle fixe quotidien, hebdomadaire, toutes les heures, toutes les cinq minutes, etc.

## Software Engineering

Au début de l’ère du data engineering, la majorité des outils utilisés étaient de bas niveaux, il fallait avoir une bonne maîtrise de chaque outil ce qui pouvait être très chronophage et pouvait demander énormément de temps et nécessité une grande maturité en termes de génie logiciel. Aujourd’hui ont subi une abstraction (simplification d’utilisation) qui a réduit radicalement la courbe d’apprentissage des outils, cependant le software engineering n’en reste pas moins une compétence nécessaire au data engineer.

Liste non exhaustive :

- Maitrise de langage :
  - SQL
  - Python
  - Bash
- framework :
  - Spark
  - airflow
  - Beam (dans un futur proche si l’adoption suit son cours)
- Infrastructure as code
