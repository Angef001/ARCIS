# ARCIS — Analysis of Risk & Capital, Integrated System
### Système Intégré d'Analyse du Risque et du Capital

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.x-FF4B4B?logo=streamlit&logoColor=white)
![Status](https://img.shields.io/badge/Status-En%20développement-orange)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Présentation

**ARCIS** est un outil de gestion et d'analyse de risque **multi-actifs**, conçu pour reproduire les tâches quotidiennes d'un analyste Risk ou d'un Middle Office en banque, assurance ou asset management.

Le projet couvre l'ensemble des classes d'actifs (obligations, actions, ETF, SCPI, Private Equity), des risques (taux, crédit, marché, liquidité, change) et des métriques utilisées en entreprise (DV01, VaR, P&L Explain, stress tests, SCR).

> Évolution de **RiskBonSim**, simulateur obligataire Python, renommé et étendu en outil multi-actifs professionnel.

---

## Fonctionnalités

### Phase 1 — Socle multi-actifs
- Modélisation d'obligations souveraines & corporate (prix, YTM, duration, convexité)
- Classes Action, ETF, SCPI, Private Equity
- Gestion de plusieurs portefeuilles nommés
- Import CSV et saisie manuelle
- Courbe des taux (bootstrap + interpolation)
- Sensibilités : **DV01**, **BPV**, **Beta**, **CS01**, **Delta FX**
- Optimisation **Markowitz** — frontière efficiente

### Phase 2 — Analyse de risque avancée
- **VaR** paramétrique, historique, Monte Carlo
- **Expected Shortfall** (CVaR)
- Matrice de corrélation multi-actifs
- **P&L Explain** — décomposition carry / taux / convexité / spread
- **Stress tests** — chocs parallèles, Bear/Bull Flattening/Steepening
- Scénarios historiques (crise 2008, COVID-19, choc taux 2022)
- Scénarios **IRRBB / EBA**

### Phase 3 — Reporting & Middle Office
- Dashboard de risque daily
- Système d'alertes & limites
- Export **PDF** et **Excel** formatés
- Contrôle de valorisation
- Réconciliation positions

### Phase 4 — Réglementaire & Capital
- **SCR marché** (Solvabilité II) — taux, actions, spread
- Ratio de solvabilité
- **Duration gap** actif-passif (ALM)
- Scénarios GSE
- **Backtesting VaR**

---

## Stack technique

| Composant | Technologie |
|-----------|-------------|
| Interface | Streamlit |
| Calcul numérique | NumPy, SciPy |
| Données | Pandas |
| Optimisation | SciPy (Markowitz) |
| Visualisation | Matplotlib |
| Tests | pytest |
| Versioning | Git / GitHub |

---

## Installation

```bash
# Cloner le repo
git clone https://github.com/Angef001/ARCIS.git
cd ARCIS

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

# Installer les dépendances
pip install -r requirements.txt

# Lancer l'application
streamlit run app.py
```

---

## Structure du projet

```
ARCIS/
├── src/
│   ├── instruments/      # Classes financières (Obligation, Action, ETF, SCPI, PE)
│   ├── portfolio/        # Gestion multi-portefeuilles + Markowitz
│   ├── market/           # Courbe des taux + data loader
│   ├── risk/             # VaR, sensibilités, P&L Explain, stress tests
│   ├── regulatory/       # SCR, IRRBB, ALM
│   ├── reporting/        # Dashboard MO, exports PDF/Excel
│   └── ui/               # Interface Streamlit (pages)
├── data/                 # Données de marché & portefeuilles exemples
├── tests/                # Tests unitaires
├── app.py                # Point d'entrée Streamlit
├── STRUCTURE.md          # Arborescence technique détaillée
└── requirements.txt
```

---

## Roadmap

| Phase | Statut | Modules |
|-------|--------|---------|
| P1 — Socle multi-actifs | 🔄 En cours | 11 modules |
| P2 — Analyse de risque avancée | ⏳ À venir | 15 modules |
| P3 — Reporting & Middle Office | ⏳ À venir | 9 modules |
| P4 — Réglementaire & Capital | ⏳ À venir | 9 modules |

**Total : 44 modules**

---

## Contexte

Projet personnel développé en parallèle d'un M2 Finance parcours **Gestion des Instruments Financiers** (CY Cergy Paris Université) et d'une alternance en finance de marché.

L'objectif est de construire un outil qui reflète les tâches concrètes d'un analyste **Risk** ou **Middle Office** — pas un exercice académique, mais une réponse directe aux compétences attendues sur les postes ciblés (risque de marché, contrôle MO, ALM, risques financiers en assurance).

---

## Auteur

**Ange Fogoum**
Étudiant ingénieur-finance — ESIGELEC / M2 GIF CY Cergy Paris Université

📧 kamgar916@gmail.com
📱 07 52 54 46 24
🔗 [GitHub](https://github.com/Angef001)
