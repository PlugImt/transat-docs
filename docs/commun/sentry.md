# Sentry

L'application utilise [Sentry](https://sentry.io/for/go/) pour la gestion des erreurs, avec l'intégration de [Sentry pour Fiber](https://docs.sentry.io/platforms/go/guides/fiber/) sur le [backend](../backend/index.md) et [Sentry pour React Native](https://sentry.io/for/react-native/) sur l'application mobile.

Sentry nous sponsorise une offre gratuite, nous les remercions chaleureusement ! :orange_heart:

Il est nécessaire d'être ajouté à l'organisation GitHub [PlugImt](https://github.com/PlugImt) pour pouvoir accéder à Sentry.


[Connexion :simple-sentry:](https://plugimt.sentry.io/issues/){ .md-button target="_blank" }

## Liens utiles

[Logs :simple-sentry:](https://plugimt.sentry.io/explore/logs/?environment=production&logsFields=timestamp&logsFields=message&logsSortBys=-timestamp&statsPeriod=1h ){ .md-button target="_blank" }
[Errors :simple-sentry:](https://plugimt.sentry.io/explore/errors/?environment=production&errorsFields=timestamp&errorsFields=message&errorsSortBys=-timestamp&statsPeriod=7d ){ .md-button target="_blank" }
[Traces :simple-sentry:](https://plugimt.sentry.io/traces/?environment=production&statsPeriod=7d){ .md-button target="_blank" }
[Session replay :simple-sentry:](https://plugimt.sentry.io/replays/?environment=production&statsPeriod=7d){ .md-button target="_blank" }


## Backend
### Configuration

La configuration de Sentry se fait dans le fichier `sentry.go`, dans le package `utils`.
Sentry est désactivé en développement.

## Logging
Les logs sont envoyés à Sentry, via le logger d'`utils`.

## Application mobile

La configuration de Sentry se fait dans le fichier `_layout.tsx` racine de toute l'application.