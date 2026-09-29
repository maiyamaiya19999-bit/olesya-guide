---
name: presentation
description: Создаёт HTML-презентацию для видеоуроков в фирменном стиле Олеси (60/40 split — правые 40% под видео, тёплая бежевая палитра, 8 схемок-вариаций, экспорт в PDF). Вызывай, когда Олеся просит слайды/презентацию к видеоуроку.
---

# Скилл: Оформление презентации для видеоуроков Олеси

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и **реальный ник** для навбара. Пока ника там нет — пиши `olesya`.
3. Если появился логотип `~/.claude/brand/logo-olesya.png` — используй его вместо монограммы.
4. Границы абсолютны: дети, семья, личные детали близких — на слайдах не появляются.

Когда Олеся просит создать презентацию, слайды или материал для видеоурока — создай HTML-страницу со слайдами в её фирменном стиле.

## Формат

Это **презентация для видеоуроков**. Каждый слайд — отдельный экран 100vh. Макет разделён вертикально:
- **Левые 60%** — зона контента (текст, списки, карточки)
- **Правые 40%** — пустая зона под видео (туда в монтаже вставляется видео Олеси)
- Между ними — тонкая вертикальная линия-разделитель `#E9E3DC`

Правая часть ВСЕГДА пустая. Никогда не размещай туда контент.

## Бренд-стиль

### Цвета (из `~/.claude/brand/style-guide.md`)
- Фон: `#FAF7F3`
- Текст: `#2A211C`
- Текст второстепенный: `#5E534C`, `#7A6F67`, `#9A908A`
- Акцент (коричневый): `#7B5A43` — для курсивных выделений в заголовках, точек в списках, бейджей, цифр
- Серые блоки: `#F1ECE6` — без закруглений, без цветных линий
- Карточки: `#F5F1EC` с рамкой `#E4DCD3` — квадратные углы
- Советы в карточках: `#ECE5DD`
- Линии: `#E9E3DC` (разделители), `#EFE9E2` (навбар, списки)
- На тёмном фоне НИКОГДА не использовать коричневый — заменять на `#D9BFA4`

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, с курсивными акцентами коричневым
- **Основной текст**: `Inter`, sans-serif — 16px, line-height 1.75
- **Подзаголовки**: `Libre Baskerville` — 20px, жирный
- **Декоративные цифры**: `Libre Baskerville`, italic, opacity 0.3, цвет `#7B5A43` — для нумерованных списков и метрик
- **Ник в навбаре**: `DM Sans`, italic, `#9A908A`

### Навбар (на каждом слайде)
- Ширина = 60% (только зона контента)
- **Слева** — монограмма `<span class="nav__mono">O</span>` (Libre Baskerville italic 22px, цвет акцента)
- **Справа** — ник `<span class="nav__logo-name">olesya</span>` (DM Sans italic 14px, `#9A908A`, `margin-right: 8px`)
- Тонкая линия снизу `#EFE9E2`
- Когда появится логотип — `<img src="logo.png" alt="O">` высотой 30px вместо монограммы

### Бейдж (на титульном слайде)
- Тонкая рамка 1px коричневая, текст капсом, разрядка 2px, размер 11px
- Текст: «УРОК», «ГАЙД», «КУРС» и т.п.

## Структура слайдов

### Слайд 1 — Титульный
```
Навбар
Бейдж «УРОК»
Заголовок h1 (Libre Baskerville, 36px, с курсивным акцентом коричневым)
Описание (Inter, 17px, #7A6F67)
Мета-инфо (13px, #9A908A, с разрядкой)
```

### Слайды 2+ — Контентные
```
Навбар
Заголовок h2 (Libre Baskerville, 28px) — БЕЗ нумерации
Контент: текст, списки, блоки, карточки, схемки
```

## Важные правила

1. **БЕЗ нумерации** — никаких 01., 02., 03. в заголовках слайдов
2. **БЕЗ номеров страниц** — никаких «1 / 21» внизу
3. **Контент только в левых 60%** — правая часть всегда пустая
4. **Каждый слайд = 100vh** — один экран
5. **Навбар на каждом слайде** — не sticky, просто повторяется
6. **Квадратные углы везде** — никаких border-radius
7. **max-width: 580px** для внутреннего контента слайда
8. **Контент вертикально по центру** слайда (flexbox align-items: center)
9. **Чередуй типы слайдов** — не делай 5 одинаковых слайдов подряд. Разбавляй базовые слайды (текст, списки) схемками (цитаты, метрики, чек-листы, формулы и т.д.). Каждый 2–3-й слайд должен быть схемкой, чтобы презентация была визуально разнообразной и интересной.
10. **Claude и reels** — слова «клод» и «рилс» ВСЕГДА пишутся латиницей: **Claude** и **reels**. Никогда кириллицей.
11. **Голос** — по разделу 8 PROFILE.md: на «ты», женский род, короткие фразы, контраст-формулы («не про X, а про Y»), без «ворвись/прокачай/изобильная».

---

## Базовые элементы контента

### Заголовок секции
```html
<h2 class="section-heading">Ты не устала от работы. Ты устала быть <em>не собой</em></h2>
```
Слово или фраза в `<em>` выделяется курсивом и коричневым цветом.

### Серый блок .highlight
Для ключевых мыслей, выводов, важных замечаний.
```html
<div class="highlight"><strong>Важно:</strong> разрешение — это не аффирмация. Это поведение.</div>
```

### Список .guide-list
С коричневыми точками, разделителями между пунктами.
```html
<ul class="guide-list">
  <li><strong>15 минут в день.</strong> Не «когда будет время», а таймер и один пост.</li>
</ul>
```

### Подзаголовок .sub-heading
```html
<h3 class="sub-heading">Подзаголовок</h3>
```

### Карточка .scenario-card
Для сценариев, кейсов, примеров.
```html
<div class="scenario-card">
  <div class="scenario-card__num">ПРИМЕР</div>
  <div class="scenario-card__title">Faceless-блог за вечер</div>
  <div class="scenario-card__point">
    <span class="scenario-card__point-label">Шаг.</span>
    <span class="scenario-card__point-text">Открыла Claude, описала тему в трёх предложениях.</span>
  </div>
  <div class="scenario-card__tip"><strong>Совет:</strong> первый пост не обязан быть шедевром. Он обязан существовать.</div>
</div>
```

### Завершающая фраза .footer-note
Курсивная фраза Libre Baskerville для финального слайда.
```html
<p class="footer-note">Мне страшно — <em>и я всё равно иду</em></p>
```

---

## Схемки-вариации (8 типов)

Используй эти схемки для разнообразия. Чередуй их с базовыми слайдами — каждый 2–3-й слайд должен быть одной из этих схемок. Выбирай тип по смыслу контента.

### Схемка 1: Цитата-акцент
Для ключевых мыслей, ярких высказываний, выводов.
```html
<div class="slide__inner">
  <div class="quote-slide__label">КЛЮЧЕВАЯ МЫСЛЬ</div>
  <div class="quote-slide__mark">&ldquo;</div>
  <div class="quote-slide__text">Автопилот — отличная вещь для самолёта. <em>Для жизни — катастрофа.</em></div>
  <div class="quote-slide__divider"></div>
  <p class="quote-slide__source">О том, почему «правильная» жизнь по чужому сценарию заканчивается выгоранием.</p>
</div>
```

### Схемка 2: Шаги с вертикальной линией
Для пошаговых процессов, путей, последовательностей. Точки: заполненные = пройденные (`steps__item--active`), пустые = предстоящие.
```html
<div class="slide__inner">
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
Для пронумерованных пунктов, анатомий, структур. Цифры — крупные, Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
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
Для главных правил, ключевых принципов, важных мыслей с пояснением.
```html
<div class="slide__inner">
  <div class="accent-bar__label">ГЛАВНОЕ ПРАВИЛО</div>
  <div class="accent-bar__block">
    <div class="accent-bar__title">Не жди вдохновения. <em>У ИИ его больше.</em></div>
    <p class="accent-bar__text">Вдохновение приходит после первого абзаца, а не до. Claude пишет первый абзац за тебя — дальше ты.</p>
    <div class="accent-bar__footer">Я даю систему, а не подвиг</div>
  </div>
</div>
```

### Схемка 5: Чек-лист (Делай / Не делай)
Для сравнений, правильного и неправильного подхода, do/don't.
```html
<div class="slide__inner">
  <div class="checklist__heading">Продажи в блоге — <em>без впаривания</em></div>
  <div class="checklist__grid">
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--do">Делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Показывай процесс и результат</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Называй цену спокойно</div>
    </div>
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--dont">Не делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>«Последние места, ворвись!»</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>Извиняться за продажу</div>
    </div>
  </div>
</div>
```

### Схемка 6: Три метрики
Для цифр, статистики, ключевых показателей. Цифры — Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
  <div class="metrics__heading">Сколько это <em>на самом деле</em></div>
  <div class="metrics__row">
    <div class="metrics__item">
      <div class="metrics__number">15</div>
      <div class="metrics__label">минут в день</div>
      <div class="metrics__desc">Столько нужно на пост с ИИ.</div>
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
Для FAQ, частых вопросов, разбора сомнений. Знаки `?` — Libre Baskerville 28px italic.
```html
<div class="slide__inner">
  <div class="qa__heading">Что тебя <em>останавливает</em></div>
  <div class="qa__item">
    <div class="qa__question">А кто, собственно, решил, что мне нельзя?</div>
    <div class="qa__answer">Никто. Это стандарт, который ты приняла по умолчанию. Его можно вернуть.</div>
  </div>
  <div class="qa__item">
    <div class="qa__question">Мне нечего сказать — какая у меня ниша?</div>
    <div class="qa__answer">Философы веками не знали свою нишу, и ничего, справились.</div>
  </div>
</div>
```

### Схемка 8: Формула
Для визуальных формул, уравнений (A + B = C). Серые блоки для компонентов, коричневая рамка для результата.
```html
<div class="slide__inner">
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
  --split: 60%;
}

@page {
  size: 1280px 720px;
  margin: 0;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 17px;
  line-height: 1.75;
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

.divider {
  position: absolute;
  top: 0;
  bottom: 0;
  left: var(--split);
  width: 1px;
  background: var(--line);
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 48px;
  border-bottom: 1px solid var(--nav-line);
  background: var(--bg);
  z-index: 10;
  flex-shrink: 0;
  width: var(--split);
}
.nav__logo { text-decoration: none; display: flex; align-items: center; }
.nav__logo img { height: 30px; width: auto; }
.nav__mono {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 22px; line-height: 30px;
  color: var(--accent);
}
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px; font-weight: 400; font-style: italic;
  color: var(--muted-3); letter-spacing: 0.5px;
  margin-right: 8px;
}

.slide__body {
  flex: 1;
  display: flex;
  align-items: center;
  width: var(--split);
  padding: 0 48px;
}

.slide__inner {
  width: 100%;
  max-width: 580px;
}

/* ===== БАЗОВЫЕ ЭЛЕМЕНТЫ ===== */

.hero { padding: 0; }
.badge {
  display: inline-block; font-size: 11px; font-weight: 600;
  color: var(--accent); border: 1px solid var(--accent);
  padding: 5px 16px; margin-bottom: 20px;
  letter-spacing: 2px; text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 36px; font-weight: 700; line-height: 1.25; margin-bottom: 16px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 17px; color: var(--muted-2); line-height: 1.7; }
.hero__meta { font-size: 13px; color: var(--muted-3); margin-top: 16px; letter-spacing: 1px; }

.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3;
  padding: 0 0 20px;
}
.section-heading em { font-style: italic; color: var(--accent); }

.highlight { background: var(--block); padding: 18px 22px; margin: 20px 0; font-size: 15px; line-height: 1.75; color: var(--muted); }
.highlight strong { color: var(--text); }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700; padding: 24px 0 10px;
}

.text { font-size: 16px; color: var(--muted); line-height: 1.75; margin-bottom: 14px; }

.guide-list { list-style: none; margin: 12px 0 20px; }
.guide-list li {
  font-size: 15px; line-height: 1.7; color: var(--muted);
  padding: 6px 0 6px 18px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 14px;
  width: 5px; height: 5px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: var(--text); }

.scenario-card { border: 1px solid var(--card-border); padding: 24px; margin: 18px 0; background: var(--card); }
.scenario-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 13px;
  color: var(--accent); letter-spacing: 1px; margin-bottom: 6px;
}
.scenario-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 18px; font-weight: 700; line-height: 1.4; margin-bottom: 16px;
}
.scenario-card__point { margin-bottom: 12px; }
.scenario-card__point-label { font-weight: 600; font-size: 15px; color: var(--text); }
.scenario-card__point-text { font-size: 14px; color: var(--muted-2); line-height: 1.7; }
.scenario-card__tip {
  background: var(--tip); padding: 12px 16px; margin-top: 14px;
  font-size: 13px; color: var(--muted); line-height: 1.65;
}
.scenario-card__tip strong { color: var(--accent); }

.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--muted);
  padding: 28px 0 0;
}
.footer-note em { color: var(--accent); }

/* ===== СХЕМКА 1: ЦИТАТА-АКЦЕНТ ===== */

.quote-slide__label {
  font-size: 11px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 28px;
}
.quote-slide__mark {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 80px; color: var(--accent); line-height: 0.5;
  margin-bottom: 16px; opacity: 0.3;
}
.quote-slide__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 24px; font-weight: 400; font-style: italic;
  line-height: 1.5; color: var(--text); max-width: 480px; margin-bottom: 28px;
}
.quote-slide__text em { color: var(--accent); }
.quote-slide__divider { width: 40px; height: 2px; background: var(--accent); margin-bottom: 20px; }
.quote-slide__source { font-size: 14px; color: var(--muted-3); line-height: 1.6; }

/* ===== СХЕМКА 2: ШАГИ С ЛИНИЕЙ ===== */

.steps__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.steps__heading em { font-style: italic; color: var(--accent); }
.steps__list { position: relative; padding-left: 32px; }
.steps__list::before {
  content: ''; position: absolute; left: 7px; top: 8px; bottom: 8px;
  width: 1px; background: var(--line);
}
.steps__item { position: relative; padding-bottom: 24px; }
.steps__item:last-child { padding-bottom: 0; }
.steps__dot {
  position: absolute; left: -32px; top: 4px;
  width: 15px; height: 15px; border: 2px solid var(--accent);
  background: var(--bg); border-radius: 50%;
}
.steps__item--active .steps__dot { background: var(--accent); }
.steps__item-title { font-weight: 600; font-size: 16px; color: var(--text); margin-bottom: 4px; }
.steps__item-text { font-size: 14px; color: var(--muted-2); line-height: 1.6; }

/* ===== СХЕМКА 3: НУМЕРОВАННЫЙ СПИСОК ===== */

.numlist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.numlist__heading em { font-style: italic; color: var(--accent); }
.numlist__item {
  display: flex; gap: 24px; align-items: baseline;
  padding: 16px 0; border-bottom: 1px solid var(--nav-line);
}
.numlist__item:last-child { border-bottom: none; }
.numlist__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 36px; color: var(--accent); opacity: 0.3;
  min-width: 48px; text-align: right; line-height: 1; flex-shrink: 0;
}
.numlist__text { font-size: 15px; color: var(--text); line-height: 1.6; }
.numlist__text strong { font-weight: 600; }
.numlist__text span { color: var(--muted-2); }

/* ===== СХЕМКА 4: АКЦЕНТНАЯ ПОЛОСА СЛЕВА ===== */

.accent-bar__label {
  font-size: 11px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 24px;
}
.accent-bar__block { border-left: 3px solid var(--accent); padding-left: 28px; }
.accent-bar__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 26px; font-weight: 700; line-height: 1.35; margin-bottom: 16px;
}
.accent-bar__title em { font-style: italic; color: var(--accent); }
.accent-bar__text { font-size: 15px; color: var(--muted); line-height: 1.75; margin-bottom: 20px; }
.accent-bar__footer {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-style: italic; color: var(--muted-3);
  padding-top: 16px; border-top: 1px solid var(--nav-line);
}

/* ===== СХЕМКА 5: ЧЕК-ЛИСТ ===== */

.checklist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.checklist__heading em { font-style: italic; color: var(--accent); }
.checklist__grid { display: grid; grid-template-columns: 1fr 1fr; gap: 0; }
.checklist__col-label {
  font-size: 11px; font-weight: 600; letter-spacing: 1.5px;
  text-transform: uppercase; padding-bottom: 14px; margin-bottom: 10px;
  border-bottom: 1px solid var(--line);
}
.checklist__col-label--do { color: var(--accent); }
.checklist__col-label--dont { color: var(--muted-3); }
.checklist__col:first-child { padding-right: 20px; border-right: 1px solid var(--nav-line); }
.checklist__col:last-child { padding-left: 20px; }
.checklist__item {
  display: flex; gap: 10px; padding: 8px 0;
  font-size: 14px; color: var(--muted); line-height: 1.6; align-items: baseline;
}
.checklist__mark { flex-shrink: 0; font-size: 14px; font-weight: 700; width: 16px; }
.checklist__mark--do { color: var(--accent); }
.checklist__mark--dont { color: var(--faint); }

/* ===== СХЕМКА 6: ТРИ МЕТРИКИ ===== */

.metrics__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.metrics__heading em { font-style: italic; color: var(--accent); }
.metrics__row { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0; }
.metrics__item {
  text-align: center; padding: 24px 12px;
  border-right: 1px solid var(--nav-line);
}
.metrics__item:last-child { border-right: none; }
.metrics__number {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 48px; color: var(--accent); opacity: 0.3;
  line-height: 1; margin-bottom: 8px;
}
.metrics__label {
  font-size: 12px; color: var(--muted-3); text-transform: uppercase;
  letter-spacing: 1px; margin-bottom: 8px;
}
.metrics__desc { font-size: 13px; color: var(--muted-2); line-height: 1.5; }

/* ===== СХЕМКА 7: ВОПРОС-ОТВЕТ ===== */

.qa__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.qa__heading em { font-style: italic; color: var(--accent); }
.qa__item { margin-bottom: 24px; }
.qa__question {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--accent);
  margin-bottom: 8px; padding-left: 32px; position: relative;
}
.qa__question::before {
  content: '?'; position: absolute; left: 0; top: -4px;
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 28px; color: var(--accent); opacity: 0.3;
}
.qa__answer {
  font-size: 15px; color: var(--muted); line-height: 1.7;
  padding-left: 32px; border-left: 1px solid var(--line);
}

/* ===== СХЕМКА 8: ФОРМУЛА ===== */

.formula__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.formula__heading em { font-style: italic; color: var(--accent); }
.formula__row {
  display: flex; align-items: center; gap: 16px; margin-bottom: 32px;
}
.formula__step {
  flex: 1; background: var(--block); padding: 18px 16px; text-align: center;
}
.formula__step-title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-weight: 700; margin-bottom: 4px;
}
.formula__step-text { font-size: 12px; color: var(--muted-2); line-height: 1.5; }
.formula__arrow { color: var(--accent); font-size: 18px; flex-shrink: 0; opacity: 0.5; }
.formula__result {
  border: 1px solid var(--accent); padding: 18px 16px; text-align: center; flex: 1;
}
.formula__result .formula__step-title { color: var(--accent); }
.formula__note { font-size: 14px; color: var(--muted-3); font-style: italic; margin-top: 8px; }

/* ===== АДАПТИВ ===== */

@media print {
  html, body { width: 1280px; }
  .slide {
    width: 1280px; height: 720px;
    page-break-after: always; page-break-inside: avoid;
  }
  .slide:last-child { page-break-after: auto; }
  body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}

/* ВАЖНО: только screen — иначе правило течёт в print/PDF и ломает 60/40 split (навбар на всю ширину, исчезает разделитель и правая зона под видео) */
@media screen and (max-width: 768px) {
  .nav { padding: 16px 20px; width: 100%; }
  .hero h1 { font-size: 26px; }
  .section-heading { font-size: 22px; }
  .slide__body { width: 100%; padding: 0 20px; }
  .divider { display: none; }
}
```

## Шаблон HTML-слайда

```html
<!-- Титульный слайд -->
<div class="slide">
<div class="divider"></div>
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">O</span></a>
  <span class="nav__logo-name">olesya</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <div class="hero">
      <div class="badge">УРОК</div>
      <h1>Блог с нуля за 15 минут в день — <em>с ИИ</em></h1>
      <p class="hero__desc">Как начать, если нет времени, идей и «правильной» ниши.</p>
      <p class="hero__meta">ПРОЯВЛЕННОСТЬ &middot; CLAUDE &middot; ПЕРВЫЙ ПОСТ</p>
    </div>
  </div>
</div>
</div>

<!-- Контентный слайд -->
<div class="slide">
<div class="divider"></div>
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
</div>
```

## Как использовать

1. Получи текст/тему от Олеси
2. Разбей на логические слайды (один экран = одна мысль)
3. Первый слайд — титульный с бейджем, заголовком, описанием
4. Остальные слайды — чередуй базовые и схемки:
   - **Цитата** — для ключевых мыслей и выводов
   - **Шаги** — для процессов и последовательностей
   - **Нумерованный список** — для структур и анатомий
   - **Акцентная полоса** — для главных правил и принципов
   - **Чек-лист** — для сравнений (делай / не делай)
   - **Метрики** — для цифр и статистики
   - **Вопрос-ответ** — для FAQ и разбора сомнений
   - **Формула** — для визуальных уравнений (A + B = C)
5. Каждый 2–3-й слайд должен быть схемкой — так интереснее смотреть
6. Не перегружай слайд — контент должен поместиться в 60% экрана по центру
7. Сохрани как `index.html` в `~/Desktop/олеся/презентации/<slug>/`

## Экспорт в PDF

Генерировать строго с размером страницы 1280×720px (16:9), иначе вёрстка ломается:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --no-pdf-header-footer --print-to-pdf="presentation.pdf" --no-margins \
  --paper-width=13.333 --paper-height=7.5 "file://$(pwd)/index.html"
```

(13.333×7.5 дюйма = 1280×720px при 96dpi.)

**ОБЯЗАТЕЛЬНО проверить сам PDF в print-режиме, а не скриншот экрана** (на экране баг не виден):

```bash
sips -s format png presentation.pdf --out _check.png   # стр. 1
```

Посмотреть глазами: есть ли вертикальный разделитель на 60%, пустые ли правые 40% под видео, стоит ли ник у разделителя (а не у правого края), тёплый ли фон (не белый). После проверки удалить `_check.png`.
