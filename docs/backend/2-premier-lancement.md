# Configuration de l'environnement et premier lancement

*Avez vous suivi le [guide de configuration d'un poste de développement pour Transat ?](../commun/poste.md)*

## .env

Récupérez le fichier `.env.example` et renommez-le `.env`. Ensuite, configurez les variables d'environnement. Remplacez `GOOGLE_TRANSLATE_API_KEY`, `OPENWEATHERMAP_API_KEY`, ainsi que toutes les variables liées aux mails (`EMAIL_`) par les clés API fournies sur le channel "#『🔐』resources-identifiants", ou utilisez les vôtres.

Votre fichier `.env` devrait ressembler à cela:

!!! example "Exemple de fichier .env"

    ```env
    # Configuration de la base de données
    DB_NAME=
    DB_USER=
    DB_PASS=
    DB_HOST=
    DB_PORT=
    
    # Sécurité
    JWT_SECRET=
    
    GOOGLE_TRANSLATE_API_KEY=
    
    OPENWEATHERMAP_API_KEY=
    
    # Configuration Email
    EMAIL_PASSWORD=
    
    # ——— Email (Primary: Brevo HTTP API) ———
    # Required: Brevo API key (not SMTP password)
    BREVO_API_KEY=
    
    # Shared sender identity used by Brevo and as default for SMTP1
    EMAIL_SENDER=
    EMAIL_SENDER_NAME=
    
    # ——— SMTP Fallback 1 (Gmail or other SMTP) ———
    EMAIL_HOST_GMAIL_1=
    EMAIL_PORT_GMAIL_1=
    EMAIL_PASSWORD_GMAIL_1=
    EMAIL_SENDER_GMAIL_1=
    EMAIL_SENDER_NAME_GMAIL_1=
    
    # ——— SMTP Fallback 2 (Second Gmail/SMTP account) ———
    EMAIL_HOST_GMAIL_2=
    EMAIL_PORT_GMAIL_2=
    EMAIL_PASSWORD_GMAIL_2=
    EMAIL_SENDER_GMAIL_2=
    EMAIL_SENDER_NAME_GMAIL_2=
    
    # ——— Discord Webhooks ———
    # Existing Discord service webhook (if you already use it elsewhere)
    DISCORD_WEBHOOK_URL=
    
    # Dedicated webhook for email failure alerts (required; no defaults in code)
    DISCORD_EMAIL_ALERT_WEBHOOK=
    
    ALLOWED_ORIGINS=*
    
    # R2 Storage
    R2_ACCESS_KEY_ID=
    R2_ACCESS_KEY_SECRET=
    R2_ACCOUNT_ID=
    R2_BUCKET_NAME=
    R2_PUBLIC_DOMAIN=
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
