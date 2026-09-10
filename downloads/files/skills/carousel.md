---
name: carousel
description: Создаёт карусель для Instagram (1080×1350, PNG) в фирменном стиле Олеси (тёплый бежевый фон, Libre Baskerville + Inter, коричневые акценты) — HTML-слайды + рендер через headless Chrome. Вызывай, когда Олеся просит карусель.
---

# Скилл: Карусель Олеси (1080×1350)

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и **реальный ник** (в навбаре и футере `@ник`). Пока ника там нет — пиши `olesya` / `@olesya`.
3. Если появился логотип `~/.claude/brand/logo-olesya.png` — скопируй в папку карусели как `logo.png` и используй вместо монограммы (высота 46px).
4. Границы абсолютны: дети, семья, личные детали близких — в карусели не появляются (ни в тексте, ни на фото).
5. Спроси Олесю одним вопросом, если чего-то нет: фото для обложки, скрины, кодовое слово для призыва.

Когда Олеся просит сделать карусель — сгенерируй HTML-слайды 1080×1350 в ФИРМЕННОМ стиле (тот же, что гайды/лендинги/презентации) и отрендери в PNG через headless Chrome. Полный шаблон слайда — ниже.

## Дизайн — фирменный стиль, как в гайдах

- Фон `#FAF7F3`, текст `#2A211C`, второстепенный `#5E534C`/`#7A6F67`
- **Заголовки**: Libre Baskerville 700, 50–58px, курсивные акценты `<em>` коричневым `#7B5A43`
- **Текст**: Inter, 29px, line-height 1.72
- Серые блоки `#F1ECE6`, квадратные углы, БЕЗ border-radius
- **Навбар на каждом слайде**: монограмма `O` слева (Libre Baskerville italic 34px, цвет акцента) + *ник* справа (DM Sans italic 25px `#9A908A`), линия снизу `#EFE9E2`
- **Футер на каждом слайде**: линия сверху `#EFE9E2`, слева `@ник` (DM Sans italic `#9A908A`), справа *листай →* (Libre Baskerville italic, коричневый); на последнем слайде — *жду в комментариях →*
- Бейдж на обложке: рамка 1px коричневая, капс, letter-spacing 4px («СПОСОБ», «ГАЙД», «РАЗРЕШЕНИЕ»…)
- Декоративные цифры шагов: Libre Baskerville italic, ~230px, коричневый, opacity .15, абсолютно справа сверху
- Лейблы («ШАГ 1», «ГЛАВНОЕ»): Inter 600, 19px, капс, letter-spacing 4px, `#9A908A`
- Цитаты/промты: серый блок `#F1ECE6` + текст Libre Baskerville italic коричневым
- Фото: «полароид» — рамка padding 16px, фон `#FFFDFB`, border `#E4DCD3`, тень, наклон -2°; стикеры PNG поверх с drop-shadow и поворотом
- Скрины: карточка border `#E4DCD3` + padding 16px + лёгкая тень; высокий скрин — контейнер `flex:1 1 0; min-height:0; overflow:hidden` (обрезка снизу)
- Схемки-вариации из скилла презентаций работают и тут: цитата-акцент (кавычка 150px opacity .3 + LB italic 46px), акцентная полоса слева 3px коричневая, команда в рамке коричневой (`/post` + курсор)
- На тёмном фоне (если слайд тёмный `#2A211C`) акцент только `#D9BFA4`
- Слова Claude и reels — всегда латиницей
- Голос — по разделу 8 PROFILE.md: на «ты», женский род, короткие удары, одна мысль на слайд, финал — одна сильная строка

## Структура типовой карусели

1. Обложка: бейдж + h1 с коричневым `<em>` + подзаголовок + полароид-фото со стикером (для faceless — вместо фото скрин или серый блок с цитатой)
2. Крючок/введение
3–5. Шаги: лейбл «ШАГ N» + гигантская цифра + заголовок + текст; скрины по смыслу
6. Перелом «главное»: акцентная полоса слева
7. Результат (команда/формула)
8. Вывод: схемка-цитата
9. Призыв: плашка с кодовым словом (рамка коричневая, letter-spacing 7px) + скрин ТГ-канала (обрезан снизу)

Пример обложки в её теме: бейдж «РАЗРЕШЕНИЕ», h1 «Блог с нуля за 15 минут в день — *и без разрешения мужа, мамы и подруг*», подзаголовок «Система, а не подвиг. Повторишь сегодня вечером». Шаг 1: «Открываешь Claude и пишешь *одну фразу*» + серый блок «Помоги мне понять, о чём мой блог, в трёх предложениях. Я — …». Вывод-цитата: «Первый пост не обязан быть шедевром. *Он обязан существовать.*»

## Шаблон слайда (копировать целиком)

```html
<!doctype html><html><head><meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{--bg:#FAF7F3;--text:#2A211C;--muted:#5E534C;--muted-2:#7A6F67;--muted-3:#9A908A;
  --accent:#7B5A43;--accent-dark:#D9BFA4;--block:#F1ECE6;--card:#F5F1EC;--card-border:#E4DCD3;--line:#E9E3DC;--nav-line:#EFE9E2}
html,body{width:1080px;height:1350px;overflow:hidden}
.canvas{width:1080px;height:1350px;position:relative;overflow:hidden;display:flex;flex-direction:column;
  font-family:'Inter',sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased}
.nav{flex:0 0 auto;display:flex;align-items:center;justify-content:space-between;
  padding:46px 90px 34px;border-bottom:1px solid var(--nav-line)}
.nav img{height:46px;width:auto;display:block}
.nav .mono{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:34px;line-height:46px;color:var(--accent)}
.nav .name{font-family:'DM Sans',sans-serif;font-style:italic;font-size:25px;color:var(--muted-3);letter-spacing:.5px}
.frame{flex:1 1 auto;min-height:0;display:flex;flex-direction:column;padding:0 100px}
.content{flex:1 1 auto;min-height:0;display:flex;flex-direction:column;justify-content:center;position:relative}
.footer{flex:0 0 auto;display:flex;align-items:center;justify-content:space-between;
  padding:30px 0 56px;border-top:1px solid var(--nav-line)}
.footer .left{font-family:'DM Sans',sans-serif;font-style:italic;font-size:22px;color:var(--muted-3)}
.footer .right{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:24px;color:var(--accent)}
.badge{display:inline-block;align-self:flex-start;font-size:19px;font-weight:600;color:var(--accent);
  border:1px solid var(--accent);padding:12px 30px;margin-bottom:44px;letter-spacing:4px;text-transform:uppercase}
h1{font-family:'Libre Baskerville',Georgia,serif;font-weight:700;font-size:56px;line-height:1.3}
h1 em{font-style:italic;color:var(--accent)}
.body{font-size:29px;color:var(--muted);line-height:1.72;margin-top:36px}
.body strong{color:var(--text)}
.steplabel{font-size:19px;font-weight:600;letter-spacing:4px;color:var(--muted-3);text-transform:uppercase;margin-bottom:30px}
.giantnum{position:absolute;top:40px;right:0;font-family:'Libre Baskerville',Georgia,serif;
  font-style:italic;font-size:230px;line-height:1;color:var(--accent);opacity:.15;user-select:none}
.highlight{background:var(--block);padding:36px 42px;margin-top:42px;font-size:28px;line-height:1.65;color:var(--muted)}
.highlight em{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;color:var(--accent)}
.shot{border:1px solid var(--card-border);background:#FFFDFB;padding:16px;box-shadow:0 14px 36px rgba(42,33,28,.10)}
.shot img{display:block;width:100%}
.polaroid{background:#FFFDFB;border:1px solid var(--card-border);padding:16px 16px 20px;
  box-shadow:0 18px 44px rgba(42,33,28,.14);transform:rotate(-2deg)}
.polaroid img{display:block;width:100%}
.sticker{position:absolute;filter:drop-shadow(0 14px 30px rgba(42,33,28,.22));z-index:3}
.accent{border-left:3px solid var(--accent);padding-left:40px}
.qmark{font-family:'Libre Baskerville',Georgia,serif;font-size:150px;color:var(--accent);line-height:.5;
  opacity:.3;margin-bottom:30px}
.qtext{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:46px;line-height:1.5}
.qtext em{color:var(--accent)}
.qdivider{width:64px;height:3px;background:var(--accent);margin:44px 0 32px}
.qsource{font-size:27px;color:var(--muted-2);line-height:1.7}
.cmd{display:inline-flex;align-items:center;align-self:flex-start;border:2px solid var(--accent);color:var(--accent);
  padding:30px 54px;margin-top:48px;font-weight:800;font-size:68px;letter-spacing:1px}
.cmd .cursor{display:inline-block;width:7px;height:64px;background:var(--accent);margin-left:16px;opacity:.8}
.plashka{display:inline-block;align-self:flex-start;border:1px solid var(--accent);color:var(--accent);
  padding:22px 54px;margin-top:46px;font-weight:700;font-size:32px;letter-spacing:7px}
.tgwrap{flex:1 1 0;min-height:0;overflow:hidden;margin-top:48px;margin-bottom:10px;display:flex;justify-content:center}
.tgwrap .shot{width:520px;align-self:flex-start}
</style></head><body>
<div class="canvas">
  <nav class="nav"><span class="mono">O</span><span class="name">olesya</span></nav>
  <div class="frame">
    <div class="content"><div class="badge">Разрешение</div>
    <h1>Блог с нуля за 15 минут в день — <em>и без чужого разрешения</em></h1>
    <p class="body" style="margin-top:28px;color:var(--muted-2)">Система, а не подвиг. Повторишь сегодня вечером</p>
    <div style="display:flex;justify-content:center;margin-top:54px;position:relative">
      <div class="polaroid" style="width:430px"><img src="photo.jpg"></div>
      <img class="sticker" src="sticker.png" style="width:190px;right:110px;top:-30px;transform:rotate(8deg)">
    </div></div>
    <div class="footer"><span class="left">@olesya</span><span class="right">листай &rarr;</span></div>
  </div>
</div></body></html>
```

Варианты `.content` для других слайдов:
- Шаг: `<div class="giantnum">1</div><div class="steplabel">Шаг 1</div><h1>Открываешь Claude и пишешь <em>одну фразу</em></h1><div class="highlight"><em>«Помоги мне понять, о чём мой блог, в трёх предложениях»</em></div><p class="body">Это база — дальше самое интересное</p>`
- Главное: `<div class="accent"><div class="steplabel">Главное</div><h1>Разрешение — это не аффирмация. <em>Это поведение</em></h1><p class="body">…</p></div>`
- Вывод-цитата: `<div class="qmark">&ldquo;</div><div class="qtext">Первый пост не обязан быть шедевром. <em>Он обязан существовать.</em></div><div class="qdivider"></div><p class="qsource">…</p>`
- Призыв: `<h1 style="font-size:50px">Хочешь пошаговую инструкцию <em>со скринами?</em></h1><p class="body">Напиши в комментариях слово «БЛОГ» — скину в директ</p><div class="plashka">«БЛОГ»</div><div class="tgwrap"><div class="shot"><img src="tg.jpg"></div></div>` + футер *жду в комментариях →*

## Рендер

Папка: `~/Desktop/олеся/карусели/карусель-<тема>/`. Материалы (фото, скрины, стикеры, `logo.png`) скопировать в неё с ASCII-именами.

```bash
for i in 1 2 3 ...; do
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
    --hide-scrollbars --force-device-scale-factor=1 --window-size=1080,1350 \
    --virtual-time-budget=10000 --screenshot="слайд-$i.png" "file://$(pwd)/slide-$i.html"
done
```

ОБЯЗАТЕЛЬНО посмотреть готовые PNG глазами: слайд может отрендериться пустым (перезапустить с sleep 1 между слайдами), футер не должен уезжать за край (`min-height:0` на flex-контейнерах), фон должен быть тёплым бежевым, а не белым (если белый — шрифты/CSS не подгрузились, перезапустить).
