# Note de cadrage — Scoring IA de risque d'attrition pour comptes Pro/PME

Exercice de cadrage de projet : produire le document qu'un Chargé de Projet Data/IA rédigerait avant le lancement d'un projet, pour aligner sponsor métier, équipe technique et parties prenantes sur le périmètre, les jalons et les risques avant d'écrire une ligne de code. Projet fictif, construit pour être réaliste dans sa structure et ses contraintes — pas un vrai projet en cours.

## 1. Contexte et problème métier

Une direction commerciale B2B gérant un portefeuille de comptes Pro/PME constate une perte de clients (churn) qu'elle ne détecte aujourd'hui qu'*a posteriori* — au moment de la résiliation ou du non-renouvellement. Les chargés de compte n'ont pas de signal précoce leur permettant de prioriser leurs actions de rétention sur les comptes les plus à risque et les plus rentables à sauver.

**Constat chiffré (hypothèse de cadrage)** : sur un portefeuille de 5 000 comptes Pro/PME, un taux de churn annuel de 12 % représente ~600 comptes perdus/an. Une détection précoce sur seulement 20 % des cas à plus haut risque, avec une action de rétention efficace à 30 %, représenterait un gain estimé de 36 comptes retenus/an — à valoriser avec le panier moyen réel une fois le projet lancé.

## 2. Objectifs

| # | Objectif | Mesurable |
|---|---|---|
| O1 | Détecter les comptes à risque de churn avant résiliation | Score de risque disponible ≥ 60 jours avant la date de fin de contrat |
| O2 | Prioriser l'effort commercial de rétention | Top 20 % des comptes par score = 50 %+ des churns réels capturés (rappel) |
| O3 | Outiller les chargés de compte sans changer leur outil quotidien | Score intégré au CRM existant, pas de nouvel outil à apprendre |

**Non-objectif explicite** : ce projet ne vise pas à automatiser la décision de rétention (offre, remise) — seulement à prioriser l'attention humaine. La décision reste au chargé de compte.

## 3. Périmètre

**Dans le périmètre :**
- Modèle de scoring sur les comptes Pro/PME existants (hors prospects)
- Historique de facturation, usage produit, interactions support/commercial comme features
- Restitution du score dans le CRM (champ ou widget)

**Hors périmètre (v1) :**
- Comptes Grand Compte (dynamique de churn différente, déjà suivis individuellement)
- Recommandation automatique d'action de rétention (v2 potentielle)
- Nouveaux clients avec moins de 6 mois d'historique (signal insuffisant)

## 4. Parties prenantes

| Rôle | Responsabilité |
|---|---|
| Sponsor (Direction Commerciale) | Priorités business, arbitrages, budget |
| Chargé de Projet Data | Cadrage, coordination, suivi des jalons, restitution |
| Data Scientist / Analyst | Modélisation, validation statistique |
| Data Engineer | Pipeline de données, intégration CRM |
| Chargés de compte (utilisateurs finaux) | Retours d'usage, validation terrain du score |
| DPO / Conformité | Validation du traitement de données clients (RGPD) |

## 5. Livrables

1. Note de cadrage (ce document)
2. Jeu de données consolidé et documenté (dictionnaire de données)
3. Modèle de scoring versionné, avec rapport de performance
4. Intégration du score au CRM (champ + fréquence de rafraîchissement)
5. Guide d'usage pour les chargés de compte
6. Bilan à 3 mois post-lancement (le score capture-t-il vraiment les churns ?)

## 6. Jalons et planning indicatif

| Jalon | Semaine | Livrable associé |
|---|---|---|
| Cadrage validé | S0 | Ce document, signé sponsor |
| Données consolidées et qualifiées | S1-S3 | Dictionnaire de données, audit qualité |
| Premier modèle (baseline) | S4-S6 | Modèle simple, performance de référence |
| Modèle itéré + validation métier | S7-S9 | Revue avec chargés de compte sur échantillon |
| Intégration CRM | S10-S12 | Score visible en production |
| Bilan à 3 mois | S24 | Rapport d'impact réel |

## 7. Risques et mitigation

| Risque | Probabilité | Impact | Mitigation |
|---|---|---|---|
| Historique de données insuffisant/mal qualifié | Élevée | Élevé | Audit qualité dès S1, avant tout travail de modélisation |
| Le churn a des causes non captées dans les données (ex : décision prix hors système) | Moyenne | Élevé | Interviews qualitatives des chargés de compte en amont |
| Adoption faible du score par les équipes terrain | Moyenne | Élevé | Impliquer 2-3 chargés de compte dès le cadrage, pas juste à la livraison |
| Dérive du modèle dans le temps (comportement clients qui change) | Moyenne | Moyen | Suivi mensuel de la performance, seuil de réentraînement défini |
| Question de conformité RGPD sur les données utilisées | Faible | Élevé | Validation DPO avant collecte, pas après |

## 8. Indicateurs de succès

- **Indicateur de pilotage projet** : respect des jalons (± 1 semaine)
- **Indicateur de performance modèle** : rappel ≥ 50 % sur le top 20 % des comptes scorés à risque (voir O2)
- **Indicateur d'adoption** : % de chargés de compte consultant le score avant un point client à risque, mesuré à 3 mois
- **Indicateur d'impact business** : nombre de comptes à risque identifié où une action a été engagée avant résiliation, comparé au bilan à 3 mois

## 9. Hypothèses et dépendances

- Le CRM expose une API ou un moyen d'intégration pour afficher un champ calculé — à vérifier avec l'équipe technique CRM avant S10.
- Un historique d'au moins 18-24 mois de données comptes est disponible et exploitable.
- Un sponsor métier est disponible pour arbitrer en cas de tension entre performance du modèle et délai.

---

*Document produit dans le cadre d'un exercice personnel de mise en pratique des compétences de cadrage de projet Data/IA — voir les autres projets du portfolio pour la partie exécution technique (analyse de données, scoring, automatisation).*

## Auteur

Alvin Kouadio
