# TP1 — Cadrage du projet
**Équipe G9 :** Wajd Maatoug, Aicha Kribi, Dous Kinza
**Sujet 19 — Huilerie : planification des livraisons d'olives**

**Repères pour les sources.** Phrases de la demande du client :
- **P1** « Pendant la saison, les agriculteurs attendent des heures devant notre huilerie avant de livrer leurs olives. »
- **P2** « Nous voulons une application pour organiser les livraisons. »
- **P3** « Les agriculteurs doivent pouvoir réserver leur passage pour apporter leurs olives. »
- **P4** « Le maître moulinier doit gérer la capacité du moulin, l'agent de pesée enregistre ce qui arrive, et le gérant veut suivre la saison. »
- **P5** « Il ne faut pas accepter plus d'olives que ce que le moulin peut traiter. »
- **P6** « Nos agriculteurs sous contrat doivent être avantagés. »
- **P7** « Certains réservent beaucoup plus qu'ils n'apportent et prennent la place des autres : il faut les dissuader. »
- **P8** « Le maître moulinier ne veut pas de gros lots, car il faut nettoyer la chaîne entre deux agriculteurs. »
- **P9** « L'agent de pesée voudrait que les petits agriculteurs puissent apporter quelques sacs. »
- **P10** « Les agriculteurs doivent être informés rapidement. »
- **Contexte** : huilerie familiale, un moulin, un maître moulinier, un agent de pesée, un gérant, environ 400 agriculteurs inscrits.

---

## 1. Vision

### Q1 — Problème métier
Pendant la saison, les arrivées d'olives ne sont pas régulées : les agriculteurs attendent des heures, la capacité du moulin n'est pas maîtrisée et certains agriculteurs occupent des places au détriment des autres.

Phrase qui décrit déjà une solution : **P2** « Nous voulons une application pour organiser les livraisons ». « Créer une application » est une solution possible, pas le problème.

### Q2 — Parties prenantes

**Citées explicitement dans la demande**

| Partie prenante | Intérêt / attente |
| --- | --- |
| Agriculteurs (environ 400) | Réserver leur passage, ne plus attendre des heures, être informés rapidement. |
| Agriculteurs sous contrat | Être avantagés (la forme de l'avantage reste à préciser). |
| Petits agriculteurs | Pouvoir apporter quelques sacs. |
| Maître moulinier | Gérer la capacité du moulin, éviter les gros lots. |
| Agent de pesée | Enregistrer ce qui arrive ; permettre l'accès aux petits agriculteurs. |
| Gérant | Suivre la saison. |

**Non citées mais concernées ou impactées**

| Partie prenante | Intérêt / attente |
| --- | --- |
| Famille propriétaire de l'huilerie | Bon fonctionnement et rentabilité de la saison (à confirmer). |
| Personne chargée de l'informatique / maintenance | Exploiter et maintenir l'application, si elle existe (à confirmer). |
| Agriculteurs non sous contrat | Impactés par la priorité donnée aux agriculteurs sous contrat. |

Aucune de ces parties prenantes non citées n'est un utilisateur confirmé du système.

### Q3 — Objectifs

- **OBJ-01** — Réduire le temps d'attente moyen d'un agriculteur avant de livrer ses olives de **[à valider]** à **[à valider]** d'ici **[à valider]**.
- **OBJ-02** — Réduire l'écart entre les quantités réservées et les quantités réellement apportées de **[à valider]** à **[à valider]** d'ici **[à valider]**.

Aucune valeur n'est inventée : ce sont des valeurs à demander au client.

### Q4 — Objectif le plus difficile à mesurer
« Informer rapidement » (P10) est le plus difficile à mesurer, car « rapidement » est subjectif. Il faut définir un indicateur (délai entre un événement et la réception de l'information par l'agriculteur, proportion d'agriculteurs informés dans ce délai) puis fixer la valeur cible avec le client. « Avantager » les agriculteurs sous contrat (P6) pose un problème voisin.

---

## 2. Périmètre

### Q5 — Tableau connu / inconnu

| Élément | Catégorie | Source ou « à valider » |
| --- | --- | --- |
| Réservation d'un passage par l'agriculteur | Dans le périmètre | P3 |
| Gestion de la capacité du moulin par le maître moulinier | Dans le périmètre | P4 (unité et période de la capacité à valider) |
| Enregistrement des olives apportées par l'agent de pesée | Dans le périmètre | P4 |
| Suivi de la saison par le gérant | Dans le périmètre | P4 (« suivre » à préciser) |
| Ne pas accepter plus d'olives que la capacité du moulin | Contrainte | P5 |
| Avantager les agriculteurs sous contrat | Contrainte | P6 (forme de l'avantage à valider) |
| Dissuader les réservations excessives | Contrainte | P7 (moyen de dissuasion à valider) |
| Éviter les gros lots / permettre les petits apports | Contrainte | P8, P9 (seuils à valider) |
| Informer rapidement les agriculteurs | Contrainte | P10 (canal et délai à valider) |
| Chaque agriculteur possède un compte ou un identifiant | Hypothèse | À valider |
| Les agriculteurs disposent d'un smartphone et d'internet | Hypothèse | À valider |
| Authentification obligatoire pour réserver | Point ouvert | À valider |
| Un agriculteur peut annuler ou modifier sa réservation | Point ouvert | À valider |
| Gestion des retards et des absences | Point ouvert | À valider |
| Canal d'information (SMS, WhatsApp, e-mail, appel) | Point ouvert | À valider |
| Qui définit le statut « sous contrat » et comment ? | Point ouvert | À valider |

Chaque hypothèse apparaît aussi comme point ouvert : « possède un compte » → authentification ; « smartphone et internet » → canal d'information.

### Q6 — Hors périmètre
Le suivi de la production d'huile après la pesée (transformation, stock, qualité) est placé **hors périmètre** : la demande porte uniquement sur l'organisation des livraisons (**P2** « organiser les livraisons »).

Le paiement et la facturation ne peuvent pas être déclarés hors périmètre avec certitude : aucune phrase ne les mentionne, nous les classons en **point ouvert**.

---

## 3. Exigences

### Q7 — Tableau des exigences

| ID | Exigence | Type (F / NF) | Source |
| --- | --- | --- | --- |
| REQ-F-01 | Le système doit permettre à un agriculteur de réserver un créneau de passage. | F | P3 |
| REQ-F-02 | Le système doit permettre au maître moulinier de définir la capacité du moulin. | F | P4 |
| REQ-F-03 | Le système doit permettre à l'agent de pesée d'enregistrer la quantité d'olives apportée. | F | P4 |
| REQ-F-04 | Le système doit refuser une réservation qui ferait dépasser la capacité du moulin. | F | P5 |
| REQ-F-05 | Le système doit informer les agriculteurs de l'état de leur réservation. | F | P10 |
| REQ-NF-01 | Le système doit informer les agriculteurs rapidement. | NF | P10 |

Remarques : REQ-F-02 et REQ-F-04 sont acceptables mais la capacité (unité, période) est à définir. REQ-NF-01 est un besoin initial non vérifiable en l'état (voir Q9). Le suivi de la saison par le gérant n'est pas transformé en exigence tant que « suivre » n'est pas défini (point ouvert).

### Q8 — Critique de REQ-F-06 et REQ-NF-02 d'une autre équipe

**REQ-F-06 — « Le système doit avantager les agriculteurs sous contrat. »**
- *Problème :* « avantager » est ambigu (priorité sur les créneaux ? créneaux réservés ? quota plus élevé ? ouverture anticipée ?). Écrire une règle précise serait inventer.
- *Version corrigée :* ne pas en faire une exigence finale. Point ouvert : « En quoi consiste concrètement l'avantage des agriculteurs sous contrat ? »

**REQ-NF-02 — « L'application doit permettre aux agriculteurs de réserver depuis un smartphone et de recevoir un SMS de confirmation. »**
- *Problèmes :* ne commence pas par « Le système doit… » ; contient plusieurs idées (réserver, recevoir un SMS) ; « smartphone » et « SMS » ne sont pas dans la demande (équipement et canal inventés).
- *Version corrigée :* REQ-F-05 « Le système doit informer les agriculteurs de l'état de leur réservation », plus les points ouverts « Quel canal d'information ? » et « Quel équipement (smartphone, ordinateur, autre) ont les agriculteurs ? ».

### Q9 — « Informer rapidement » : pourquoi ce n'est pas vérifiable
« Rapidement » est subjectif, non quantifié et sans indicateur de mesure. Questions au client, sans inventer de valeur cible :
- Quel délai maximal est acceptable entre un événement (confirmation, annulation, changement de créneau) et l'information de l'agriculteur ?
- Quels événements doivent déclencher une information ?
- Par quel canal les agriculteurs veulent-ils être informés ?

---

## 4. Analyse IA

Prompt utilisé, adapté au sujet N19, **après** notre analyse (parties 1 à 3) : « Analyse cette demande client pour un système de planification des livraisons d'olives dans une huilerie. Identifie les ambiguïtés, les informations manquantes et les questions qui devraient être posées au client. N'invente pas de nouvelles exigences. »

Propositions obtenues :
1. Définir précisément ce qu'est un « gros lot » et un « petit agriculteur » (seuils en kg ou en sacs).
2. Préciser la capacité du moulin : unité (kg/h, kg/jour), horaires, période de saison.
3. Préciser l'avantage des agriculteurs sous contrat (priorité, créneaux réservés, quotas).
4. Préciser « dissuader » : pénalité, limite de réservations, blocage temporaire.
5. Résoudre la tension entre « pas de gros lots » (maître moulinier) et « petits agriculteurs acceptés » (agent de pesée).
6. Authentification : comment identifier un agriculteur ? Faut-il un compte ?
7. Annulation, modification, retards et absences d'une réservation.
8. Envoyer des notifications SMS et WhatsApp automatiques, avec rappel 24 h avant le créneau.
9. Développer une application mobile native iOS et Android pour les agriculteurs.
10. Ajouter un module de paiement en ligne des frais de pressage.
11. Ajouter un suivi de la qualité de l'huile (acidité) et une traçabilité par lot d'olives.
12. « Informer rapidement » n'est pas mesurable en l'état : définir un délai et un canal avec le client.

### Q10 — Tableau de classement

| Proposition IA | Décision | Justification (preuve dans la demande ?) |
| --- | --- | --- |
| 1. Définir « gros lot » / « petit agriculteur » | Acceptée | Ambiguïté réelle : P8 et P9 utilisent ces notions sans seuil. |
| 2. Préciser la capacité du moulin | Acceptée | P4 et P5 parlent de capacité sans unité ni période. |
| 3. Préciser l'avantage des agriculteurs sous contrat | Acceptée | Ambiguïté directe de P6. |
| 5. Tension gros lots / petits agriculteurs | Acceptée | P8 et P9 expriment deux attentes opposées de deux acteurs. |
| 6. Authentification | À valider | Rien dans la demande ; à poser en point ouvert. |
| 7. Annulation, modification, retards | À valider | Plausible, mais absent de la demande. |
| 8. Notifications SMS/WhatsApp + rappel 24 h | Rejetée comme exigence | Canal et délai inventés. P10 demande seulement d'informer rapidement ; devient une question. |
| 9. Application mobile native | Rejetée | Choix technique non demandé. |
| 10. Paiement en ligne | Rejetée | Aucune phrase ne le mentionne. |
| 11. Qualité d'huile et traçabilité par lot | Rejetée | Hors du périmètre de la demande (livraisons d'olives). |
| 12. « Informer rapidement » non mesurable | Acceptée | Problème réel, déjà identifié en Q4 et Q9. |

### Q11 — Proposition plausible mais inventée
**Proposition 11 : suivi de la qualité de l'huile et traçabilité par lot.**
- *Pourquoi elle est convaincante :* c'est une fonction courante dans une huilerie, elle semble professionnelle, et elle se greffe naturellement sur l'enregistrement des apports faits par l'agent de pesée.
- *Pourquoi elle est dangereuse si on l'accepte sans vérification :* elle élargit le périmètre au-delà des livraisons, ajoute des données, des règles et des tests (mesures, lots, stock), coûte du temps de développement et n'a jamais été demandée par le client.

*(La proposition 8 sur les notifications avec rappel 24 h est aussi plausible mais inventée : le client demande seulement d'informer rapidement.)*

### Q12 — Ambiguïté relevée par l'IA que nous n'avions pas identifiée
**La tension entre P8 et P9** (proposition 5) : le maître moulinier ne veut pas de gros lots, l'agent de pesée veut que les petits agriculteurs puissent apporter quelques sacs. Nous avions classé ces deux phrases séparément comme règles ; elles expriment en réalité deux attentes différentes de deux acteurs, qu'il faut arbitrer avec le client (quelle règle prime en cas de conflit ?).

*(À confirmer par l'équipe : si vous aviez déjà vu cette tension, remplacez par une autre ambiguïté que vous n'aviez pas relevée.)*
