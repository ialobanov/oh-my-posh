# Setup Oh-My-Posh

## PowerShell Profile

```powershell
vim $PROFILE
```

```properties
oh-my-posh init pwsh --config $env:USERPROFILE\.ohmyposh\zen.toml | Invoke-Expression
```
