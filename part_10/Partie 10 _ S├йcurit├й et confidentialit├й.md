Sécurité et confidentialité

![](Aspose.Words.898f9fa5-3ee3-465e-9c51-d2abf82e1c6a.001.png)

**Personnes**

le maillon le plus faible en matière de sécurité et de confidentialité, c'est *vous* . La sécurité est souvent compromise au niveau humain, alors, comportez-vous comme si vous étiez toujours une cible. Un bot ou un acteur humain essaie d'infiltrer vos identifiants et informations sensibles à tout moment. C'est notre réalité, et elle ne va pas disparaître

**Le pouvoir de la pensée négative**

La pensée négative nous permet d'envisager des scénarios désastreux et d'agir pour les prévenir.

Les ingénieurs de données doivent réfléchir activement aux scénarios d'utilisation des données et collecter des données sensibles uniquement s'il existe un besoin réel en aval. La meilleure façon de protéger les données privées et sensibles est d'éviter d'ingérer ces données en premier lieu.

Les ingénieurs de données doivent réfléchir aux scénarios d'attaque et de fuite avec tout pipeline de données ou système de stockage qu'ils utilisent. Lorsque vous décidez des stratégies de sécurité, assurez-vous que votre approche offre une sécurité adéquate et pas seulement l'illusion de la sécurité.

**Soyez toujours paranoïaque**

Faites toujours preuve de prudence lorsque quelqu'un vous demande vos informations d'identification. En cas de doute - et vous devriez toujours être dans un doute extrême lorsqu'on vous demande des informations d'identification - attendez et obtenez un deuxième avis de vos collègues et amis.

**Processus**

Lorsque les gens suivent des processus de sécurité réguliers, la sécurité devient une partie du travail. Faites de la sécurité une habitude, pratiquez régulièrement une véritable sécurité, appliquez le principe du moindre privilège et comprenez le modèle de responsabilité partagée dans le cloud.

**Sécurité active**

L*a sécurité active* implique de réfléchir et de rechercher les menaces de sécurité dans un monde dynamique et changeant. Plutôt que de simplement déployer des attaques de phishing simulées planifiées, vous pouvez adopter une posture de sécurité active en recherchant des attaques de phishing réussies et en réfléchissant aux vulnérabilités de sécurité de votre organisation.

Plutôt que d'adopter simplement une liste de contrôle de conformité standard, vous pouvez penser aux vulnérabilités internes spécifiques à votre organisation et aux incitations que les employés pourraient avoir à divulguer ou à utiliser à mauvais escient des informations privées.

**Le principe du moindre privilège**

*Le principe du moindre privilège* signifie qu'une personne ou un système ne doit recevoir que les privilèges et les données dont il a besoin pour accomplir la tâche à accomplir et rien de plus.

Fournissez à l'utilisateur (ou au groupe auquel il appartient) les rôles IAM dont il a besoin quand il en a besoin. Lorsque ces rôles ne sont plus nécessaires, supprimez-les. La même règle s'applique aux comptes de service.

Pour les clients, assurez-vous que c'est le cas. Mettre en œuvre des contrôles d'accès au niveau des colonnes, des lignes et des cellules autour des données sensibles ; pensez à masquer les PII et autres données sensibles et créez des vues qui contiennent uniquement les informations auxquelles le spectateur a besoin d'accéder.

**Responsabilité partagée dans le cloud**

Le fournisseur de cloud est chargé d'assurer la sécurité physique de son centre de données et de son matériel. Dans le même temps, vous êtes responsable de la sécurité des applications et des systèmes que vous créez et gérez dans le cloud. La plupart des failles de sécurité dans le cloud continuent d'être causées par les utilisateurs finaux, et non par le cloud. Les violations se produisent en raison de mauvaises configurations involontaires, d'erreurs, d'oublis et de négligences.

**Sauvegardez toujours vos données**

Les données disparaissent :

- C'est un disque dur ou un serveur mort.
- Quelqu'un peut accidentellement supprimer une base de données ou un bucket de stockage d'objets.
- Un mauvais acteur peut également verrouiller des données. Les attaques de ransomwares sont très répandues de nos jours.

Vous devez sauvegarder vos données régulièrement, à la fois pour la reprise après sinistre et la continuité des opérations commerciales, si une version de vos données est compromise par une attaque de ransomware. De plus, testez régulièrement la restauration de vos sauvegardes de données.

**Patch et de mises à jour**

Les Logiciels deviennent obsolètes et des vulnérabilités de sécurité sont constamment découvertes. Pour éviter d'exposer une faille de sécurité dans une ancienne version des outils que vous utilisez, corrigez et mettez toujours à jour les systèmes d'exploitation et les logiciels au fur et à mesure que de nouvelles mises à jour sont disponibles. Pour mettre à jour votre propre code et vos dépendances, automatisez les builds ou définissez des alertes sur les versions et les vulnérabilités afin que vous puissiez être invité à effectuer les mises à jour manuellement.

**Chiffrement**

Le chiffrement est un procédé qui permet de protéger l'intégrité et la confidentialité de l'information en la rendant illisible pour toute personne qui n'a pas la clé de déchiffrement.

**Chiffrement at rest**

Assurez-vous que vos données sont chiffrées lorsqu'elles sont au repos (sur un périphérique de stockage). Les ordinateurs portables de votre entreprise doivent avoir un chiffrement intégral du disque activé pour protéger les données en cas de vol d'un appareil.

Implémentez le chiffrement côté serveur pour toutes les données stockées dans les serveurs, les systèmes de fichiers, les bases de données et le stockage d'objets dans le cloud.

Toutes les sauvegardes de données à des fins d'archivage doivent également être cryptées. Enfin, intégrez le chiffrement au niveau de l'application, le cas échéant.

**Chiffrement sur le fil**

Chiffrement sur le fil est maintenant la valeur par défaut pour les protocoles actuels. Par exemple, HTTPS est généralement requis pour les API cloud modernes.

Les ingénieurs de données doivent toujours être conscients de la façon dont les clés sont manipulées ; la mauvaise gestion des clés est une source importante de fuites de données.

De plus, HTTPS ne fait rien pour protéger les données si les autorisations de compartiment sont laissées ouvertes au public, une autre cause de plusieurs scandales de données au cours de la dernière décennie.

**Logging, Monitoring, et Alerting**

En tant qu'ingénieur de données, vous devez configurer une surveillance, une journalisation et des alertes automatisées pour être au courant des événements particuliers lorsqu'ils se produisent dans vos systèmes. Si possible, configurez la détection automatique des anomalies.

*Accès*

Qui accède à quoi, quand et d'où ? Quels nouveaux accès ont été accordés ? Y a-t-il des schémas étranges chez vos utilisateurs actuels qui pourraient indiquer que leur compte est compromis, comme essayer d'accéder à des systèmes auxquels ils n'ont pas accès

habituellement ou auxquels ils ne devraient pas avoir accès ? Voyez-vous de nouveaux utilisateurs non reconnus accéder à votre système ? Assurez-vous de passer régulièrement au peigne fin les journaux d'accès, les utilisateurs et leurs rôles pour vous assurer que tout semble OK.

*Ressources*

Surveiller votre disque, CPU, mémoire et E/S pour des modèles qui paraissent hors de l'ordinaire. Vos ressources ont-elles subitement changé ? Si c'était le cas, cela pourrait indiquer une faille de sécurité.

*Facturation*

Surtout avec les services SaaS et gérés dans le cloud, vous devez contrôler les coûts. Configurez des alertes budgétaires pour vous assurer que vos dépenses sont conformes aux attentes. Si un pic inattendu se produit dans votre facturation, cela peut indiquer que quelqu'un ou quelque chose utilise vos ressources à des fins malveillantes.

*Autorisations excessives*

De plus en plus, les vendeurs fournissent des outils qui surveillent les autorisations qui ne sont *pas utilisées* par un utilisateur ou un compte de service pendant un certain temps. Ces outils peuvent souvent être configurés pour alerter automatiquement un administrateur ou supprimer des autorisations après un délai spécifié.

Mettre en place un tableau de bord pour tous les membres de l'équipe des données afin de visualiser la surveillance et de recevoir des alertes lorsque quelque chose semble hors de l'ordinaire. Associez cela à un plan de réponse aux incidents efficace pour gérer les failles de sécurité lorsqu'elles se produisent, et parcourez le plan régulièrement pour être prêt.
