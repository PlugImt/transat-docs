# Migrations de la base de données

La base de données utilisée est PostgreSQL. [Goose](https://github.com/pressly/goose) est utilisé pour les migrations (c'est-à-dire les évolutions de la base de données).

## Qu'est-ce qu'une migration?

Un besoin courant avec une base de données relationnelle est de modifier la structure de la base de données. Par exemple, on veut ajouter une colonne à une table, la renommer, ou encore supprimer une table. On crée alors une migration pour effectuer ces modifications.

## Création d'une migration

Un script est disponible pour créer une migration vide.

```bash
./scripts/create_migration.sh "nom_de_la_migration"
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

## FAQ

!!! question "Comment appliquer une migration?"

    Les migrations sont automatiquement appliquées lors du démarrage de l'application.
    Cependant, il est quand même possible de les appliquer manuellement.

    Adaptez les paramètres de la commande à votre configuration:
    ```bash
    goose -dir db/migrations postgres "host=localhost port=5432 user=postgres password=postgres dbname=postgres sslmode=disable" up
    ```

!!! question "Est-ce que je peux modifier une migration existante?"

    C'est techniquement faisable, mais ce n'est **pas recommandé**. Il est préférable de créer une nouvelle migration pour les modifications.
    En effet, si la migration a déjà été appliquée, la migration modifiée ne sera pas appliquée. Le problème se pose surtout en production, car en dev, on peut tout remettre à zéro facilement.

## Troubleshotting 

Si en lançant la commande, vous obtenez une erreur comme ceci:

```bash
$ ./scripts/create_migration.sh "add_passid_and_courses"
goose n'est pas installé. Installation en cours...
Impossible d'installer goose automatiquement.
Veuillez l'installer manuellement: go install github.com/pressly/goose/v3/cmd/goose@latest
```

1. Vérifiez que goose est bien installé dans votre [$GOPATH](https://go.dev/wiki/GOPATH):

=== "Linux/macOS"

    ```bash
    ls ~/go/bin
    ```

=== "Windows"

    ```powershell
    Get-ChildItem "$HOME\go\bin"
    ```

Si tel est le cas, vérifiez si votre `$PATH` contient le répertoire de votre `~/go/bin`&nbsp;:

=== "Linux/macOS"

    ```bash
    echo $PATH | sed 's/:/\n/g' | grep ~/go/bin
    ```

=== "Windows"

    ```powershell
    $env:PATH -split ';' | Where-Object { $_ -like "$HOME\go\bin" }
    ```

Si ce n'est pas le cas, ajoutez le répertoire à votre `$PATH`. Temporairement:
=== "Linux/macOS"

    ``` sh
    export PATH=$PATH:~/go/bin
    ```

=== "Windows"

    ``` sh
    set PATH=%PATH%;%USERPROFILE%\go\bin
    ```

Plus proprement: voir la doc de votre shell.
