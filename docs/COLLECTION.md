# Вся добыча из треда: 10 репозиториев, превращающих Claude Code в дизайнера

> Источник: https://x.com/RoundtableSpace/status/2110255627704455591
> Автор: 0xMarioNawfal (аккаунт про крипту и AI, 268к подписчиков)
> Дата: 2026-10-14. Охват: 324к просмотров, 3.3к репостов, 8.2к лайков
> Собрано: 2026-10-15. Все ссылки проверены, битые исправлены.

## Вердикт одной таблицей

| # | Репозиторий | Статус | Вердикт |
|---|-------------|--------|---------|
| 1 | superdesign | 7.4к звезд, ЗАБРОШЕН | пропустить |
| 2 | better-design | 416 звезд, живой | БРАТЬ (дашборды) |
| 3 | design-taste | 118 звезд, живой | БРАТЬ ПЕРВЫМ (вкус для агента) |
| 4 | canvas-ui | 5к звезд, живой | точечно (3D/эффекты) |
| 5 | paper shaders | 3.7к звезд, живой | БРАТЬ (фоны, zero-dep) |
| 6 | ui-layouts | 3.7к звезд, живой | витрина идей |
| 7 | hyperiux | ссылка из треда БИТАЯ, найден настоящий | пропустить (фримиум) |
| 8 | motion-primitives | 6.7к звезд, живой, самый зрелый | БРАТЬ точечно (анимации) |
| 9 | cursify | 2.1к звезд, живой | витрина идей (курсоры) |
| 10 | trickle | ссылка из треда БИТАЯ, найден настоящий | БРАТЬ (текст-анимации, zero-runtime) |

## Скепсис из комментариев (сохраняю, он по делу)

- «ten repos and the ui still screams bootstrap» — скиллы задают направление, вкус не гарантируют
- «Ten repos to make it a designer, but I still can't get it to pick a decent font» — про выбор шрифтов ни один репозиторий не решает, это решает design-taste/taste-typography
- «Лучше собери скилл сам: дай Claude примеры хорошего дизайна, пусть Claude сделает скилл. Если все пользуются одними скиллами — всё будет выглядеть одинаково» — аргумент за свой жанровый пак поверх design-taste, а не против него

---

## 1. Superdesign Skill — ПРОПУСТИТЬ

- В треде: https://github.com/superdesigndev/superdesign
- Сайт продукта: https://www.superdesign.dev
- Актуальный скилл: https://github.com/superdesigndev/superdesign-skill
- Chrome-расширение «клонируй любой сайт»: https://chromewebstore.google.com/detail/obpjaonipoaomjnokbimppohbpjibflm
- Звезд: 7.4к, форков 764. Лицензия: open source
- Что это: был AI-дизайн-агент внутри IDE (Cursor, Windsurf, Claude Code, VS Code) — мокапы, компоненты, вайрфреймы из промпта, designs сохранялись локально в `.superdesign/`
- Почему пропустить: в шапке репозитория написано прямым текстом — **репо историческое, больше не поддерживается**, продукт уехал в веб-приложение. Ставить старый экстеншн — ставить мёртвый код
- Что забрать вместо: идею `design.mdc` (системный промпт дизайна как кастомный режим в Cursor) и идею Chrome-расширения для клонирования референсов
- Поддержка локальных моделей: в старом README было про OpenAI-compatible серверы (пример `http://127.0.0.1:1234/v1` для LM Studio) — приём переиспользуемый для любых скиллов

## 2. Better Design — БРАТЬ (дашборды)

- Репозиторий: https://github.com/marvkr/better-design
- Сайт и превью всех тем: https://better-design.com , https://better-design.com/design-systems
- Настройки/API-ключ для remote MCP: https://better-design.com/settings
- Звезд: 416. Лицензия: MIT
- Что это: MCP-сервер + shadcn-регистр + слой ревью. Агент подбирает дизайн-систему под задачу, тянет токены и компоненты, потом сам себя ревьюит по WCAG и визуальным правилам
- Инструменты MCP: `resolve-design-system`, `get-design-system-docs`, `get-ui-principle` (иерархия, отступы, типографика, глубина, motion, формы), `get-review-rules` (a11y + визуал), `resolve-icon-library`, `search-icons` (через Iconify)
- Установка:
  - `npx skills add marvkr/better-design --skill better-design`
  - `npx better-design` (детектит тулзы, подключает MCP, аккаунт не нужен)
  - remote MCP вручную: `https://better-design.com/api/mcp` с Bearer-ключом
  - компонент в shadcn-проект: `npx shadcn@latest add https://www.better-design.com/registry/<система>/<компонент>.json`, пример: `.../registry/linear/button.json`
  - все 9 transitions.dev-портов разом: `.../registry/linear/transitions.json` (notification-badge, menu-dropdown, panel-reveal, card-resize, icon-swap, text-swap, modal-transition, page-slide, number-pop-in); исходник один — `scripts/transitions-src/`, регенерация `node scripts/generate-transitions.mjs`, тесты `cd tests && bun install && bun run test`
- Все 31 темы (светлые/тёмные, вайб, для чего): Linear dark (dev tools), Linear Quality dark (полированные dev tools), Supabase dark (бэкенд-дашборды), Vercel dark (Geist, деплой), Airbnb light (маркетплейсы), Notion light (продуктивность), Stripe light (финтех), Apple light (SF Pro, потребительские), Figma light (креативные тулзы), Light Marketplace (e-commerce), Precision Light (B2B), Minimal Light (утилиты), Dark Orange (SaaS), Vibrant Dark (соцсети), Neutral Monochrome (дата-тулзы), Cinematic Dark (стриминги), Editorial Dark (издательства, serif), Corporate Fintech (банки), Beam Custom, Beam Lib, Glassmorphic Dark, Inset Dark (аналитика), Lumen Dark (креатив), Metal FX Gold/Silver/Chromatic (премиум/железо/дерзкие бренды), Midnight Glass (аналитика), Monochrome Industrial (CLI-тулзы), Pillow Light (lifestyle), Tactile Minimal (фокус-тулзы), TV Style (медиа, 10-foot UI)
- Красивый сайт: better-design.com/design-systems — листать как каталог референсов, даже без установки
- Куда: Court-Viewer, CourtPulse, GefestBilling, SberBusiness, TestBuh — брать Linear / Corporate Fintech / Precision Light; ZavodsvayCom — Light Marketplace

## 3. Design Taste — БРАТЬ ПЕРВЫМ (вкус)

- Репозиторий: https://github.com/madebymustafa/design-taste
- Звезд: 118, форков 6. Лицензия: MIT
- Что это: 24 скилла, превращающие taste в инструкции. Диагноз: все агенты (Claude Code, Codex, Cursor, opencode) по умолчанию рисуют одно и то же — индиго-фиолетовый градиент, hero по центру, три карточки, Inter, slate-900, rounded-2xl. Репо лечит именно это
- Установка (5 секунд): `git clone https://github.com/madebymustafa/design-taste.git && cd design-taste && ./scripts/install.sh` (раскладывает все 24 скилла по найденным агентам), проверка `./scripts/validate.sh`. Вручную — скопировать папки `skills/*` в: Claude Code `~/.claude/skills/`, Cursor `~/.cursor/skills/`, Codex `~/.codex/skills/`, **opencode `~/.config/opencode/skills/`**, Cline/Roo `~/.cline/skills/` / `~/.roo/skills/`. Детали: `docs/INSTALL.md` в репо
- Ядро (1): `design-taste` — прочитай бриф, объяви design read, забань LLM-паттерны, докрути детали, pre-flight чеклист. Вешается на любую UI-генерацию
- Жанровые паки (10, выбирать ОДИН на проект): editorial-minimal (швейцарская печать: тёплая бумага, чернила, киноварь, serif+mono), brutalist-industrial (рассекреченный чертёж, моно-координаты), quiet-luxury (частный банк: слоновая кость, латунь/бычья кровь, serif с италиком), dark-tech (школа Linear/Vercel: почти-чёрный, hairline, моно-метаданные, один сдержанный акцент), playful-color (стикеры-постеры: гигантский жирный тип, толстые контуры, hard offset-тени), retro-print (ризо/70-80е: halftone, misregistered-оффсеты, штампы), japanese-minimal (ваби-саби: рисовая бумага, суми, ханко, пустота как лэйаут, один вертикальный текст), neo-brutalism (громкий потребительский веб: всё в черной обводке, 6px-тени, пилюли), corporate-trust (белый, один тёмно-синий, таблицы доказательств, чипы комплаенса), cinematic-motion (страница-как-фильм: чередующиеся сцены, живой экран продукта, scrub-счётчик, drag-карусель)
- Крафт-скиллы (9, кладутся поверх любого пака): taste-design-system (трёхуровневые токены primitive→semantic→component, DTCG, аудит инвентаря), taste-typography (пары, fluid-шкалы, длины строк, ритм), taste-color (архитектура 60-30-10, OKLCH-рампы, математика контраста WCAG 2.2, пары для дальтоников, тёмная тема), taste-motion (токены длительностей/изингов, хореография, reduced-motion), taste-gsap (context/matchMedia, таймлайны, pin/scrub-гигиена, только transform-анимации, refresh после шрифтов), taste-accessibility (WCAG 2.2 AA при генерации), taste-design-review (структурированный аудит: taste-проход → эвристики Нильсена → a11y → ранжированные находки), taste-landing-page (правило 8 секунд, hero-паттерны, CTA-дисциплина, психология прайсинга), taste-ux-copy (заголовки, кнопки, triады ошибка→фикс, empty states), taste-brand-identity (вордмарки, локапы, фавикон+og, бренд-лист)
- Код-скиллы (3): taste-code-craft (семантический HTML, токены вместо хардкода, ноль инлайн-стилей), taste-web-performance (бюджеты LCP/CLS/INP, шрифты без сдвигов, дисциплина картинок), taste-code-review (6 проходов: поведение→структура→вкус→безопасность→перформанс→a11y)
- Демо-доказательства (открыть рядом в браузере): `examples/before.html` vs `examples/after.html` (дефолт vs скилл, 5 секунд и всё ясно), по одному демо на жанр (`brutalist-industrial.html`, `quiet-luxury.html`, `dark-tech.html`, `playful-color.html`, `retro-print.html`, `japanese-minimal.html`, `neo-brutalism.html`, `corporate-trust.html`, `cinematic-motion.html`), `media/cinematic-motion-demo.gif` + полный ролик `.mp4` (один бриф, 39 секунд), `gallery/launch-grid.png` (все 10 идентичностей на одном брифе), папка `gallery/` принимает before/after от сообщества
- Роадмап репо: taste-figma-tokens (синк Figma↔код), CI render-to-screenshot с диффом со/без скиллов, маркетплейс паков
- Куда: ставится в opencode один раз — дальше на каждый проект по жанру: суды/биллинг — corporate-trust или dark-tech; Zavodsvay/каталоги — quiet-luxury или editorial-minimal; игровые/медийные — cinematic-motion или playful-color. SEO-проектам — связка taste-web-performance + trickle

## 4. Canvas UI — ТОЧЕЧНО (эффекты поверх живого HTML)

- Репозиторий: https://github.com/DavidHDev/canvas-ui
- Сайт, доки, компоненты, плейграунд: https://canvasui.dev , https://canvasui.dev/docs , https://canvasui.dev/components , https://canvasui.dev/playground , установка https://canvasui.dev/docs/installation , рендеринг https://canvasui.dev/docs/rendering , MCP https://canvasui.dev/docs/mcp
- Звезд: 5к, форков 247. Лицензия: MIT + Commons Clause (в своих проектах бесплатно, включая коммерческие; продавать саму библиотеку нельзя)
- Что это: 35 canvas-компонентов, эффекты бегут ПОВЕРХ живого интерактивного HTML (текст выделяется, ссылки кликаются) через экспериментальный HTML-in-canvas API; где не поддерживается — GPU-overlay fallback. Ноль конфигурации, ставится через shadcn-регистр, исходник падает в `components/canvasui/` и он твой
- Установка: `npx shadcn@latest add @canvas-ui/liquid-react` (liquid→любой компонент, react→solid/preact/vue/svelte/vanilla; `-webgpu` суффикс для WebGPU-сборок через vgpu/WGSL). MCP: `npx shadcn@latest mcp init --client claude`, работает с Claude Code, Cursor, VS Code, Codex, OpenCode — дальше «add the Liquid component from Canvas UI»
- Категории (35 шт): fluid (Liquid, Ripple, Cloth, Droplets, Bubble, Displacement), fire/energy (Blaze, Flame Wrap, Force Field, Laser), glass/optics (Glass, Frost, Magnify, Bend, Peel, Clouds), retro/glitch (VHS, Glitch, Retro Dither, Asciify, Decrypt Reveal, Glyph Rain), particles/structure (Particle Reveal, Particle Scroll, Shatter, Grid, Hex Float, Canvas), 3D-объекты работают везде без флага — ASCII Object, Glass Object, Particle Object, Dithered Object, Liquid Object (целятся в GLB/glTF, SVG, картинку)
- Ограничение (важно): HTML-in-canvas требует Chrome с флагом `chrome://flags/#canvas-draw-element` или origin-trial токен; WebGPU-сборки — Chrome/Edge 113+, Safari 26+/iOS 26, Firefox 141+. Без WebGPU обёрнутый контент просто рендерится как есть. 3D-компоненты работают везде
- Куда: Burrow3D, Elite3D, игровые демо, hero-секции лендингов — да. Суды, биллинг, SEO-инструменты — оверхед, туда paper shaders или вообще ничего

## 5. Paper Shaders — БРАТЬ (фоны, zero-dependency)

- Репозиторий: https://github.com/paper-design/shaders
- Живые доки и конструктор: https://shaders.paper.design
- Звезд: 3.7к, форков 160. Лицензия: Apache-2.0 (коммерческое использование без атрибуции; при редистрибуции как части другой шейдер-библиотеки — сохранить LICENSE/NOTICE). Организация: Lost Coast Labs (paper.design)
- Что это: canvas-шейдеры без зависимостей — текстура для фонов или масок под формы/текст, анимированные или статичные, лёгкие и быстрые, широкая поддержка браузеров. Дизайнер крутит визуально в Paper — разработчик забирает лёгким кодом
- Установка: React `npm i @paper-design/shaders-react`, vanilla `npm i @paper-design/shaders`. Зависимость пинить — под 0.0.x возможны breaking changes. Vue и остальные — ждут community PR
- Пример: `import { MeshGradient, DotOrbit } from '@paper-design/shaders-react'` → `<MeshGradient colors={['#5100ff','#00ff80','#ffcc00','#ea00ff']} distortion={1} swirl={0.8} speed={0.2} />`
- Куда: hero-фоны Zavodsvay, Yamobur, FloraMaverick, Sabor, Tulipania — один компонент вместо three.js. Лучший кандидат на «лестницу»: нативная лёгкость вместо библиотеки ради библиотеки

## 6. UI Layouts — ВИТРИНА ИДЕЙ

- В треде: `github.com/ui-layouts/ui-...` — точное имя: https://github.com/ui-layouts/uilayouts (без дефиса)
- Сайт: https://www.ui-layouts.com , все компоненты: https://www.ui-layouts.com/components , лаборатория: https://www.ui-layouts.com/labs
- Звезд: 3.7к, форков 223. Лицензия: MIT. Автор: Naymur (x.com/naymur_dev). Стек: tailwindcss + motion/framer-motion (+ clsx, tailwind-merge, хук useMediaQuery руками)
- Хиты: R3F Blob, Image Ripple, Buy Me Coffee, Youtube Tags, File Upload, Password, Range Slider, Motion Number, Embla Carousel, Sparkles, Drag Items, Timeline Animation, Clip Path Image, Buttons, Image Mousetrail, Image Reveal
- Куда: не ставить целиком — ходить глазами, копировать приём. Image Mousetrail/Reveal — для каталогов Zavodsvay; Motion Number — для счётчиков в дашбордах судов; File Upload — для Court-Viewer/DocuMind

## 7. Hyperiux Components — ПРОПУСТИТЬ (фримиум)

- В треде: `github.com/Hyperiux-Immer...` — **БИТАЯ, такого репо нет (404)**. Настоящий: https://github.com/Hyperiux-Immersion-Labs/hyperiux-components (32 звезды). Витрина: https://vault.hyperiux.com , агентство: https://hyperiux.com
- Что это: 32 бесплатных эффекта (open source) + 83 pro за подпиской Vault Pro. CLI `npx hyperiux` ставит исходники в проект, есть MCP-сервер для агентов (`packages/mcp-server`, в npm на момент проверки ещё не опубликован — только локально)
- Почему пропустить: модель «половина витрины за paywall», звёзд и сообщества в разы меньше, чем у бесплатных аналогов. Всё нужное закрывают motion-primitives + paper shaders без подписки
- Если всё же: `git clone https://github.com/Hyperiux-Immersion-Labs/hyperiux-components && pnpm install && pnpm dev`

## 8. Motion Primitives — БРАТЬ ТОЧЕЧНО (самый зрелый)

- Репозиторий: https://github.com/ibelick/motion-primitives
- Сайт и доки: https://motion-primitives.com , https://motion-primitives.com/docs
- Звезд: 6.7к (больше всех в подборке), форков 287. Лицензия: MIT. Статус: beta, компоненты и breaking updates регулярно. Стек: motion + Tailwind
- Что это: UI-кит красивых анимированных интерфейсов — легко интегрируемые motion-компоненты для инженеров и дизайнеров
- Куда: микроанимации в дашбордах (Court-Viewer, CourtPulse, OpsWatch) — брать по одному компоненту, не весь кит. Для FrontLab/WebForge — держать как референс анимаций

## 9. Cursify — ВИТРИНА ИДЕЙ (курсоры)

- Репозиторий: https://github.com/ui-layouts/cursify
- Сайт: https://cursify.ui-layouts.com
- Звезд: 2.1к, форков 101. Авторы: Durgesh Bachhav + Naymur (та же команда, что ui-layouts). Стек: motion, tailwind
- Что это: библиотека анимаций курсора для React/Next.js — тот же стартер-каркас, что ui-layouts (registry/components: blurvignette, button-хуки, cards, clip-path, footers, scroll-animation)
- Куда: курсорные эффекты — только для маркетинговых страниц (Zavodsvay-лендинги, FloraMaverick). В рабочих инструментах курсорные либы — вредительство для usability, не ставить

## 10. Trickle UI Kit — БРАТЬ (текст, zero-runtime)

- В треде: `github.com/akaieuan/trick...` — **БИТАЯ (404)**. Настоящий: https://github.com/akaieuan/trickle-UI-kit (автор akaieuan, akabuild.dev). Демо/дом проекта: https://akabuild.dev/demo/trickle-ui-kit
- Сайт-каталог: https://tricklekit.dev (интерактивный каталог с твик-панелями и replay, страница установки, audit-роут для QA)
- Звезд: 1. Лицензия: MIT. Статус: v0.1, свежак. Стек: TypeScript 78%, CSS 21%
- Что это: 47 текстовых анимаций на ЧИСТОМ CSS — ноль рантайма, SSR-safe (сервер отдаёт финальный HTML с классами, браузер стартует анимацию на первом paint, без flash и hydration mismatch), медиана <1кб gzip на компонент. Браузер работает, React только дёргает пару стейтов (Typewriter, DecryptScramble, Shatter, Pixel и др.)
- Установка (только shadcn CLI, npm-пакета нет и не будет — регистр и есть дистрибуция): `npx shadcn@latest add https://tricklekit.dev/r/typewriter.json`. Требует Tailwind v4 + инициализированный shadcn. Один вызов тянет транзитивные зависимости (оболочка TextRoot, CSS-переменные, keyframes, reduced-motion override). Исходник твой в момент установки — кастомизируй свободно, апгрейд = перезапуск команды
- Куда: ПЕРВЫЙ кандидат для SEO-проектов (SEO-Zavodsvay, SerpWatcher, StatGladys) — анимация без JS-налога и LCP-штрафов. Заголовки лендингов Zavodsvay/Yamobur. Связка с taste-web-performance

---

## Красивые сайты — сходить глазами

| Сайт | Что там красивого |
|------|-------------------|
| https://shaders.paper.design | интерактивный конструктор шейдеров, крути параметры живьём |
| https://better-design.com/design-systems | 31 тема как каталог вкуса (Linear, Stripe, Cinematic Dark) |
| https://tricklekit.dev | каталог 47 анимаций с твик-панелями и replay |
| https://motion-primitives.com | живые демо анимаций в доке |
| https://canvasui.dev/playground | сравнение 35 эффектов рядом |
| https://www.ui-layouts.com/labs | эксперименты, которых нет в stable |
| https://cursify.ui-layouts.com | курсорные приёмы для лендингов |
| https://vault.hyperiux.com | витрина эффектов (смотреть бесплатно, не покупать) |
| перед/после design-taste | `examples/before.html` vs `after.html` в одном браузере + `gallery/launch-grid.png` |

## Привязка к моим проектам

- Суды и биллинг (Court-Viewer, CourtPulse, CourtDesk, GefestBilling, SberBusiness, TestBuh): better-design (Linear / Corporate Fintech / Precision Light) + design-taste corporate-trust или dark-tech + точечно motion-primitives
- Каталоги и лендинги (Zavodsvay, ZavodsvayCom, Yamobur, FloraMaverick, Sabor): paper shaders фон + trickle заголовки + design-taste quiet-luxury или editorial-minimal
- SEO-инструменты (SEO-Auditor, SEO-Zavodsvay, SerpWatcher, StatGladys): trickle (ноль JS) + taste-web-performance, тяжёлые эффекты запрещены
- 3D и игры (Burrow3D, Elite3D, Game*): canvas-ui 3D-объекты, остальное не тащить
- Генераторы (FrontLab, WebForge, WizardMD, DOCX-Builder): design-taste в opencode один раз — дальше каждый генерируемый сайт наследует вкус

## Что установить прямо сейчас (минимум)

```bash
git clone https://github.com/madebymustafa/design-taste.git
cd design-taste && ./scripts/install.sh && ./scripts/validate.sh
```

Дальше по требованию: `npx shadcn@latest add https://tricklekit.dev/r/typewriter.json`, `npm i @paper-design/shaders-react`, темы с better-design.com.
