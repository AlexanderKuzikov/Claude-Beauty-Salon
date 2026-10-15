# Claude-Beauty-Salon — Instructions for AI Agents

## Commands
- lint: none (markdown-only repo, no build)
- test: none
- build: none

## Conventions
- Язык общения: русский, технические термины — как есть (EN)
- Ссылки на репозитории — всегда полные URL, проверенные (два URL из треда битые, исправления — в COLLECTION.md)
- Никакого КАПСА в заголовках

## Structure
- `README.md` — точка входа (<100 строк)
- `docs/COLLECTION.md` — вся добыча (исключение из правила «не создавать .md»: разрешено пользователем 2026-10-15)
- `docs/CONTEXT.md` — живое состояние + журнал
- `docs/DECISIONS.md` — ADR, append-only

## Do NOT touch
- Не запускать `npm install` / `pip install` — ставить нечего, это база знаний
- Не коммитить и не пушить без явной просьбы

## Documentation rules
- После работы — обнови docs/CONTEXT.md
- Если принял архитектурное решение — запиши в docs/DECISIONS.md
- НЕ создавай новых файлов документации без разрешения
- Переиспользуемые знания — в D:\GitHub\knowledge/README.md
