# Migrations de la base de données

La base de données utilisé PostgreSQL. [Goose](https://github.com/pressly/goose) est utilisé pour les migrations (c'est-à-dire les évolutions de la base de données).

## Création d'une migration

Un script est disponible pour créer une migration vide.

```bash
./scripts/create_migration.sh "nom-de-la-migration"
```

## Composition d'une migration

Une migration est composée d'un fichier SQL.

```sql
-- +goose Up
-- SQL in this section is executed when the migration is applied.

CREATE TABLE table_name (
    id SERIAL PRIMARY KEY,
    ...
);

-- +goose Down
-- SQL in this section is executed when the migration is rolled back.
DROP TABLE IF EXISTS table_name;
```

Dans la première partie, vous définissez les requêtes SQL qui seront executés lors de la migration. Dans la seconde partie, vous définissez les requêtes SQL qui seront executés lors du rollback (en gros revenir à la version précédente, jamais en théorie mais ça peut arriver en cas de problème).

## Exécution des migrations

Les migrations sont exécutées automatiquement au démarrage de l'application.

```

```
