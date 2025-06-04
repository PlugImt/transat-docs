# Sentry

L'application utilise [Sentry](https://sentry.io/for/go/) pour la gestion des erreurs, avec l'intégration de [Sentry pour Fiber](https://docs.sentry.io/platforms/go/guides/fiber/).

Sentry nous sponsorise un plan gratuit, nous les remercions !

Il est nécessaire d'être ajouté à l'organisation GitHub [PlugImt](https://github.com/PlugImt) pour pouvoir accéder à Sentry.


[Connexion :simple-sentry:](https://plugimt.sentry.io/issues/){ .md-button target="_blank" }


## Configuration

La configuration de Sentry se fait dans le fichier `sentry.go`, dans le package `utils`.
Sentry est désactivé en développement.

## Logging
Les logs sont envoyés à Sentry, via le logger d'`utils`.
