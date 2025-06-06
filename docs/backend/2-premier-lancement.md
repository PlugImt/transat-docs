# Configuration de l'environnement et premier lancement

*Avez vous suivi le [guide de configuration d'un poste de développement pour Transat ?](../commun/poste.md)*

## .env

Récupérez le fichier `.env.example` et renommez-le `.env`. Ensuite, configurez les variables d'environnement. Remplacez `GOOGLE_TRANSLATE_API_KEY`, `OPENWEATHERMAP_API_KEY`, ainsi que toutes les variables liées aux mails (`EMAIL_`) par les clés API fournies sur le channel "#『🔐』resources-identifiants", ou utilisez les vôtres.

Votre fichier `.env` devrait ressembler à cela:

!!! example "Exemple de fichier .env"

    ```env
    # Configuration de la base de données
    DB_USER=transat
    DB_PASS=transat
    DB_HOST=localhost
    DB_PORT=5432
    DB_NAME=transat

    DATABASE_URL=postgres://transat:transat@localhost:5432/transat
    PORT=3000

    # Sécurité
    JWT_SECRET=super-secret-key

    GOOGLE_TRANSLATE_API_KEY=abc123

    OPENWEATHERMAP_API_KEY=abc123

    # Configuration Email
    EMAIL_SENDER=transat@transat.dev
    EMAIL_HOST=transat.dev
    EMAIL_PORT=465
    EMAIL_PASSWORD=transat

    ENV=development

    DATA_FOLDER=./data
    ```

## Base de donnée locale

Pour ne pas dépendre de la base de données centrale (ne travaillez pas en prod…), vous pouvez lancer une base de données locale. Un fichier Docker Compose est disponible pour vous simplifier la tâche. L'utilisateur, le mot de passe et le nom de la base de données viennent du fichier `.env`, ainsi la configuration de la base de données locale est identique à celle de la base de données centrale (à part le port/host).

```bash
docker compose up -d
```

### Initialisation et migrations de la base de données

L'application utilise [Goose](https://github.com/pressly/goose) pour les migrations. Les migrations devraient s'éxécuter automatiquement au démarrage de l'application.

En apprendre plus sur les [migrations](./migrations.md).

## Premier lancement

```bash
go run .
```

## Première compilation

```bash
go build .
```



## Développement

Pour développer l'application, vous pouvez utiliser [Air](https://github.com/cosmtrek/air) pour automatiser le rechargement de l'application lorsque vous modifiez un fichier.

```bash
# Installer Air
go install github.com/air-verse/air@latest

air
```
