# 🧮 Calculatrice API - Projet Multi-Backend

Projet éducatif de calculatrice avec interface frontend Node.js et 3 implémentations backend (JavaScript, Java, Python) pour démontrer la portabilité et la flexibilité des architectures API.

## 📋 Table des Matières

- [Présentation](#présentation)
- [Architecture](#architecture)
- [Installation](#installation)
- [Lancement avec Docker Compose](#lancement-avec-docker-compose)
- [Choix du Backend](#choix-du-backend)
- [Tests](#tests)
- [CI/CD](#cicd)
- [Contributions](#contributions)
- [Licence](#licence)

---

## 📖 Présentation

Ce projet propose une calculatrice complète avec :

- **Frontend** : Interface utilisateur moderne en Node.js avec Playwright pour les tests E2E
- **3 Backends** : Implémentations API dans JavaScript, Java et Python
- **Docker** : Conteneurisation complète pour un déploiement unifié

Choisissez le backend qui vous convient et lancez tout le projet en une seule commande !

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Frontend (Node.js)                        │
│              Interface utilisateur + Tests Playwright         │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
        ┌───────────────────────────────────────┐
        │      Choix du Backend (1/3)            │
        └───────────────────────────────────────┘
        │              │              │
        ▼              ▼              ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│  JS API     │ │   Java API  │ │  Python API │
│ (Node.js)   │ │  (Spring)   │ │  (FastAPI)  │
└─────────────┘ └─────────────┘ └─────────────┘
```

### Technologies

| Composant | Technologie |
|-----------|-------------|
| Frontend | Node.js, HTML/CSS/JS |
| Tests Frontend | Playwright |
| Backend JS | Node.js, Express |
| Backend Java | Spring Boot, Maven |
| Backend Python | FastAPI, pytest |
| Conteneurisation | Docker, Docker Compose |

---

## 🚀 Installation

### Prérequis

Avant de lancer le projet, assurez-vous d'avoir installé :

- **Docker** et **Docker Compose** (v20+)
- **Git**
- **Node.js** (v18+)
- **Java** (v17+) - pour le backend Java
- **Python** (v3.10+) - pour le backend Python

### Cloner le projet

```bash
git clone https://github.com/Loocist23/test-js.git
cd test-js
```

---

## 🐳 Lancement avec Docker Compose

### Option 1 : Lancer tous les services (Frontend + 3 Backends)

```bash
docker-compose up --build
```

Cela lancera :
- Frontend Node.js
- Backend JavaScript
- Backend Java
- Backend Python

### Option 2 : Lancer uniquement le Frontend

```bash
docker-compose --file docker-compose.yml frontend up --build
```

### Option 3 : Lancer un Backend spécifique

```bash
# Backend JavaScript
docker-compose --file docker-compose.yml api-js up --build

# Backend Java
docker-compose --file docker-compose.yml api-java up --build

# Backend Python
docker-compose --file docker-compose.yml api-python up --build
```

### Vérifier les services

```bash
# Voir les logs
docker-compose logs -f

# Voir les services en cours d'exécution
docker-compose ps

# Arrêter les services
docker-compose down
```

---

## 🎯 Choix du Backend

### JavaScript (Node.js)

**Avantages :**
- ✅ Développement rapide
- ✅ Écosystème riche (npm)
- ✅ Asynchrone natif
- ✅ Intégré au frontend

**Commandes :**
```bash
# Lancer l'API
cd calculator-api-js
npm install
npm start

# Lancer les tests
npm test
```

**Port :** 3001

### Java (Spring Boot)

**Avantages :**
- ✅ Typage fort
- ✅ Performance élevée
- ✅ Écosystème Spring mature
- ✅ Bonnes pratiques par défaut

**Commandes :**
```bash
# Lancer l'API
cd calculator-api-java
mvn spring-boot:run

# Lancer les tests
mvn test
```

**Port :** 8080

### Python (FastAPI)

**Avantages :**
- ✅ Syntaxe moderne
- ✅ Documentation automatique (Swagger)
- ✅ Asynchrone
- ✅ Typage optionnel (Pydantic)

**Commandes :**
```bash
# Lancer l'API
cd calculator-api-python
pip install -r requirements.txt
uvicorn main:app --reload

# Lancer les tests
pytest
```

**Port :** 8000

### Tableau Comparatif

| Critère | JavaScript | Java | Python |
|---------|------------|------|--------|
| Vitesse de développement | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Performance | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Typage | Dynamique | Fort | Optionnel |
| Documentation | Manuelle | Auto (SpringDoc) | Auto (Swagger) |
| Tests | Jest | JUnit | Pytest |
| Écosystème | npm | Maven | pip |

---

## 🧪 Tests

### Tests Frontend (Playwright)

```bash
cd Calculator
npm test
```

Les tests vérifient :
- Interface utilisateur
- Calculs de base (+, -, *, /)
- Gestion des erreurs
- Responsive design

### Tests Backend

#### JavaScript
```bash
cd calculator-api-js
npm test
```

#### Java
```bash
cd calculator-api-java
mvn test
```

#### Python
```bash
cd calculator-api-python
pytest
```

### Lancement des tests avec Docker

```bash
# Tous les tests
docker-compose exec frontend npm test

# Tests backend JS
docker-compose exec api-js npm test

# Tests backend Java
docker-compose exec api-java mvn test

# Tests backend Python
docker-compose exec api-python pytest
```

---

## 🔄 CI/CD

### GitHub Actions

Chaque backend possède son propre workflow :

- **JavaScript** : `.github/workflows/js.yml`
- **Java** : `.github/workflows/java.yml`
- **Python** : `.github/workflows/python.yml`

### Workflow typique

```yaml
name: CI Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: install dependencies
      - run: run tests
      - run: code coverage
```

---

## 📊 Coverage

Chaque backend inclut un rapport de couverture :

```bash
# JavaScript
npm run coverage

# Java
mvn clean verify coverage:report

# Python
pytest --cov=src --cov-report=html
```

---

## 🤝 Contributions

Les contributions sont les bienvenues ! Veuillez respecter :

1. Fork le projet
2. Créez une branche (`git checkout -b feature/nouvelle-fonctionnalité`)
3. Commitz vos changements (`git commit -m 'Ajout fonctionnalité'`)
4. Pushz vers la branche (`git push origin feature/nouvelle-fonctionnalité`)
5. Ouvrez une Pull Request

---

## 📝 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

---

## 📞 Support

Pour toute question ou problème, veuillez :

1. Vérifier les [FAQ](FAQ.md)
2. Ouvrir une issue sur GitHub
3. Contacter l'équipe

---

**Projet développé par :** Loocist23  
**Dernière mise à jour :** 2026-06-24
