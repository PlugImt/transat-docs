# Commencer à développer sur Transat

L'application Transat est en deux parties, le [backend](../backend/index.md) en Go et le [mobile](../app/index.md) en React Native. Vous pouvez donc sauter directement à la section qui vous intéresse, si vous ne souhaitez pas développer sur l'intégralité de l'application.

## Prérequis

!!! tip "Pour les utilisateurs sous macOS"

    Il faut installer [Homebrew](https://brew.sh/), un gestionnaire de paquets pour macOS. Si vous ne l'avez pas déjà, vous pouvez l'installer avec la commande suivante:
    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

!!! tip "Pour les utilisateurs sous Windows"

    Installez [Chocolatey](https://chocolatey.org/), un gestionnaire de paquets pour Windows. Si vous ne l'avez pas déjà, vous pouvez l'installer. Ouvrez PowerShell en tant qu'administrateur et exécutez la commande suivante:

    ```powershell
    powershell -c "irm https://community.chocolatey.org/install.ps1|iex"
    ```

## Mobile

### Dépendances logicielles à installer

Tout d'abord, pour une app React Native, il faut installer **Node.js**.

=== "Linux/macOS"
    
    Je vous conseille d'installer [nvm](https://github.com/nvm-sh/nvm), un gestionnaire de version de Node.js.
    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
    source ~/.bashrc
    nvm install 22
    nvm alias default 22
    nvm use default
    ```

    Sinon, vous pouvez installer Node.js avec le gestionnaire de paquets de votre distribution, ou `brew` sur macOS.

=== "Windows"

    Installez Node.js avec [Chocolatey](https://chocolatey.org/).

    ```powershell
    # Download and install Node.js
    choco install nodejs-lts --version="22"

    # Verify the Node.js version
    node -v # Should print "v22.16.0".

    # Verify npm version
    npm -v # Should print "10.9.2".
    ```

### Cloner le repo

Clonez le repo de l'application:
```bash
git clone https://github.com/plugimt/transat-app.git
cd transat-app
```

Voir la page [Configuration de l'environnement et premier lancement](../app/2-premier-lancement.md) pour continuer

## Backend

=== "Linux/macOS"

    ### Go
    Installez Go avec le gestionnaire de paquets de votre distribution.

    Sous macOS, vous pouvez installer Go avec `brew`:

    ```bash
    brew install go
    ```

    ### Docker

    Sous Linux, installez Docker avec le gestionnaire de paquets de votre distribution.

    Sous macOS, installez Docker Desktop avec brew:

    ```bash
    brew install --cask docker
    ```

=== "Windows"

    ### Go
    Installez Go avec [Chocolatey](https://chocolatey.org/).

    ```powershell
    # Download and install Go
    choco install go --version="1.23.4"

    # Verify the Go version (should print "go version go1.23.4 windows/amd64")
    go version
    ```

    ### Docker
    Installez Docker Desktop avec Chocolatey:

    ```powershell
    choco install docker-desktop
    ```

### PostgreSQL

Il n'est pas nécessaire d'installer PostgreSQL nativement sur votre machine, la base de données est déployée par Docker.

### Configurer le projet

```bash
git clone https://github.com/plugimt/transat-backend.git
cd transat-backend/
```

Voir la page [Configuration de l'environnement et premier lancement](../backend/2-premier-lancement.md)