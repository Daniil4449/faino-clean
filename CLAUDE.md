# Faino Clean — Project Context for Claude

## Що це за проєкт

Сайт клінінгової компанії для бізнесу **Faino Clean** (fainoclean.com.ua), Київ.
Аутсорс-клінінг: офіси, склади, виробничі приміщення, торгові площі, готелі/апартаменти, ЖК.
Працює з 2013 року, у Києві — з 2014-го. ФОП 3 групи, офіційний договір.

Телефон: +380951915964 · Email: cleanandclear4449@gmail.com

**Це окремий, незалежний проєкт** — не форк і не похідна від `Daniil4449/importica`. Деякі інфраструктурні патерни (SEO-теги, GitHub Pages деплой, Formsubmit) підглянуті звідти як перевірений підхід, але дизайн і контент — власні, під затверджену дизайн-систему Faino Clean.

## Файлова структура

```
faino-clean/
├── index.html          ← ЄДИНИЙ файл сайту (весь HTML, CSS, JS всередині)
├── robots.txt
├── sitemap.xml
├── og-image.svg
├── CNAME                ← fainoclean.com.ua
├── CLAUDE.md
├── DEVELOPMENT_LOG.md   ← історія рішень по сесіях, звіряти тут перед новою сесією
├── README.md
└── .github/workflows/deploy.yml
```

## Дизайн-система (не змінювати без явного запиту користувача)

```
--bg: oklch(96.5% 0.012 145)
--bg-alt: oklch(93.5% 0.016 145)
--ink: oklch(24% 0.045 155)
--ink-soft: oklch(38% 0.03 150)
--line: oklch(85% 0.02 150)
--accent: oklch(30% 0.06 155)
--dark: oklch(17% 0.025 155)
--paper: oklch(98% 0.006 100)
```
Заголовки — Playfair Display (500–700), текст — Outfit (300–600). Inter заборонено.
Іконки — тонкі лінійні (stroke ~1.4–1.6px), без кольорових підложок. Без нумерації розділів 01/02/03.
Позиціонування B2B — без "з душею", без емодзі-будиночків, без кітчу (мітли, бульбашки).

## Інфраструктура

| Що | Де / Як |
|----|---------|
| Хостинг | GitHub Pages, репозиторій `faino-clean` |
| Домен | fainoclean.com.ua (реєстратор Imena.ua, DNS → Cloudflare, план) |
| Форма | Formsubmit.co → cleanandclear4449@gmail.com, POST у прихований iframe |
| Аналітика | GA4 — заплановано, ID ще не вставлено |
| Google Sheets / Telegram-бот | Заплановано на Фазу 2–3 (див. DEVELOPMENT_LOG.md) |

## Правила

- Не змінювати дизайн-систему і структуру секцій без прямого запиту користувача
- Нові секції додавати органічно в тому самому стилі
- Зберігати всі SEO meta-теги при будь-яких змінах
- Кожну сесію оновлювати DEVELOPMENT_LOG.md коротким описом змін

## Git / Deploy

```bash
git add index.html
git commit -m "опис змін"
git push origin main
# → GitHub Actions автоматично деплоїть на GitHub Pages
```
