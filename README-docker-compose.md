# Docker Compose - Lancement des services

## Structure

- **Frontend** (Calculator) : Port 3001
- **API JavaScript** (calculator-api-js) : Port 3000
- **API Python** (calculator-api-python) : Port 3000
- **API Java** (calculator-api-java) : Port 3000

## Lancement

### Lancer Front + un Back de ton choix

```bash
# Front + API JavaScript
./run-js.sh

# Front + API Python
./run-python.sh

# Front + API Java
./run-java.sh
```

### Lancer Front + tous les Back

```bash
./run-all.sh
```

### Lancer uniquement le Front

```bash
docker compose up -d frontend
```

### Lancer uniquement un Back

```bash
docker compose up -d api-js
docker compose up -d api-python
docker compose up -d api-java
```

### Arrêter les services

```bash
docker compose down
```

### Voir les logs

```bash
docker compose logs -f
```

### Voir l'état des services

```bash
docker compose ps
```

## URL d'accès

- **Frontend** : http://localhost:3001
- **API JavaScript** : http://localhost:3000
- **API Python** : http://localhost:3000
- **API Java** : http://localhost:3000
