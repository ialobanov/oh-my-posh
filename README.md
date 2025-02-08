# Setup Oh-My-Posh

## PowerShell Profile

```powershell
vim $PROFILE
```

```powershell
oh-my-posh init pwsh --config $env:USERPROFILE\.ohmyposh\zen.toml | Invoke-Expression
```

## Zen Theme

```powershell
mkdir .ohmyposh
```

```powershell
vim ~\.ohmyposh\zen.toml
```

```toml
console_title_template = '{{ .Shell }} in {{ .Folder }}'
version = 3
final_space = true

[palette]
  black = '#262B44'
  blue = '#4B95E9'
  green = '#59C9A5'
  orange = '#F07623'
  red = '#D81E5B'
  white = '#E0DEF4'
  yellow = '#F3AE35'

[[blocks]]
  type = 'prompt'
  alignment = 'left'
  newline = true

  [[blocks.segments]]
    type = 'path'
    style = 'plain'
    background = 'tranparent'
    foreground = 'blue'
    template = '{{ .Path }}'

    [blocks.segmants.properties]
      style = 'full'

  [[blocks.segments]]
     type = 'git'
     style = 'plain'
     foreground = '#6c6c6c'
     background = 'transparent'
     template = '{{ .HEAD }}{{ if or (.Working.Changed) (.Staging.Changed) }}*{{ end }} <cyan>{{ if gt .Behind 0 }}⇣{{ end }}{{ if gt .Ahead 0 }}⇡{{ end }}</>'

    [blocks.segments.properties]
      branch_icon = ' '
      commit_icon = '@'
      fetch_status = true

[[blocks]]
  type = 'rprompt'
  overflow = 'hidden'

    [[blocks.segments]]
      type = 'executiontime'
      style = 'plain'
      foreground = 'yellow'
      background = 'transperent'
      template = '{{ .FormattedMs }}'

      [blocks.segments.properties]
        threshold = 5000

[[blocks]]
  type = 'prompt'
  alignment = 'left'
  newline = true

  [[blocks.segments]]
    type = 'text'
    style = 'plain'
    foreground_templates = [
      "{{if gt .Code 0}}red{{end}}",
      "{{if eq .Code 0}}magenta{{end}}",
    ]
    background = 'transparent'
    template = "❯"

[transient_prompt]
  foreground_templates = [
    "{{if gt .Code 0}}red{{end}}",
    "{{if eq .Code 0}}magenta{{end}}",
  ]
  background = 'transparent'
  template = '❯ '

[secondary_prompt]
  foreground = 'magenta'
  background = 'transparent'
  template = '❯❯ '
```
