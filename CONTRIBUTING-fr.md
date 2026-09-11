# Guide de contribution, Grist Gouv Widgets

Merci de vous intéresser à la contribution au projet Grist Gouv ! C'est grâce à des personnes comme vous que l'écosystème de widgets disponibles pour les agents publics peut grandir et s'améliorer.

Ce guide s'applique spécifiquement aux **widgets personnalisés** développés pour [Grist Gouv](https://grist.numerique.gouv.fr), le déploiement souverain de Grist au sein de la Suite interministérielle. Pour toute contribution portant sur le cœur de l'application (fonctionnalités, bugs, traductions…), nous vous invitons à vous rendre directement sur [grist-core](https://github.com/gristlabs/grist-core).

Lire ce guide avant de soumettre une contribution, c'est respecter le temps de l'équipe qui maintient le projet, et en retour, nous ferons tout notre possible pour être raisonnablement réactifs et vous accompagner si votre widget a l'air prometteur.

---

## Types de contributions recherchées

Nous accueillons ces contributions :

- **Des widgets** : composants personnalisés qui étendent les fonctionnalités de Grist dans un contexte de service public.
- **Des tutoriels vidéo courts** : démonstrations de l'utilisation d'un widget existant ou d'un cas d'usage Grist Gouv.

Pour tout le reste (bugs dans l'application, nouvelles fonctionnalités natives, traductions de l'interface…), merci de contribuer directement à [grist-core](https://github.com/gristlabs/grist-core).

### Ce que nous ne cherchons pas comme contributions 

- Des widgets qui reproduisent des fonctionnalités déjà couvertes nativement par Grist.
- Du code généré intégralement par un outil d'IA sans relecture ni compréhension humaine de ce qui a été produit (voir la section [Qualité du code](#qualité-du-code)).
- Des contributions hors périmètre : bugs applicatifs, demandes d'évolution du moteur Grist, questions de support utilisateur.

---

## Règles de base

En contribuant à ce projet, vous vous engagez à :

- Traiter les autres contributeurs et l'équipe avec respect et bienveillance.
- Documenter votre widget de façon suffisante pour qu'une autre personne puisse le comprendre, le maintenir et l'améliorer sans vous.
- Signaler les failles de sécurité par les canaux appropriés (voir [Signaler une faille de sécurité](#signaler-une-faille-de-sécurité)), et ne jamais les divulguer publiquement avant qu'elles soient corrigées.
- Être réactif si l'équipe demande des modifications après review : sans réponse sous 2 semaines, nous clôturerons la soumission.

---

## Première contribution

Tu n'as jamais contribué à un projet open source ? Pas de panique, tout le monde commence quelque part. Voici quelques ressources (en anglais) pour vous aider à démarrer :

- [How to Contribute to an Open Source Project on GitHub](https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github), série vidéo gratuite
- [firsttimersonly.com](http://www.firsttimersonly.com/)

Pour trouver des points d'entrée accessibles dans l'écosystème Grist plus largement, vous pouvez consulter les issues taguées [`good first issue`](https://github.com/gristlabs/grist-core/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22good+first+issue%22) sur grist-core.

---

## Comment soumettre un widget

Il existe deux façons pour votre widget de rejoindre l'écosystème Grist Gouv. Comprendre quel chemin vous correspond vous aidera à savoir quoi préparer.

### Chemin A, On découvre votre widget et on le forke

Si l'équipe Grist Gouv tombe sur un widget que vous avez publié publiquement et le juge pertinent, nous pouvons le forker dans notre organisation et l'intégrer, sans aucune action de votre part.

Cela dit, plus votre widget respecte déjà les critères de qualité décrits à l'étape 2 ci-dessous, plus nous serons en mesure de le forker, le merger ou l'héberger sur notre instance pour tous les agents publics. Ces critères sont une façon de rendre votre widget « fork-ready ».

### Chemin B, Vous voulez que votre widget soit hébergé sur l'instance DINUM ou ANCT

Si votre objectif est de rendre votre widget disponible à tous les utilisateurs des instances officielles Grist Gouv, vous devez suivre les quatre étapes ci-dessous. Ce chemin requiert de respecter tous les critères de qualité, et l'équipe réalisera un audit de sécurité avant tout déploiement en production.

---

> ⚠️ **Note sur les contributions générées par IA**
>
> Les issues, pull requests et le code de widgets ne doivent pas être du contenu IA brut, non relu. Vous devez avoir lu, pleinement compris, et, pour le code, testé tout ce que vous soumettez. En ouvrant une issue ou une pull request, vous certifiez que vous seriez en mesure d'expliquer et de défendre votre contribution lors de la review, sans vous appuyer sur un assistant IA.
>
> Utiliser des outils IA pour vous aider à écrire ou améliorer du code est tout à fait acceptable. Soumettre du contenu IA que vous n'avez pas rigoureusement relu ne l'est pas.

---

### Étape 1, Créez votre propre dépôt

Publiez votre widget dans un dépôt public à votre nom (ou celui de votre organisation), sur GitHub ou une autre forge publique. Il n'est pas nécessaire d'ouvrir une pull request vers notre dépôt : nous forkons les repos que nous jugeons pertinents, plutôt que d'accepter des PRs entrantes.

### Étape 2, Vérifiez les critères de qualité

Avant de nous signaler votre widget, assurez-vous qu'il respecte les points suivants :

**Lisibilité et maintenabilité**
- Le code est lisible par un développeur humain sans avoir recours à un outil IA pour le comprendre.
- Les fonctions et variables ont des noms explicites et descriptifs.
- Un fichier `README.md` accompagne le widget et explique : ce que fait le widget, comment le configurer, les éventuelles dépendances.
- Le widget a un périmètre fonctionnel clairement défini et raisonnablement limité. Un widget qui fait une chose bien est plus facile à relire, tester et maintenir qu'un widget qui essaie de couvrir plusieurs cas d'usage. Si votre widget donne l'impression de faire plusieurs métiers différents, envisagez de réduire son périmétre.

**Tests**
- Les fonctionnalités principales sont couvertes par des **tests unitaires**.
- Des **tests d'intégration** couvrent au moins le scénario de base (création d'un document, interaction avec le widget) pour vérifier qu'une modification ne casse pas l'existant.

> 💡 **Vous n'êtes pas développeur ?** Si vous avez construit votre widget avec l'aide d'un outil IA et que vous n'êtes pas à l'aise pour écrire des tests vous-même, vous pouvez utiliser un prompt structuré pour qu'une IA les génère à votre place, à condition de les relire et de les exécuter avant de soumettre. Des outils comme [playwright-skill](https://github.com/testdino-hq/playwright-skill) proposent une approche structurée de la génération de tests assistée par IA (note : nous n'avons pas encore testé formellement cet outil, considérez-le comme un point de départ plutôt qu'une recommandation officielle). Si vous utilisez un agent IA qui supporte les skills, vous pouvez lui indiquer d'utiliser [playwright-skill](https://github.com/testdino-hq/playwright-skill) pour vous aider à écrire des tests E2E de votre widget, en veillant à adapter le résultat au contexte Grist (accès simulé aux données, contraintes d'iframe). Quel que soit l'outil utilisé, assurez-vous de comprendre ce que les tests vérifient et qu'ils passent effectivement sur votre code.
>
> Si vous exécutez un agent IA en local pour vous aider à développer ou tester votre widget, nous recommandons d'utiliser [agent-vm](https://github.com/sylvinus/agent-vm) pour le faire en sécurité, il exécute l'agent dans un environnement isolé, limitant ce à quoi il peut accéder ou modifier sur votre machine.

**Qualité du code**

> ⚠️ Si vous avez utilisé un outil d'IA (Copilot, ChatGPT, Claude…) pour vous aider à développer votre widget, c'est tout à fait acceptable, à condition que vous soyez en mesure d'expliquer chaque partie du code produit. Un code que vous ne comprenez pas vous-même ne peut pas être maintenu par l'équipe.
>
> Attention à la verbosité. Les outils IA ont tendance à générer du code plus long que nécessaire, et même si vous êtes capable d'expliquer chaque ligne, un code verbeux rend la review significativement plus difficile et plus lente. Avant de soumettre, demandez-vous : est-ce que ça pourrait s'écrire de façon plus concise sans perdre en clarté ? Les reviewers doivent pouvoir lire la logique de votre widget en une fois.
>
> Cela inclut la duplication de code entre widgets. Si vous soumettez un dépôt contenant plusieurs widgets et que certains partagent la même logique (fonctions utilitaires, appels API, helpers UI…), ce code partagé doit vivre dans un module commun, pas être copié-collé dans chaque widget. Le code dupliqué est plus difficile à relire et crée de la dette de maintenance : un bug corrigé à un endroit restera silencieusement présent dans les autres.

### Étape 3, Signale votre widget à l'équipe

Une fois votre dépôt prêt, contactez-nous sur le canal **[Tchap Grist-Contributions](https://www.tchap.gouv.fr/#/room/!kkwhrcxoMcnAGMXMIM:agent.dinum.tchap.gouv.fr)** en partageant :

- Le lien vers votre dépôt
- Une description courte de ce que fait le widget (2-3 phrases)
- Le contexte d'usage : pour quel type d'administration, quel cas métier ?

### Étape 4, Review et décision

L'équipe Grist Gouv examine votre soumission. Nous nous engageons à vous donner un premier retour **sous 1 mois** : validation, demande de modifications, ou refus motivé. Dans la mesure du possible, nous essayons de répondre plus vite.

Si le widget est retenu pour un hébergement sur l'instance DINUM ou ANCT, une vérification complémentaire de sécurité sera réalisée par l'équipe technique avant mise en production.

---

## Qualité du code

Il n'existe pas à ce jour de linter ou de formateur imposé pour les widgets Grist Gouv. En revanche, nous attendons que le code soit :

- **Compréhensible** : une personne qui ne l'a pas écrit doit pouvoir le lire et comprendre son fonctionnement.
- **Minimal** : pas de dépendances superflues, pas de code mort.
- **Sûr** : pas de requêtes vers des services externes non documentés, pas de stockage de données utilisateur en dehors de Grist.

---

## Signaler une faille de sécurité

**Ne créez pas d'issue publique pour signaler une faille de sécurité.**

Si vous découvrez une vulnérabilité dans un widget hébergé sur l'instance Grist Gouv ou dans l'infrastructure elle-même, utilisez l'un de ces canaux :

- **VDP (Vulnerability Disclosure Policy) de l'État** : [https://vdp.numerique.gouv.fr/p/Policy](https://vdp.numerique.gouv.fr/p/Policy)
  - Pour soumettre un signalement : [https://vdp.numerique.gouv.fr/p/Send-a-report](https://vdp.numerique.gouv.fr/p/Send-a-report)
- **Contact direct** : contactez l'équipe Grist.Gouv en message privé via Tchap

Pour vous aider à évaluer si vous êtes face à une faille de sécurité, posez-vous ces questions :
- Est-ce que cela me permettrait d'accéder à des données qui ne m'appartiennent pas ?
- Est-ce que cela pourrait désactiver ou perturber le service pour d'autres utilisateurs ?

Si vous répondez « oui » à l'une de ces questions, traitez le problème comme une faille de sécurité.

---

## Signaler un bug (hors sécurité)

Pour les bugs non liés à la sécurité, contactez-nous sur le [forum Grist](https://forum.grist.libre.sh) ou sur le canal Tchap Grist-Contributions, en précisant :

1. Le nom et la version du widget concerné
2. Ce que vous avez fait
3. Ce que vous vous attendiez à voir
4. Ce que vous avez vu à la place
5. Si possible : un exemple de document Grist qui reproduit le bug

> Pour les bugs sur l'application Grist elle-même (et non sur un widget), merci de les signaler directement sur [grist-core](https://github.com/gristlabs/grist-core/issues).

---

## Suggérer une amélioration ou un nouveau widget

L'objectif de Grist Gouv est de proposer des outils utiles aux agents publics, adaptés aux contraintes de la sphère publique française (interopérabilité, souveraineté, accessibilité). Avant de vous lancer dans un développement, vérifiez qu'un widget similaire n'existe pas déjà dans le [catalogue des widgets](https://support.getgrist.com/widget-custom/).

Pour proposer une idée de widget ou une amélioration :

1. Ouvrez une discussion sur le [forum Grist](https://forum.grist.libre.sh) en décrivant le besoin métier, pas seulement la solution technique.
2. Précisez si vous êtes prêt à développer vous-même ou si vous cherchez quelqu'un pour le faire.
3. L'équipe ou la communauté pourra réagir, affiner le besoin, et indiquer si c'est dans le périmètre du projet.

---

## Processus de revue

Les soumissions de widgets sont examinées par au moins un développeur de l'équipe Grist.Gouv. La responsabilité finale de validation revient à :

- **Grégoire Cutzach** (DINUM / LaSuite)
- **Pierre Colle** (ANCT)

La review porte sur trois aspects :
- **Pertinence** : le widget répond-il à un vrai besoin de service public ?
- **Qualité technique** : le code est-il lisible, testé, maintenable ?
- **Sécurité** : le widget présente-t-il des risques pour les données ou l'infrastructure ?

Nous nous engageons à vous donner un retour **sous 1 mois**. Si des modifications sont demandées et qu'il n'y a aucun retour de votre part sous 2 semaines, nous pourrons clôturer la soumission, vous pourrez bien sûr la rouvrir ultérieurement.

---

## Communauté

Pour poser des questions, partager votre avancement ou discuter avec d'autres contributeurs :

- **Forum** : [https://forum.grist.libre.sh](https://forum.grist.libre.sh), pour les échanges structurés, les retours d'expérience et les discussions de fond
- **Canal Tchap Grist-Contributions** : [https://www.tchap.gouv.fr/#/room/!kkwhrcxoMcnAGMXMIM:agent.dinum.tchap.gouv.fr](https://www.tchap.gouv.fr/#/room/!kkwhrcxoMcnAGMXMIM:agent.dinum.tchap.gouv.fr), pour les échanges rapides et le suivi de soumission

---

## Conventions (code, commits, issues)

Il n'existe pas à ce jour de convention formelle imposée pour les commits ou le nommage des issues dans ce projet. Nous te recommandons néanmoins :

- D'utiliser des messages de commit clairs en français ou en anglais, décrivant ce qui a changé et pourquoi.
- De nommer votre dépôt de façon explicite : `grist-widget-[nom-fonctionnel]` est un bon format.

Ces conventions pourront évoluer à mesure que la communauté de contributeurs grandira.

---

*Ce guide est maintenu par l'équipe Grist Gouv (DINUM / ANCT). Dernière mise à jour : Septembre 2026.*
