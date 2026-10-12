# 🏥 CLINICONE — Application de Diagnostic Médical

Application de bureau en **Python** (interface CustomTkinter, thème sombre + vert) qui propose une aide au diagnostic (grippe/rhume, maladie cardiaque), des calculateurs médicaux, la génération de certificats et de rapports en PDF, et un historique des patients protégé par mot de passe.

> ⚠️ **Projet à but pédagogique uniquement.** Cette application ne remplace en aucun cas l'avis d'un professionnel de santé.

---

## ✨ Fonctionnalités

| Module | Description |
|---|---|
| 🤧 **Diagnostic Grippe / Rhume** | Classification par arbre de décision à partir de 4 symptômes (fièvre, fatigue, toux, courbatures) |
| ❤️ **Diagnostic Maladie Cardiaque** | Modèle entraîné sur le dataset *Cleveland Heart Disease* + alertes (tension, cholestérol) |
| 🧮 **Calculateurs médicaux** | IMC (avec interprétation colorée) et Surface Corporelle (formule de Mosteller) |
| 📄 **Certificats médicaux** | Arrêt de travail, aptitude au sport, certificat général, non-contagion (PDF avec logo) |
| 🗂️ **Historique patients** | Liste des patients de la session, protégée par mot de passe, export PDF |
| 📑 **Rapports PDF** | Rapport de diagnostic avec détails, alertes et zone de signature |
| 🌍 **Multi-langues** | Français 🇫🇷 / Arabe 🇹🇳 / Anglais 🇬🇧 (changement en un clic) |

---

## 🛠️ Technologies

- **Python 3.9+**
- [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) — interface graphique
- [scikit-learn](https://scikit-learn.org/) — `DecisionTreeClassifier`
- [pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/) — traitement des données
- [ReportLab](https://www.reportlab.com/) — génération de PDF

---

## 📦 Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/<votre-utilisateur>/clinicone.git
cd clinicone

# 2. (Optionnel) Créer un environnement virtuel
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

# 3. Installer les dépendances
pip install customtkinter scikit-learn numpy pandas reportlab
```

---

## 📁 Structure du projet

```
clinicone/
├── interface.py                # Application principale
├── processed.cleveland.csv     # Dataset cardiaque (obligatoire)
├── logo.png                    # Logo pour les PDF (optionnel)
└── README.md
```

### Dataset

Le module cardiaque utilise le fichier **`processed.cleveland.csv`** (UCI Machine Learning Repository — [Heart Disease](https://archive.ics.uci.edu/dataset/45/heart+disease)).

Le fichier doit :
- contenir une **ligne d'en-tête** avec les noms de colonnes ;
- avoir une colonne nommée **`target`** (0 = sain, 1–4 = malade) ;
- utiliser `?` pour les valeurs manquantes (elles sont supprimées automatiquement).

Colonnes attendues : `age, sex, cp, trestbps, chol, fbs, restecg, thalach, exang, oldpeak, slope, ca, thal, target`

---

## ▶️ Lancement

```bash
python interface.py
```

---

## 🚀 Utilisation

1. **Choisir la langue** (FR / AR / EN) en haut de la fenêtre.
2. **Diagnostic** : cocher les symptômes ou saisir les paramètres cardiaques, puis cliquer sur *Diagnostiquer*.
3. **Imprimer le rapport** : renseigner l'identité du patient pour générer un PDF (`rapport_<nom>_<prenom>.pdf`).
4. **Certificats** : choisir le type, remplir les champs, générer `certificat_<nom>_<prenom>.pdf`.
5. **Historique** : accessible via mot de passe (`admin` par défaut), exportable en PDF.

---


## 🔒 Sécurité & limites

- Le mot de passe de l'historique (`admin`) est **codé en dur** : à remplacer par un vrai système d'authentification pour un usage réel.
- L'historique est conservé **en mémoire** (perdu à la fermeture de l'application).
- Le modèle grippe/rhume est entraîné sur un **très petit jeu de données** d'illustration.
- Les noms de médecin et de ville dans les certificats sont des **champs fictifs** (`[Nom du médecin]`, `[Ville]`) à personnaliser.

---

## 🔮 Améliorations possibles

- Base de données (SQLite) pour un historique persistant
- Authentification sécurisée (mot de passe haché)
- Support complet RTL et police arabe dans les PDF
- Évaluation des modèles (précision, matrice de confusion)
- Packaging en exécutable (`PyInstaller`)

---


## 📄 Licence

Projet académique — libre d'utilisation à des fins éducatives.
