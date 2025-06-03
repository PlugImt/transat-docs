# Configuration de l'environnement et premier lancement

## .env

Récupérez le fichier `.env.example` et renommez-le `.env`. Ensuite, configurez les variables d'environnement. Remplacez `GOOGLE_TRANSLATE_API_KEY`, `OPENWEATHERMAP_API_KEY`, ainsi que toutes les variables liées aux mails (`EMAIL_`) par les clés API fournies sur le channel "#『🔐』resources-identifiants"

## Base de donnée locale

Pour ne pas dépendre de la base de données centrale (ne travaillez pas en prod…), vous pouvez lancer une base de données locale. Un fichier Docker Compose est disponible pour vous simplifier la tâche. L'utilisateur, le mot de passe et le nom de la base de données viennent du fichier `.env`, ainsi la configuration de la base de données locale est identique à celle de la base de données centrale (à part le port/host).

```bash
docker compose up -d
```

## Migration

L'application utilise [Goose](https://github.com/pressly/goose) pour les migrations. Normalement, les migrations devraient s'éxécuter automatiquement au démarrage de l'application.

## Premier lancement

```bash
go run .
```

## Développement

Pour développer l'application, vous pouvez utiliser [Air](https://github.com/cosmtrek/air) pour automatiser le rechargement de l'application lorsque vous modifiez un fichier.

```bash
# Installer Air
go install github.com/air-verse/air@latest

air
```
