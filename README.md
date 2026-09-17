# Note de cadrage — Scoring IA de risque d'attrition (exercice)

## En bref
Avant de coder quoi que ce soit sur un projet data, il y a un document qui force à répondre à trois questions : pourquoi on fait ça, jusqu'où, et qu'est-ce qui peut mal tourner. Je me suis entraîné à cet exercice sur un cas fictif (aucune vraie entreprise derrière), pour apprendre la méthode de cadrage d'un projet data avant de foncer dans la technique.

## 1. Contexte et problème métier
Une direction commerciale B2B gérant un portefeuille de comptes Pro/PME constate une perte de clients (churn) qu'elle ne détecte qu'après coup — au moment de la résiliation. Les chargés de compte n'ont pas de signal pour prioriser leurs actions de rétention.

**Hypothèse de cadrage (chiffres fictifs, pour illustrer le raisonnement)** : sur un portefeuille de 5 000 comptes, un taux de churn de 12 % représente ~600 comptes perdus par an. Détecter 20 % des cas à risque avec une rétention efficace à 30 % donnerait un gain estimé de 36 comptes retenus par an.

## 2. Objectifs
| # | Objectif | Mesurable |
|---|---|---|
| O1 | Détecter les comptes à risque avant résiliation | Score disponible ≥ 60 jours avant la fin de contrat |
| O2 | Prioriser l'effort commercial | Top 20 % des comptes = 50 %+ des churns réels capturés |
| O3 | Rester simple à utiliser | Score intégré au CRM existant, pas de nouvel outil |

**Ce que ce projet ne fait pas** : automatiser la décision de rétention — seulement aider à prioriser l'attention humaine.

## 3. Périmètre
Dans le périmètre : comptes Pro/PME existants, historique de facturation et d'usage, restitution dans le CRM.
Hors périmètre : Grands Comptes (dynamique différente), recommandation automatique d'action, nouveaux clients avec peu d'historique.

## 4. Parties prenantes
| Rôle | Responsabilité |
|---|---|
| Sponsor (Direction Commerciale) | Priorités, arbitrages, budget |
| Chargé de Projet Data | Cadrage, coordination, suivi |
| Data Scientist / Analyst | Modélisation |
| Chargés de compte | Retours terrain |
| DPO / Conformité | Validation RGPD du traitement des données clients |

## 5. Jalons indicatifs
| Jalon | Semaine |
|---|---|
| Cadrage validé | S0 |
| Données consolidées | S1-S3 |
| Premier modèle | S4-S6 |
| Validation métier | S7-S9 |
| Intégration CRM | S10-S12 |
| Bilan à 3 mois | S24 |

## 6. Principaux risques
| Risque | Mitigation |
|---|---|
| Données insuffisantes ou mal qualifiées | Audit qualité avant tout travail de modélisation |
| Adoption faible par les équipes terrain | Impliquer des chargés de compte dès le cadrage |
| Question de conformité RGPD | Validation DPO avant collecte |

## Ce que j'en retiens
Le plus dur a été la partie risques : c'est facile de lister des évidences ("manque de budget"). J'ai essayé de trouver des risques spécifiques à ce projet précis, avec une mitigation concrète en face plutôt qu'un mot vague.

Alvin Kouadio
