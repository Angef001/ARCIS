# ARCIS — Arborescence technique

**Analysis of Risk & Capital, Integrated System**
*Système Intégré d'Analyse du Risque et du Capital*

---

## Légende

- `[existant]` — fichier déjà présent dans RiskBonSim, à migrer
- `[P1]` à `[P4]` — phase de développement cible

---

## Structure complète

```
ARCIS/
│
├── src/
│   │
│   ├── instruments/                        # Classes financières
│   │   ├── base.py                         # Classe abstraite Instrument            [P1]
│   │   ├── obligation.py                   # Obligations souveraines & corporate    [existant][P1]
│   │   ├── action.py                       # Actions cotées & indices               [P1]
│   │   ├── etf.py                          # ETF / fonds                            [P1]
│   │   ├── scpi.py                         # SCPI / OPCI (non cotés)               [P1]
│   │   ├── private_equity.py               # Private Equity (valorisation NAV)      [P1]
│   │   └── __init__.py
│   │
│   ├── portfolio/                          # Gestion multi-portefeuilles
│   │   ├── portefeuille.py                 # Gestionnaire nommé + sauvegarde        [P1]
│   │   ├── markowitz.py                    # Frontière efficiente Markowitz         [P1]
│   │   ├── allocation.py                   # Poids & rebalancement                  [P1]
│   │   └── __init__.py
│   │
│   ├── market/                             # Données de marché
│   │   ├── courbe_taux.py                  # Bootstrap + interpolation              [P1]
│   │   ├── data_loader.py                  # Import CSV + saisie manuelle           [existant]
│   │   └── __init__.py
│   │
│   ├── risk/                               # Moteur de risque
│   │   ├── sensibilites.py                 # DV01, BPV, Beta, CS01, Delta FX       [P1]
│   │   ├── var.py                          # VaR paramétrique                       [existant][P2]
│   │   ├── var_historique.py               # VaR historique réelle                  [P2]
│   │   ├── var_montecarlo.py               # VaR Monte Carlo                        [P2]
│   │   ├── expected_shortfall.py           # CVaR / Expected Shortfall              [P2]
│   │   ├── correlation.py                  # Matrice corrélation multi-actifs       [P2]
│   │   ├── pnl_explain.py                  # P&L Explain (carry, taux, convexité, spread) [P2]
│   │   ├── stress_test.py                  # Stress tests + scénarios IRRBB         [existant][P2]
│   │   └── __init__.py
│   │
│   ├── regulatory/                         # Modules réglementaires
│   │   ├── scr.py                          # SCR marché Solvabilité II              [P4]
│   │   ├── irrbb.py                        # 6 scénarios EBA standard               [P4]
│   │   ├── alm.py                          # Duration gap actif-passif              [P4]
│   │   └── __init__.py
│   │
│   ├── reporting/                          # Outputs Middle Office
│   │   ├── dashboard.py                    # Rapport daily MO                       [P3]
│   │   ├── rapport_pdf.py                  # Export PDF                             [P3]
│   │   ├── export_excel.py                 # Export Excel formaté                   [P3]
│   │   └── __init__.py
│   │
│   └── ui/                                 # Interface Streamlit
│       ├── lang.py                         # Traductions FR/EN                      [existant]
│       └── pages/
│           ├── home.py                     # Page d'accueil                         [existant]
│           ├── instruments.py              # Saisie / visualisation instruments     [P1]
│           ├── portfolio.py                # Gestion portefeuilles + Markowitz      [existant][P1]
│           ├── risk.py                     # VaR + sensibilités                     [existant][P2]
│           ├── pnl.py                      # P&L Explain                            [P2]
│           ├── stress.py                   # Stress tests + scénarios               [P2]
│           ├── regulatory.py               # SCR + IRRBB + ALM                      [P4]
│           └── reporting.py               # Dashboard MO + exports                 [P3]
│
├── data/
│   ├── portefeuille_oblig.csv              # Portefeuille obligataire exemple       [existant]
│   ├── portefeuille_mixte.csv              # Portefeuille multi-actifs exemple      [P1]
│   ├── curve.csv                           # Courbe des taux                        [existant]
│   └── historique/                         # Séries temporelles de marché           [P2]
│
├── tests/
│   ├── test_obligation.py                  # Tests obligation                       [existant]
│   ├── test_var.py                         # Tests VaR                              [existant]
│   ├── test_sensibilites.py                # Tests DV01, BPV, Beta, CS01            [P1]
│   ├── test_pnl_explain.py                 # Tests P&L Explain                      [P2]
│   └── test_stress.py                      # Tests stress tests                     [P2]
│
├── app.py                                  # Point d'entrée Streamlit               [existant]
├── README.md                               # Documentation projet                   [existant]
├── requirements.txt                        # Dépendances Python                     [existant]
└── .streamlit/
    └── config.toml                         # Config Streamlit                       [existant]
```

---

## Résumé par phase

| Phase | Dossiers principaux | Nb fichiers |
|-------|---------------------|-------------|
| P1 — Socle multi-actifs | `instruments/`, `portfolio/`, `market/` | 11 |
| P2 — Analyse de risque avancée | `risk/` | 15 |
| P3 — Reporting & Middle Office | `reporting/` | 9 |
| P4 — Réglementaire & Capital | `regulatory/` | 9 |

**Total : 44 modules**

---

## Ordre de développement recommandé

1. `src/instruments/base.py` — classe abstraite, socle de tout
2. `src/instruments/obligation.py` — migration depuis RiskBonSim
3. `src/market/courbe_taux.py` — brancher le curve.csv existant
4. `src/risk/sensibilites.py` — DV01, BPV, Beta, CS01
5. `src/portfolio/portefeuille.py` — gestionnaire multi-portefeuilles
6. `src/portfolio/markowitz.py` — frontière efficiente
7. `src/risk/pnl_explain.py` — P&L Explain complet
8. `src/risk/var_historique.py` — VaR historique réelle
9. `src/reporting/dashboard.py` — rapport daily MO
10. `src/regulatory/scr.py` — SCR Solvabilité II
