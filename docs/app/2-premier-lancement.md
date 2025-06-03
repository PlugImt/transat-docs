# Première configuration de l'environnement

## .env

Récupérez le fichier `.env.example` et renommez-le `.env`.

## Installer les dépendances

```bash
npm install
```

## Lefthook

Lefthook est un outil de gestion des hooks Git. Il est utilisé pour vérifier le respect des conventions de code (Linter, formatter, etc avec [Biome](https://biomejs.dev/fr/)).

```bash
lefthook install

# Sortie attendue:
# sync hooks: ✔️ (pre-commit)
```

# Lancer l'application

```bash
npm run android|ios # selon votre choix
```

La première exécution peut prendre un peu de temps, car une build de développement sera compilée.

Pour les prochaines exécutions, le temps de build sera plus rapide. De plus, il sera possible de directement lancer la development build (si elle est encore installée) avec `npm run start`, puis de faire `i` ou `a` pour lancer l'application sur iOS ou Android.
