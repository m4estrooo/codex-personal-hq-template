# Глобальные правила Codex

Это резервная копия глобального `AGENTS.md` для Codex. Перед использованием замени правила на свои.

## Куда установить

macOS/Linux:

```bash
mkdir -p ~/.codex
cp templates/codex-global/AGENTS.md ~/.codex/AGENTS.md
```

Windows PowerShell:

```powershell
mkdir $env:USERPROFILE\.codex
copy templates\codex-global\AGENTS.md $env:USERPROFILE\.codex\AGENTS.md
```

## Важно

- Этот файл не должен содержать секреты, токены, пароли, cookie или приватные ключи.
- Если меняешь глобальный `~/.codex/AGENTS.md`, обнови эту копию и сделай `commit + push`.
- Проектный `AGENTS.md` в конкретном репозитории может уточнять эти правила.
