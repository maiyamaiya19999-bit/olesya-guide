---
name: guide
description: Создаёт HTML-гайд, статью, чек-лист или лендинг гайда в фирменном стиле Олеси (тёплый бежевый фон, Libre Baskerville + Inter, коричневые акценты). Вызывай, когда Олеся просит оформить текст как гайд/статью/чек-лист/лендинг.
---

# Скилл: Оформление текста в фирменный гайд Олеси

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и **реальный ник** для навбара. Пока ника там нет — пиши `olesya`.
3. Если у Олеси уже есть логотип (`~/.claude/brand/logo-olesya.png`) — используй его вместо монограммы (см. «Навбар»).
4. Границы абсолютны: дети, семья, личные детали близких — в гайдах не появляются, даже как пример.

Когда Олеся просит оформить текст как гайд, статью, чек-лист, обучающий материал или лендинг — создай HTML-страницу в её фирменном стиле.

## Бренд-стиль

### Цвета (из `~/.claude/brand/style-guide.md`)
- Фон: `#FAF7F3` (тёплый бежево-белый)
- Текст: `#2A211C` (тёмный кофейно-коричневый)
- Текст второстепенный: `#5E534C`, `#7A6F67`, `#9A908A`
- Акцент (коричневый): `#7B5A43` — используется для: курсивных выделений в заголовках, нумерации, точек в списках, бейджей, заголовка промт-блока, кнопок
- Серые блоки: `#F1ECE6` — без закруглений, без цветных линий слева
- Карточки: `#F5F1EC` с рамкой `#E4DCD3` — квадратные углы
- Советы внутри карточек: `#ECE5DD` — квадратные углы
- Линии-разделители: `#E9E3DC`, тонкие линии навбара и списков: `#EFE9E2`
- Тёмный фон (если нужен): `#2A211C`, на нём акцент — только `#D9BFA4` (песочный)

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, с курсивными акцентами коричневым цветом
- **Основной текст**: `Inter`, sans-serif — 17px, line-height 1.75
- **Подзаголовки**: `Libre Baskerville` — 22px, жирный
- **Нумерация**: `Libre Baskerville` — курсив, коричневый цвет

### Навбар
- Sticky, фон `#FAF7F3`, тонкая линия снизу `#EFE9E2`
- **Слева** — монограмма: `<span class="nav__mono">O</span>` (Libre Baskerville, italic, 22px, цвет акцента)
- **Справа** — ник курсивом: `<span class="nav__logo-name">olesya</span>` (DM Sans, italic, `#9A908A`). Реальный ник — из `~/.claude/brand/style-guide.md`
- `justify-content: space-between` — монограмма и ник на разных краях
- Когда появится логотип `~/.claude/brand/logo-olesya.png` — скопируй его в папку гайда как `logo.png` и замени монограмму на `<img src="logo.png" alt="O">` высотой 30px

### Бейдж
- Тонкая рамка 1px коричневая, текст капсом с разрядкой, размер 11px
- Текст бейджа зависит от контента: «ГАЙД», «УРОК», «СТАТЬЯ», «ЧЕК-ЛИСТ», «МАТЕРИАЛ»

## Структура страницы

```
1. Навбар (sticky): монограмма O слева, ник справа
2. Hero: бейдж + заголовок h1 (с курсивным акцентом) + описание + мета-инфо
3. Intro: жирный тезис + обычный текст
4. Секции (01. 02. 03...): заголовок с нумерацией + контент
5. Внутри секций:
   - Серые блоки .highlight — для ключевых определений
   - Списки .guide-list — с коричневыми точками
   - Промт-блоки .prompt-box — серый фон, заголовок коричневый
   - Нумерованные списки .headline-list — курсивная нумерация
   - Карточки .scenario-card — для сценариев/кейсов/уроков
   - Чек-листы .check-list — квадратные чекбоксы
6. Футер: © год · <ник> · Все права защищены
```

## Правила оформления

1. **Заголовки секций**: `<h2>` с нумерацией `<span>01.</span>` (коричневый) + курсивное слово `<em>` (коричневый)
2. **Подзаголовки**: `<h3>` в Libre Baskerville
3. **Серые блоки**: только `background: var(--block)` — БЕЗ закруглений, БЕЗ цветных линий слева
4. **Карточки**: квадратные углы, рамка `var(--card-border)`, фон `var(--card)`
5. **Советы**: фон `var(--tip)`, квадратные углы, слово «Совет:» коричневым
6. **Промт-блоки**: светлый фон `var(--block)` (НЕ тёмный), заголовок коричневым
7. **На тёмном фоне НИКОГДА не использовать коричневый `#7B5A43`** — он теряется. Вместо него `#D9BFA4`
8. **Адаптивность**: контейнер 740px, на мобильных — уменьшать шрифты
9. **Claude и reels** — слова «клод» и «рилс» ВСЕГДА пишутся латиницей: **Claude** и **reels** (reels — с маленькой буквы). Никогда кириллицей.
10. **Голос** — по разделу 8 PROFILE.md: к читательнице на «ты», женский род, короткие фразы, без инфоцыганских штампов. Заголовки — как её фразы: «Ты не устала от работы. Ты устала быть *не собой*».

## Как использовать

1. Получи текст от Олеси
2. Разбей на логические секции с нумерацией 01, 02, 03...
3. Определи тип контента: списки → `.guide-list`, определения → `.highlight`, пошаговые инструкции → карточки `.scenario-card`, промты → `.prompt-box`, то, что нужно отмечать по ходу → `.check-list`, страница-обёртка с кнопками → «Лендинг гайда»
4. Собери HTML по шаблону ниже (CSS копируй целиком)
5. Сохрани как `~/Desktop/олеся/гайды/<slug>/index.html` (slug — латиницей, через дефис: `razreshi`, `blog-s-nulya`). Картинки — в ту же папку
6. Предложи Олесе опубликовать на её GitHub Pages: репозиторий `<её-логин>.github.io` (или отдельный репозиторий с Pages), папка `guides/<slug>/index.html` → адрес `https://<её-логин>.github.io/guides/<slug>/`. Публиковать — только после её «да»

## Шаблон HTML

```html
<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Название гайда</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
<style>/* полный CSS ниже */</style>
</head>
<body>
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">O</span></a>
  <span class="nav__logo-name">olesya</span>
</nav>
<div class="container">
  <header class="hero">
    <div class="badge">Гайд</div>
    <h1>Блог с нуля за 15 минут в день — <em>с ИИ</em></h1>
    <p class="hero__desc">Как начать вести блог, если нет времени, идей и «правильной» ниши.</p>
    <p class="hero__meta">15 МИНУТ ЧТЕНИЯ &middot; ДЛЯ НАЧИНАЮЩИХ</p>
  </header>

  <p class="intro-bold">Первый пост не обязан быть шедевром. Он обязан существовать.</p>
  <p class="intro-text">Здесь — система, а не подвиг. Три шага, которые можно пройти сегодня вечером.</p>

  <h2 class="section-heading"><span>01.</span> Разреши себе <em>начать</em></h2>
  <div class="highlight"><strong>Разрешение</strong> — это не аффирмация. Это поведение: открыла Claude, написала первый пост, опубликовала.</div>
  <ul class="guide-list">
    <li><strong>Не жди идеальной ниши.</strong> Философы веками не знали свою нишу, и ничего, справились.</li>
    <li><strong>Не жди вдохновения.</strong> У ИИ его больше.</li>
  </ul>

  <p class="footer-note">Мне страшно — <em>и я всё равно иду</em>.</p>
</div>
<footer class="footer">&copy; 2026 &middot; olesya &middot; Все права защищены</footer>
</body>
</html>
```

## Чек-лист (вариант оформления)

Для материалов, которые нужно отмечать по ходу: «что сделать до первого поста», «проверь перед публикацией». Бейдж — «ЧЕК-ЛИСТ». Чекбоксы — квадратные, рамка коричневая, без скруглений. Пункт можно пометить как уже выполненный классом `is-done` (заливка акцентом + галочка).

```html
<h2 class="section-heading"><span>02.</span> Перед первым <em>постом</em></h2>
<ul class="check-list">
  <li>Выбрала одну тему, а не «про всё»</li>
  <li>Написала в Claude: «Помоги мне сформулировать, о чём мой блог, в трёх предложениях»</li>
  <li class="is-done">Разрешила себе не быть идеальной</li>
  <li>Поставила таймер на 15 минут и опубликовала первый пост</li>
</ul>
```

Правила: одна мысль на пункт, начинать с глагола в женском роде прошедшего времени («выбрала», «написала») или с инфинитива — но не смешивать в одном списке. В конце чек-листа — одна сильная строка `.footer-note`.

## Лендинг гайда

Одностраничная обёртка: hero с кнопками + 2–3 коротких блока «что внутри» + финальная кнопка. Используется, когда гайд отдаётся по кнопке (ссылка на PDF, Telegram, другой гайд) или как страница-вход.

Кнопки — квадратные, две вариации:
- `.btn` — основная: фон акцента `#7B5A43`, белый текст
- `.btn.btn--secondary` — вторичная: прозрачный фон, рамка 1px акцента, текст акцентом

```html
<header class="hero hero--landing">
  <div class="badge">Гайд</div>
  <h1>Разреши себе <em>быть видимой</em></h1>
  <p class="hero__desc">Гайд о проявленности без аффирмаций: как перестать ждать разрешения и начать показываться — прямо сейчас, такая, какая есть.</p>
  <div class="hero__actions">
    <a class="btn" href="#">Забрать гайд</a>
    <a class="btn btn--secondary" href="#">Читать онлайн</a>
  </div>
  <p class="hero__meta">БЕСПЛАТНО &middot; 12 СТРАНИЦ &middot; ЧИТАТЬ 10 МИНУТ</p>
</header>

<div class="landing-grid">
  <div class="landing-card">
    <div class="landing-card__num">01.</div>
    <div class="landing-card__title">Кто решил, что тебе нельзя</div>
    <p class="landing-card__text">Откуда берётся «мне ещё рано» и почему это не про тебя.</p>
  </div>
  <div class="landing-card">
    <div class="landing-card__num">02.</div>
    <div class="landing-card__title">Разрешение как поведение</div>
    <p class="landing-card__text">Не мантра, а три действия на сегодня.</p>
  </div>
  <div class="landing-card">
    <div class="landing-card__num">03.</div>
    <div class="landing-card__title">Деньги как разрешение</div>
    <p class="landing-card__text">Почему первый продукт — это тоже про «мне можно».</p>
  </div>
</div>

<div class="cta">
  <p class="cta__text">Ты не сотрудник своего блога. <em>Ты его владелец.</em></p>
  <a class="btn" href="#">Забрать гайд</a>
</div>
```

Правила лендинга: одна главная кнопка на экран (вторичная — рядом, не третья), ссылки — реальные (Telegram, файл, другой гайд), текст кнопки — глагол («Забрать», «Читать», «Открыть»), никаких «Ворваться» и «Залетай».

## Полный CSS (копировать целиком)

```css
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #FAF7F3; --text: #2A211C; --muted: #5E534C; --muted-2: #7A6F67; --muted-3: #9A908A; --faint: #BFB5AD;
  --accent: #7B5A43; --accent-dark: #D9BFA4;
  --block: #F1ECE6; --card: #F5F1EC; --card-border: #E4DCD3; --tip: #ECE5DD; --line: #E9E3DC; --nav-line: #EFE9E2;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 17px;
  line-height: 1.75;
  -webkit-font-smoothing: antialiased;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 48px;
  border-bottom: 1px solid var(--nav-line);
  position: sticky;
  top: 0;
  background: var(--bg);
  z-index: 100;
}
.nav__logo {
  text-decoration: none;
  display: flex;
  align-items: center;
}
.nav__logo img { height: 30px; width: auto; }
.nav__mono {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic;
  font-size: 22px;
  line-height: 30px;
  color: var(--accent);
}
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
  font-style: italic;
  color: var(--muted-3);
  letter-spacing: 0.5px;
}

.container { max-width: 740px; margin: 0 auto; padding: 0 24px; }

.hero { padding: 60px 0 48px; }
.badge {
  display: inline-block;
  font-size: 11px;
  font-weight: 600;
  color: var(--accent);
  border: 1px solid var(--accent);
  padding: 5px 16px;
  margin-bottom: 20px;
  letter-spacing: 2px;
  text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 38px;
  font-weight: 700;
  line-height: 1.25;
  margin-bottom: 16px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 18px; color: var(--muted-2); line-height: 1.7; }
.hero__meta { font-size: 14px; color: var(--muted-3); margin-top: 16px; letter-spacing: 1px; }

.intro-bold {
  font-size: 18px;
  font-weight: 700;
  line-height: 1.65;
  color: var(--text);
  padding: 40px 0 16px;
}
.intro-text {
  font-size: 17px;
  color: var(--muted);
  line-height: 1.75;
  padding-bottom: 48px;
}

.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 30px;
  font-weight: 700;
  line-height: 1.3;
  padding: 56px 0 24px;
  border-top: 1px solid var(--line);
}
.section-heading span { color: var(--accent); margin-right: 8px; }
.section-heading em { font-style: italic; color: var(--accent); }

.highlight {
  background: var(--block);
  padding: 20px 24px;
  margin: 24px 0;
  font-size: 16px;
  line-height: 1.75;
  color: var(--muted);
}
.highlight strong { color: var(--text); }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 22px;
  font-weight: 700;
  padding: 36px 0 16px;
}

.text { font-size: 17px; color: var(--muted); line-height: 1.75; margin-bottom: 16px; }

.guide-list { list-style: none; margin: 16px 0 24px; }
.guide-list li {
  font-size: 16px; line-height: 1.75; color: var(--muted);
  padding: 8px 0 8px 20px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 16px;
  width: 6px; height: 6px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: var(--text); }

.prompt-box {
  background: var(--block);
  padding: 36px;
  margin: 32px 0;
}
.prompt-box__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700;
  color: var(--accent);
  margin-bottom: 6px;
}
.prompt-box__subtitle { font-size: 13px; color: var(--muted-3); margin-bottom: 20px; }
.prompt-box__text { font-size: 15px; line-height: 1.8; color: var(--muted); }

.headline-list { list-style: none; margin: 16px 0 32px; }
.headline-list li {
  display: flex; gap: 16px; padding: 16px 0;
  border-bottom: 1px solid var(--nav-line); align-items: baseline;
}
.headline-list li:first-child { border-top: 1px solid var(--nav-line); }
.headline-num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 15px;
  color: var(--accent); min-width: 28px; flex-shrink: 0;
}
.headline-text { font-size: 17px; line-height: 1.6; color: var(--text); font-weight: 500; }

.scenario-card {
  border: 1px solid var(--card-border);
  padding: 32px; margin: 24px 0; background: var(--card);
}
.scenario-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 14px;
  color: var(--accent); letter-spacing: 1px; margin-bottom: 8px;
}
.scenario-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700; line-height: 1.4; margin-bottom: 20px;
}
.scenario-card__point { margin-bottom: 14px; }
.scenario-card__point-label { font-weight: 600; font-size: 16px; color: var(--text); }
.scenario-card__point-text { font-size: 15px; color: var(--muted-2); line-height: 1.7; }
.scenario-card__ending {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--text);
  padding-top: 16px; margin-top: 16px; border-top: 1px solid var(--card-border);
}
.scenario-card__tip {
  background: var(--tip); padding: 14px 18px; margin-top: 16px;
  font-size: 14px; color: var(--muted); line-height: 1.65;
}
.scenario-card__tip strong { color: var(--accent); }

/* ===== ЧЕК-ЛИСТ ===== */
.check-list { list-style: none; margin: 16px 0 32px; }
.check-list li {
  font-size: 16px; line-height: 1.75; color: var(--text);
  padding: 12px 0 12px 36px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.check-list li:last-child { border-bottom: none; }
.check-list li::before {
  content: ''; position: absolute; left: 0; top: 17px;
  width: 16px; height: 16px;
  border: 1.5px solid var(--accent); background: var(--bg);
}
.check-list li.is-done { color: var(--muted-2); }
.check-list li.is-done::before { background: var(--accent); }
.check-list li.is-done::after {
  content: ''; position: absolute; left: 5px; top: 20px;
  width: 5px; height: 9px;
  border-right: 2px solid var(--bg); border-bottom: 2px solid var(--bg);
  transform: rotate(45deg);
}

/* ===== ЛЕНДИНГ: КНОПКИ, HERO, КАРТОЧКИ, CTA ===== */
.btn {
  display: inline-block;
  font-family: 'Inter', sans-serif;
  font-size: 14px; font-weight: 600;
  letter-spacing: 1px; text-transform: uppercase;
  text-decoration: none;
  padding: 14px 28px;
  background: var(--accent); color: #fff;
  border: 1px solid var(--accent);
  transition: background .15s ease;
}
.btn:hover { background: #66493A; border-color: #66493A; }
.btn--secondary { background: transparent; color: var(--accent); }
.btn--secondary:hover { background: var(--block); border-color: var(--accent); }

.hero--landing { padding: 80px 0 56px; }
.hero--landing h1 { font-size: 44px; }
.hero__actions { display: flex; gap: 12px; flex-wrap: wrap; margin-top: 28px; }

.landing-grid {
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px;
  margin: 24px 0 48px;
}
.landing-card { background: var(--card); border: 1px solid var(--card-border); padding: 24px; }
.landing-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 14px; color: var(--accent); margin-bottom: 10px;
}
.landing-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-weight: 700; line-height: 1.4; margin-bottom: 10px;
}
.landing-card__text { font-size: 14px; color: var(--muted-2); line-height: 1.65; }

.cta {
  background: var(--block); padding: 48px 32px; margin: 48px 0 0; text-align: center;
}
.cta__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 22px; font-style: italic; color: var(--text); margin-bottom: 24px; line-height: 1.5;
}
.cta__text em { color: var(--accent); }

.footer {
  text-align: center; padding: 64px 24px;
  border-top: 1px solid var(--line); margin-top: 64px;
  color: var(--muted-3); font-size: 14px;
}
.footer .tiny {
  font-size: 12.5px; color: var(--faint); max-width: 52ch;
  margin: 12px auto 0; line-height: 1.6; letter-spacing: 0;
}
.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 18px; font-style: italic; color: var(--muted);
  text-align: center; padding: 48px 24px 0;
}
.footer-note em { color: var(--accent); }

/* только screen — чтобы мобильные правила не текли в print/PDF */
@media screen and (max-width: 768px) {
  .nav { padding: 16px 20px; }
  .hero h1, .hero--landing h1 { font-size: 28px; }
  .section-heading { font-size: 24px; }
  .scenario-card { padding: 20px; }
  .prompt-box { padding: 24px; }
  .landing-grid { grid-template-columns: 1fr; }
  .hero__actions .btn { width: 100%; text-align: center; }
}
```
