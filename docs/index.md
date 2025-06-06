---
title: Accueil
hide:
    - navigation
    - toc
---

# Bienvenue sur la documentation de Transat !

<div class="grid cards" markdown>

-   :mobile_phone: &nbsp;
    **L'application mobile** &nbsp; :simple-expo:

    ***

    [:octicons-arrow-right-24: plus d'informations](app/index.md)

-   :material-server: &nbsp;
    **Le backend** &nbsp; :fontawesome-brands-golang:

    ***

    [:octicons-arrow-right-24: plus d'informations](backend/index.md)

-   :octicons-code-24: &nbsp;
    **Commun entre l'application et le backend**

    ***

    [:octicons-arrow-right-24: :simple-sentry: Sentry ](commun/sentry.md)

    [:octicons-arrow-right-24: Commencer à développer sur Transat](commun/poste.md)
</div>

## Contribuer à la documentation

La document de Transat est écrite en Markdown, à l'aide Mkdoc avec le [thème Material](https://squidfunk.github.io/mkdocs-material/).

## Comment contribuer?

```bash
# créer un venv
python3 -m venv .venv

# activer le venv
source .venv/bin/activate

# installer les dépendances
pip install -r requirements.txt

# lancer le serveur de documentation
mkdocs serve
```
