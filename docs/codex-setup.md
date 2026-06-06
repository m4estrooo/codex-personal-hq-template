# Настройка Codex

## Глобальные инструкции

Глобальный файл правил:

- macOS/Linux: `~/.codex/AGENTS.md`
- Windows: `%USERPROFILE%\.codex\AGENTS.md`

В него кладутся личные правила владельца, которые должны работать во всех проектах.

Резервная копия этих правил хранится в `templates/codex-global/AGENTS.md`.

Установить на macOS/Linux:

```bash
mkdir -p ~/.codex
cp templates/codex-global/AGENTS.md ~/.codex/AGENTS.md
```

Установить на Windows PowerShell:

```powershell
mkdir $env:USERPROFILE\.codex
copy templates\codex-global\AGENTS.md $env:USERPROFILE\.codex\AGENTS.md
```

Если меняешь глобальный файл вручную, обнови `templates/codex-global/AGENTS.md` и сделай `commit + push`, чтобы не потерять правила при смене устройства.

## Проектные инструкции

Файл `AGENTS.md` в корне этого репозитория описывает правила только для текущего репозитория.

Codex читает инструкции слоями:

1. глобальный `AGENTS.override.md` или `AGENTS.md`;
2. проектные `AGENTS.override.md` или `AGENTS.md` от корня проекта к текущей папке;
3. дополнительные fallback-файлы, если они указаны в настройках Codex.

Файлы ближе к текущей папке имеют больший приоритет.

## Проверка

В новом чате из корня репозитория попроси Codex:

```text
Перечисли активные инструкции, которые ты видишь для этого проекта.
```

В ответе должны быть правила про русский язык, handoff, план-трекер, Git-протокол и проверку динамических фактов.
