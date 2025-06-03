# Logging

Le logging est géré par le package `utils`.

## Utilisation

```go
utils.LogHeader("📧 JWT Middleware")
utils.LogMessage(utils.LevelError, "Invalid token")
utils.LogLineKeyValue(utils.LevelError, "Error", err)
utils.LogFooter()

// Sortie:
// ╔======== 📧 JWT Middleware ========╗
// ║ Invalid token
// ║ Error: invalid token
// ╚======== 📧 JWT Middleware ========╝
```
