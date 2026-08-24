# Faino Clean — Project Context for Claude

## Що це за проєкт

Сайт клінінгової компанії для бізнесу **Faino Clean** (fainoclean.com.ua), Київ.
Аутсорс-клінінг: офіси, склади, виробничі приміщення, торгові площі, готелі/апартаменти, ЖК.
Працює з 2013 року, у Києві — з 2014-го. ФОП 3 групи, офіційний договір.

Телефон: +380951915964 · Email: cleanandclear4449@gmail.com

**Це окремий, незалежний проєкт** — не форк і не похідна від `Daniil4449/importica`. Деякі інфраструктурні патерни (SEO-теги, GitHub Pages деплой, Formsubmit) підглянуті звідти як перевірений підхід, але дизайн і контент — власні, під затверджену дизайн-систему Faino Clean.

## ⚠️ Правило роботи: усі зміни коду/файлів — тільки через Claude Code

Користувач прямо попросив (сесія 24.08.2026): будь-яку задачу на зміну коду чи файлів виконує Claude Code (ти), а не сам користувач вручну — щоб уникнути помилок. Якщо задача вимагає дій у зовнішніх вебінтерфейсах (Google Analytics, Search Console, Cloudflare dashboard тощо, поза репозиторієм) — це єдиний виняток, там користувач діє сам за покроковою інструкцією.

## ⚠️ Два окремі акаунти Cloudflare — не переплутати

- **daniilka4449@gmail.com** (особиста пошта) → домен **importica.com.ua** (проєкт Importica)
- **cleanandclear4449@gmail.com** (бізнес-пошта Faino Clean) → домен **fainoclean.com.ua**

Той самий поділ і в Google-акаунтах для GA4/Search Console — обидва сервіси Faino Clean підключені на **cleanandclear4449@gmail.com** (той самий Google-акаунт, де вже був ресурс Importica — тобто один акаунт, кілька ресурсів усередині).

## Файлова структура

```
faino-clean/
├── index.html               ← ЄДИНИЙ файл сайту (весь HTML, CSS, JS всередині)
├── logo-green.svg            ← фінальне лого (шапка, hero) — не перемальовувати
├── logo-black.svg            ← запасний варіант, поки не використовується на сайті
├── logo-building-green.svg   ← тільки іконка будівлі (favicon)
├── favicon.svg
├── robots.txt
├── sitemap.xml
├── og-image.svg
├── CNAME                ← fainoclean.com.ua
├── CLAUDE.md
├── context.md           ← знімок стану для Claude.ai Project Knowledge
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
--accent: #1A5E33
--dark: oklch(17% 0.025 155)
--paper: oklch(98% 0.006 100)
```
Заголовки — Playfair Display (500–700), текст — Outfit (300–600). Inter заборонено.
Іконки — тонкі лінійні (stroke ~1.4–1.6px), без кольорових підложок. Без нумерації розділів 01/02/03.
Позиціонування B2B — без "з душею", без емодзі-будиночків, без кітчу (мітли, бульбашки).

## Інфраструктура

| Що | Де / Як |
|----|---------|
| Хостинг | ✅ GitHub Pages, репозиторій `Daniil4449/faino-clean`, auto-deploy |
| Домен | ✅ fainoclean.com.ua повністю підключено — DNS через Cloudflare (акаунт cleanandclear4449@gmail.com) |
| Форма | ✅ Formsubmit.co → cleanandclear4449@gmail.com, POST у прихований iframe |
| Google Sheets | ✅ "Faino Clean — Ліди" через Apps Script webhook — деталі в context.md |
| Аналітика GA4 | ✅ Підключено 24.08.2026. Measurement ID `G-S3F8CCMZS7`, тег gtag.js в `<head>` index.html |
| Google Search Console | ✅ Верифіковано 24.08.2026 (тип ресурсу "Домен"), sitemap.xml надіслано |
| Telegram-бот | ✅ Фаза 3 завершена — нова заявка автоматично створює тему в Telegram-групі, через Make.com |

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
