# Checks

Минимальные проверки репозитория без установки зависимостей.

## Быстрая проверка

macOS/Linux или Git Bash:

```bash
git status --short --branch
git ls-files | sort
test -f README.md
test -f AGENTS.md
test -f handoff/current.md
test -f .gitignore
```

Windows PowerShell:

```powershell
git status --short --branch
git ls-files | Sort-Object
Test-Path README.md
Test-Path AGENTS.md
Test-Path handoff/current.md
Test-Path .gitignore
```

## Проверка секретов

macOS/Linux или Git Bash:

```bash
rg -n --hidden --glob '!.git/**' --glob '!outputs/**' --glob '!work/**' \
  '(AKIA[0-9A-Z]{16}|AIza[0-9A-Za-z_-]{35}|gh[pousr]_[0-9A-Za-z_]{36,255}|sk-[0-9A-Za-z]{20,}|-----BEGIN (RSA |OPENSSH |EC |DSA )?PRIVATE KEY-----)' .
```

Windows PowerShell:

```powershell
rg -n --hidden --glob '!.git/**' --glob '!outputs/**' --glob '!work/**' '(AKIA[0-9A-Z]{16}|AIza[0-9A-Za-z_-]{35}|gh[pousr]_[0-9A-Za-z_]{36,255}|sk-[0-9A-Za-z]{20,}|-----BEGIN (RSA |OPENSSH |EC |DSA )?PRIVATE KEY-----)' .
```

Если команда ничего не выводит, типовые секреты не найдены. Это не заменяет полноценный secret scan, но ловит самые опасные случайные коммиты.

## Что проверять вручную

- наличие обязательных файлов;
- отсутствие секретов;
- свежесть handoff;
- корректность task-id;
- базовая проверка ссылок и источников.

## Ограничения

- В проекте пока нет кода, тестов, сборки, Docker или CI.
- Основная проверка сейчас - структурная и документальная.
- Для будущих кодовых проектов проверки должны жить в отдельных репозиториях.
