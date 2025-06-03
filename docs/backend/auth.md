# Authentification

L'authentification est gérée par un token JWT.

## Générer un token

Pour générer un token, il faut utiliser la fonction `GenerateJWT` du package `utils`.

```go
token, err := utils.GenerateJWT(email, jwtSecret, fingerprint)
```

## Vérification d'un token

Les tokens sont vérifiés avec le middleware `JWTMiddleware` du package `middlewares`. L'email contenu dans le token est stocké dans le contexte de la requête.

```go
c.Locals("email")
```
