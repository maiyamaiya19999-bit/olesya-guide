---
name: presentation-full
description: Создаёт HTML-презентацию на весь экран (контент по всей ширине, БЕЗ места под видео) в фирменном стиле Олеси. Слайды 16:9, тёплая бежевая палитра, схемки-вариации, экспорт в PDF. Вызывай, когда Олеся просит полноэкранные слайды без зоны под видео.
---

# Скилл: Полноэкранная презентация Олеси (без места под видео)

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и **реальный ник** для навбара. Пока ника там нет — пиши `olesya`.
3. Если появился логотип `~/.claude/brand/logo-olesya.png` — используй его вместо монограммы.
4. Границы абсолютны: дети, семья, личные детали близких — на слайдах не появляются.

Когда Олеся просит создать презентацию/слайды БЕЗ зоны под видео (контент на всю ширину) — создай HTML-страницу со слайдами 16:9 в её фирменном стиле.

> Это вариант обычного скилла `presentation`, но **без 60/40 split**. Здесь контент занимает весь экран. Если нужна презентация с пустой правой зоной под видео Олеси — используй `/presentation`.

## Формат

- Каждый слайд — отдельный экран **16:9** (1920×1080).
- Контент занимает **всю ширину**, центрирован по горизонтали и вертикали.
- **Нет** вертикального разделителя и **нет** пустой зоны под видео.
- Навбар — на всю ширину слайда.
- Шрифты крупные (рассчитаны под просмотр слайда целиком, не в колонке).

## Бренд-стиль

### Цвета (из `~/.claude/brand/style-guide.md`)
- Фон: `#FAF7F3`
- Текст: `#2A211C`
- Текст второстепенный: `#5E534C`, `#7A6F67`, `#9A908A`
- Акцент (коричневый): `#7B5A43` — курсивные выделения в заголовках, точки списков, бейджи, цифры
- Серые блоки: `#F1ECE6` — без закруглений, без цветных линий
- Карточки: `#F5F1EC` с рамкой `#E4DCD3` — квадратные углы
- Линии: `#E9E3DC` (разделители), `#EFE9E2` (навбар, списки)
- На тёмном фоне НИКОГДА не использовать коричневый — заменять на `#D9BFA4`

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, курсивные акценты коричневым
- **Основной текст**: `Inter`, sans-serif
- **Декоративные цифры**: `Libre Baskerville`, italic, коричневый (часто opacity 0.3)
- **Ник в навбаре**: `DM Sans`, italic, `#9A908A`

### Навбар (на каждом слайде)
- На всю ширину слайда: **слева** монограмма `<span class="nav__mono">O</span>` (Libre Baskerville italic 28px, цвет акцента), **справа** ник `<span class="nav__logo-name">olesya</span>` (DM Sans italic 17px, `#9A908A`)
- Тонкая линия снизу `#EFE9E2`
- Когда появится логотип — `<img src="logo.png" alt="O">` высотой 38px вместо монограммы

### Бейдж (на титульном слайде)
- Тонкая рамка 1px коричневая, текст капсом, разрядка 2.5px, размер 14px
- Текст: «УРОК», «ГАЙД», «КУРС», «ПРЕЗЕНТАЦИЯ» и т.п.

## Важные правила

1. **Контент на всю ширину** — никакого split, разделителя или пустой зоны.
2. **БЕЗ номеров страниц в навбаре**, но допускается деликатный номер слайда внизу справа (`.slide__number`).
3. **Каждый слайд = один экран 16:9** (1920×1080).
4. **Навбар на каждом слайде** — не sticky, просто повторяется.
5. **Квадратные углы везде** — никаких border-radius.
6. **Контент центрирован** по обеим осям (flexbox), заголовки по центру, тело — левое выравнивание внутри центрированного блока.
7. **Не перегружай слайд** — одна мысль на экран. Контент должен помещаться по высоте без обрезки.
8. **Чередуй типы слайдов** — каждый 2–3-й слайд делай схемкой (цитата, шаги, метрики, чек-лист и т.д.), чтобы было визуально разнообразно.
9. **Claude и reels** — слова «клод» и «рилс» ВСЕГДА пишутся латиницей: **Claude** и **reels**. Никогда кириллицей.
10. **Голос** — по разделу 8 PROFILE.md: на «ты», женский род, короткие фразы, контраст-формулы, без «ворвись/прокачай/изобильная».

---

## Базовые элементы

### Титульный слайд (hero)
```html
<div class="hero">
  <div class="badge">ПРЕЗЕНТАЦИЯ</div>
  <h1>Разреши себе <em>быть видимой</em></h1>
  <p class="hero__desc">Проявленность без аффирмаций: три действия, а не мантра.</p>
  <p class="hero__meta">ПРОЯВЛЕННОСТЬ &middot; БЛОГ С ИИ &middot; ДЕНЬГИ</p>
</div>
```

### Три карточки (часто на титульном или обзорном слайде)
```html
<div class="cards">
  <div class="card">
    <div class="card__num">01.</div>
    <h3 class="card__title">Разрешение</h3>
    <p class="card__text">Состояние, из которого ты показываешься.</p>
  </div>
  <!-- ещё 2 карточки: Инструмент, Результат -->
</div>
```

### Заголовок секции
```html
<h2 class="section-heading">Ты не сотрудник своего блога. <em>Ты его владелец</em></h2>
```

### Серый блок .highlight
```html
<div class="highlight"><strong>Важно:</strong> faceless — не значит невидимый. Faceless — значит свободный от чужих ожиданий.</div>
```

### Список .guide-list
```html
<ul class="guide-list">
  <li><strong>15 минут в день.</strong> Таймер, Claude, один пост.</li>
</ul>
```

### Завершающая фраза .footer-note
```html
<p class="footer-note">Мне страшно — <em>и я всё равно иду</em></p>
```

---

## Схемки-вариации (для разнообразия — каждый 2–3-й слайд)

### Схемка 1: Цитата-акцент
```html
<div class="quote">
  <div class="quote__label">КЛЮЧЕВАЯ МЫСЛЬ</div>
  <div class="quote__mark">&ldquo;</div>
  <div class="quote__text">Ты не устала от работы. <em>Ты устала быть не собой.</em></div>
  <div class="quote__divider"></div>
  <p class="quote__source">Про выгорание, которое лечится не отпуском.</p>
</div>
```

### Схемка 2: Шаги с вертикальной линией
```html
<div class="steps">
  <div class="steps__heading">Блог с нуля — <em>за неделю</em></div>
  <div class="steps__list">
    <div class="steps__item steps__item--active">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Разрешила себе начать</div>
      <div class="steps__item-text">Без идеальной ниши и без «а вдруг осудят».</div>
    </div>
    <div class="steps__item">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Собрала контент-план в Claude</div>
      <div class="steps__item-text">Семь тем за 15 минут.</div>
    </div>
  </div>
</div>
```

### Схемка 3: Нумерованный список
```html
<div class="numlist">
  <div class="numlist__heading">Четыре столпа <em>блога</em></div>
  <div class="numlist__item">
    <div class="numlist__num">1</div>
    <div class="numlist__text"><strong>Разрешение</strong> <span>— состояние, из которого ты показываешься.</span></div>
  </div>
  <div class="numlist__item">
    <div class="numlist__num">2</div>
    <div class="numlist__text"><strong>Инструмент</strong> <span>— блог с ИИ, 15 минут в день.</span></div>
  </div>
</div>
```

### Схемка 4: Акцентная полоса слева
```html
<div class="accent-bar">
  <div class="accent-bar__label">ГЛАВНОЕ ПРАВИЛО</div>
  <div class="accent-bar__block">
    <div class="accent-bar__title">Не жди вдохновения. <em>У ИИ его больше.</em></div>
    <p class="accent-bar__text">Claude пишет первый абзац — дальше ты.</p>
    <div class="accent-bar__footer">Я даю систему, а не подвиг</div>
  </div>
</div>
```

### Схемка 5: Чек-лист (Делай / Не делай)
```html
<div class="checklist">
  <div class="checklist__heading">Продажи в блоге — <em>без впаривания</em></div>
  <div class="checklist__grid">
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--do">Делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Называй цену спокойно</div>
    </div>
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--dont">Не делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>«Последние места, ворвись!»</div>
    </div>
  </div>
</div>
```

### Схемка 6: Три метрики
```html
<div class="metrics">
  <div class="metrics__heading">Сколько это <em>на самом деле</em></div>
  <div class="metrics__row">
    <div class="metrics__item">
      <div class="metrics__number">15</div>
      <div class="metrics__label">минут в день</div>
      <div class="metrics__desc">На пост с ИИ.</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">1</div>
      <div class="metrics__label">тема</div>
      <div class="metrics__desc">А не «про всё сразу».</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">0</div>
      <div class="metrics__label">идеальных постов</div>
      <div class="metrics__desc">Нужно, чтобы начать.</div>
    </div>
  </div>
</div>
```

### Схемка 7: Вопрос-ответ
```html
<div class="qa">
  <div class="qa__heading">Что тебя <em>останавливает</em></div>
  <div class="qa__item">
    <div class="qa__question">А кто, собственно, решил, что мне нельзя?</div>
    <div class="qa__answer">Никто. Это стандарт по умолчанию. Его можно вернуть.</div>
  </div>
</div>
```

### Схемка 8: Формула
```html
<div class="formula">
  <div class="formula__heading">Формула <em>блога</em></div>
  <div class="formula__row">
    <div class="formula__step">
      <div class="formula__step-title">Разрешение</div>
      <div class="formula__step-text">Состояние</div>
    </div>
    <div class="formula__arrow">+</div>
    <div class="formula__step">
      <div class="formula__step-title">Инструмент</div>
      <div class="formula__step-text">Блог с ИИ, 15 минут</div>
    </div>
    <div class="formula__arrow">=</div>
    <div class="formula__result">
      <div class="formula__step-title">Результат</div>
      <div class="formula__step-text">Деньги и свобода</div>
    </div>
  </div>
  <p class="formula__note">Без первого слагаемого второе не работает.</p>
</div>
```

---

## Полный CSS (копировать целиком)

```css
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #FAF7F3; --text: #2A211C; --muted: #5E534C; --muted-2: #7A6F67; --muted-3: #9A908A; --faint: #BFB5AD;
  --accent: #7B5A43; --accent-dark: #D9BFA4;
  --block: #F1ECE6; --card: #F5F1EC; --card-border: #E4DCD3; --tip: #ECE5DD; --line: #E9E3DC; --nav-line: #EFE9E2;
}

@page { size: 1920px 1080px; margin: 0; }

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 24px;
  line-height: 1.7;
  -webkit-font-smoothing: antialiased;
}

.slide {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  page-break-after: always;
  position: relative;
  background: var(--bg);
}

/* Навбар на всю ширину */
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 22px 64px;
  border-bottom: 1px solid var(--nav-line);
  background: var(--bg);
  flex-shrink: 0;
}
.nav__logo { text-decoration: none; display: flex; align-items: center; }
.nav__logo img { height: 38px; width: auto; }
.nav__mono {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 28px; line-height: 38px;
  color: var(--accent);
}
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 17px; font-weight: 400; font-style: italic;
  color: var(--muted-3); letter-spacing: 0.5px;
}

/* Тело слайда — центр по обеим осям */
.slide__body {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 56px 80px;
}
.slide__inner {
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
}

/* Деликатный номер слайда */
.slide__number {
  position: absolute; bottom: 32px; right: 64px;
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 18px; color: var(--faint);
}

/* ===== ТИТУЛЬНЫЙ (HERO) ===== */
.hero { text-align: center; }
.badge {
  display: inline-block; font-size: 14px; font-weight: 600;
  color: var(--accent); border: 1px solid var(--accent);
  padding: 7px 20px; margin-bottom: 40px;
  letter-spacing: 2.5px; text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 64px; font-weight: 700; line-height: 1.3;
  max-width: 1200px; margin: 0 auto 32px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 26px; color: var(--muted-2); line-height: 1.7; max-width: 900px; margin: 0 auto; }
.hero__meta { font-size: 18px; color: var(--muted-3); margin-top: 24px; letter-spacing: 1px; }

/* ===== ТРИ КАРТОЧКИ ===== */
.cards {
  display: grid; grid-template-columns: repeat(3, 1fr);
  gap: 40px; max-width: 1280px; width: 100%; margin: 48px auto 0;
}
.card { background: var(--card); border: 1px solid var(--card-border); padding: 40px; }
.card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 19px; color: var(--accent); margin-bottom: 16px;
}
.card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 27px; font-weight: 700; line-height: 1.4; margin-bottom: 16px;
}
.card__text { font-size: 19px; color: var(--muted-2); line-height: 1.7; }

/* ===== БАЗОВЫЕ ЭЛЕМЕНТЫ ===== */
.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 36px;
}
.section-heading em { font-style: italic; color: var(--accent); }

.text { font-size: 24px; color: var(--muted); line-height: 1.75; margin-bottom: 20px; }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 30px; font-weight: 700; margin: 32px 0 14px;
}

.highlight {
  background: var(--block); padding: 28px 32px; margin: 28px 0;
  font-size: 22px; line-height: 1.7; color: var(--muted);
}
.highlight strong { color: var(--text); }

.guide-list { list-style: none; margin: 16px 0; }
.guide-list li {
  font-size: 22px; line-height: 1.7; color: var(--muted);
  padding: 14px 0 14px 28px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 24px;
  width: 7px; height: 7px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: var(--text); }

.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 32px; font-style: italic; color: var(--muted);
  text-align: center;
}
.footer-note em { color: var(--accent); }

/* ===== СХЕМКА 1: ЦИТАТА ===== */
.quote { max-width: 1000px; margin: 0 auto; text-align: center; }
.quote__label {
  font-size: 14px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2.5px; text-transform: uppercase; margin-bottom: 32px;
}
.quote__mark {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 120px; color: var(--accent); line-height: 0.5;
  margin-bottom: 24px; opacity: 0.3;
}
.quote__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 40px; font-style: italic; line-height: 1.5;
  color: var(--text); margin-bottom: 32px;
}
.quote__text em { color: var(--accent); }
.quote__divider { width: 56px; height: 2px; background: var(--accent); margin: 0 auto 24px; }
.quote__source { font-size: 20px; color: var(--muted-3); line-height: 1.6; }

/* ===== СХЕМКА 2: ШАГИ ===== */
.steps { max-width: 1000px; margin: 0 auto; }
.steps__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 44px;
}
.steps__heading em { font-style: italic; color: var(--accent); }
.steps__list { position: relative; padding-left: 44px; }
.steps__list::before {
  content: ''; position: absolute; left: 10px; top: 12px; bottom: 12px;
  width: 1px; background: var(--line);
}
.steps__item { position: relative; padding-bottom: 32px; }
.steps__item:last-child { padding-bottom: 0; }
.steps__dot {
  position: absolute; left: -44px; top: 4px;
  width: 21px; height: 21px; border: 2px solid var(--accent);
  background: var(--bg); border-radius: 50%;
}
.steps__item--active .steps__dot { background: var(--accent); }
.steps__item-title { font-weight: 600; font-size: 24px; color: var(--text); margin-bottom: 6px; }
.steps__item-text { font-size: 20px; color: var(--muted-2); line-height: 1.6; }

/* ===== СХЕМКА 3: НУМЕРОВАННЫЙ СПИСОК ===== */
.numlist { max-width: 1000px; margin: 0 auto; }
.numlist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 44px;
}
.numlist__heading em { font-style: italic; color: var(--accent); }
.numlist__item {
  display: flex; gap: 32px; align-items: baseline;
  padding: 22px 0; border-bottom: 1px solid var(--nav-line);
}
.numlist__item:last-child { border-bottom: none; }
.numlist__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 56px; color: var(--accent); opacity: 0.3;
  min-width: 72px; text-align: right; line-height: 1; flex-shrink: 0;
}
.numlist__text { font-size: 23px; color: var(--text); line-height: 1.6; }
.numlist__text strong { font-weight: 600; }
.numlist__text span { color: var(--muted-2); }

/* ===== СХЕМКА 4: АКЦЕНТНАЯ ПОЛОСА ===== */
.accent-bar { max-width: 1000px; margin: 0 auto; }
.accent-bar__label {
  font-size: 14px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2.5px; text-transform: uppercase; margin-bottom: 28px;
}
.accent-bar__block { border-left: 4px solid var(--accent); padding-left: 40px; }
.accent-bar__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 40px; font-weight: 700; line-height: 1.35; margin-bottom: 20px;
}
.accent-bar__title em { font-style: italic; color: var(--accent); }
.accent-bar__text { font-size: 22px; color: var(--muted); line-height: 1.75; margin-bottom: 24px; }
.accent-bar__footer {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-style: italic; color: var(--muted-3);
  padding-top: 20px; border-top: 1px solid var(--nav-line);
}

/* ===== СХЕМКА 5: ЧЕК-ЛИСТ ===== */
.checklist { max-width: 1100px; margin: 0 auto; }
.checklist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 40px;
}
.checklist__heading em { font-style: italic; color: var(--accent); }
.checklist__grid { display: grid; grid-template-columns: 1fr 1fr; }
.checklist__col-label {
  font-size: 14px; font-weight: 600; letter-spacing: 1.5px;
  text-transform: uppercase; padding-bottom: 18px; margin-bottom: 14px;
  border-bottom: 1px solid var(--line);
}
.checklist__col-label--do { color: var(--accent); }
.checklist__col-label--dont { color: var(--muted-3); }
.checklist__col:first-child { padding-right: 32px; border-right: 1px solid var(--nav-line); }
.checklist__col:last-child { padding-left: 32px; }
.checklist__item {
  display: flex; gap: 14px; padding: 12px 0;
  font-size: 21px; color: var(--muted); line-height: 1.6; align-items: baseline;
}
.checklist__mark { flex-shrink: 0; font-size: 20px; font-weight: 700; width: 22px; }
.checklist__mark--do { color: var(--accent); }
.checklist__mark--dont { color: var(--faint); }

/* ===== СХЕМКА 6: МЕТРИКИ ===== */
.metrics { max-width: 1200px; margin: 0 auto; }
.metrics__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 44px;
}
.metrics__heading em { font-style: italic; color: var(--accent); }
.metrics__row { display: grid; grid-template-columns: 1fr 1fr 1fr; }
.metrics__item { text-align: center; padding: 32px 20px; border-right: 1px solid var(--nav-line); }
.metrics__item:last-child { border-right: none; }
.metrics__number {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 72px; color: var(--accent); opacity: 0.3;
  line-height: 1; margin-bottom: 12px;
}
.metrics__label { font-size: 16px; color: var(--muted-3); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 10px; }
.metrics__desc { font-size: 19px; color: var(--muted-2); line-height: 1.5; }

/* ===== СХЕМКА 7: ВОПРОС-ОТВЕТ ===== */
.qa { max-width: 1000px; margin: 0 auto; }
.qa__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 40px;
}
.qa__heading em { font-style: italic; color: var(--accent); }
.qa__item { margin-bottom: 32px; }
.qa__question {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 26px; font-style: italic; color: var(--accent);
  margin-bottom: 12px; padding-left: 48px; position: relative;
}
.qa__question::before {
  content: '?'; position: absolute; left: 0; top: -6px;
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 40px; color: var(--accent); opacity: 0.3;
}
.qa__answer { font-size: 22px; color: var(--muted); line-height: 1.7; padding-left: 48px; border-left: 1px solid var(--line); }

/* ===== СХЕМКА 8: ФОРМУЛА ===== */
.formula { max-width: 1200px; margin: 0 auto; }
.formula__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 46px; font-weight: 700; line-height: 1.3;
  text-align: center; margin-bottom: 40px;
}
.formula__heading em { font-style: italic; color: var(--accent); }
.formula__row { display: flex; align-items: center; gap: 24px; margin-bottom: 28px; }
.formula__step { flex: 1; background: var(--block); padding: 28px 22px; text-align: center; }
.formula__step-title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 22px; font-weight: 700; margin-bottom: 6px;
}
.formula__step-text { font-size: 17px; color: var(--muted-2); line-height: 1.5; }
.formula__arrow { color: var(--accent); font-size: 26px; flex-shrink: 0; opacity: 0.5; }
.formula__result { border: 1px solid var(--accent); padding: 28px 22px; text-align: center; flex: 1; }
.formula__result .formula__step-title { color: var(--accent); }
.formula__note { font-size: 19px; color: var(--muted-3); font-style: italic; text-align: center; margin-top: 12px; }

/* ===== PRINT / PDF ===== */
@media print {
  html, body { width: 1920px; }
  .slide { width: 1920px; height: 1080px; page-break-after: always; page-break-inside: avoid; }
  .slide:last-child { page-break-after: auto; }
  .nav { position: relative; }
  .slide__number { position: absolute; }
  body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}

/* ВАЖНО: мобильные правила только в screen — иначе текут в print и ломают слайды */
@media screen and (max-width: 900px) {
  .nav { padding: 16px 24px; }
  .hero h1 { font-size: 36px; }
  .section-heading, .steps__heading, .numlist__heading,
  .checklist__heading, .metrics__heading, .qa__heading, .formula__heading { font-size: 28px; }
  .cards { grid-template-columns: 1fr; }
  .slide__body { padding: 40px 24px; }
}
```

## Шаблон HTML-слайда

```html
<!-- Титульный слайд -->
<div class="slide">
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">O</span></a>
  <span class="nav__logo-name">olesya</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <div class="hero">
      <div class="badge">ПРЕЗЕНТАЦИЯ</div>
      <h1>Разреши себе <em>быть видимой</em></h1>
      <p class="hero__desc">Проявленность без аффирмаций: три действия, а не мантра.</p>
    </div>
  </div>
</div>
<span class="slide__number">01</span>
</div>

<!-- Контентный слайд -->
<div class="slide">
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">O</span></a>
  <span class="nav__logo-name">olesya</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <h2 class="section-heading">Первый пост не обязан быть шедевром. <em>Он обязан существовать</em></h2>
    <p class="text">Текст слайда.</p>
  </div>
</div>
<span class="slide__number">02</span>
</div>
```

## Как использовать

1. Получи тему/текст от Олеси.
2. Разбей на слайды — одна мысль на экран.
3. Первый слайд — титульный (бейдж + заголовок + описание), часто + три карточки-обзора.
4. Остальные слайды — чередуй базовые (текст, списки) и схемки (цитата, шаги, нумерованный список, акцентная полоса, чек-лист, метрики, вопрос-ответ, формула). Каждый 2–3-й слайд — схемка.
5. Заголовки — по центру, тело — слева внутри центрированного блока.
6. Не перегружай: контент должен влезать в экран без обрезки по высоте.
7. Сохрани как `index.html` в `~/Desktop/олеся/презентации/<slug>/`.

## Экспорт в PDF

Размер страницы задаётся через `@page { size: 1920px 1080px }`, поэтому достаточно:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --no-pdf-header-footer --print-to-pdf="presentation.pdf" \
  "file://$(pwd)/index.html"
```

**ОБЯЗАТЕЛЬНО проверить сам PDF (а не скриншот экрана)** — на экране баги print не видны:

```bash
sips -s format png presentation.pdf --out _check.png
```

Посмотреть глазами: контент на всю ширину, навбар на всю ширину, нет разделителя и пустых зон, ничего не обрезано по высоте, фон тёплый бежевый (не белый). После проверки удалить `_check.png`.
