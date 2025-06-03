# Première configuration de l'environnement

## .env

Récupérez le fichier `.env.example` et renommez-le `.env`.

!!! question "Qu'est-ce qu'un fichier `.env`?"

    Un fichier `.env` est un qui contient des variables d'environnement, une par ligne. Dans l'application, ce fichier est chargé par Expo. Il contient l'URL de l'API.

## Installer les dépendances

```bash
npm install
```

## Lefthook

Lefthook est un outil de gestion des hooks Git.

!!! question "Qu'est-ce qu'un hook Git?"

    Un hook Git est un script qui est exécuté automatiquement lors d'une commande Git, à certains moments clés. Par exemple, il est possible de vérifier que le code est conforme aux conventions de code avant de commiter.

    Ils sont installés dans le dossier `.git/hooks` du projet. Pour simplifier l'installation, nous utilisons Lefthook.

```bash
lefthook install

# Sortie attendue:
# sync hooks: ✔️ (pre-commit)
```

# Lancer l'application

```bash
npm run android|ios # selon votre choix
```

!!! info "Premier lancement un peu long"

    La première exécution peut prendre un peu de temps, car une build de développement sera compilée. Vous pouvez en lire un peu plus [ici](https://docs.expo.dev/develop/development-builds/create-a-build/).

Vous n'aurez plus besoin de relancer cette commande, sauf si vous avez modifié le fichier `package.json`.

Il suffit en effet de lancer la commande suivante pour lancer l'application:

```bash
npm run start
```

Puis d'appuyer sur `i` ou `a` pour lancer l'application sur iOS ou Android.
