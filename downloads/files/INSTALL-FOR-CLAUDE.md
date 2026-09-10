# Установщик рабочего места Олеси (инструкция для Claude)

Ты выполняешь установку на маке Олеси — ученицы Майи (@maysoulme). Пакет — приватный репозиторий `maiyamaiya19999-bit/olesya-setup`, Олеся приглашена в него на чтение. Пройди пункты по порядку, в конце дай отчёт по каждому. Если какой-то пункт не удался — не молчи и не пропускай: скажи, что именно не вышло, и предложи решение. Ничего не выдумывай: токены, ники, названия каналов — только из ответов Олеси.

Ниже `$P` = `~/olesya-setup` (папка, куда клонируется пакет).

## 1. Инструменты

Проверь и при необходимости установи (через Homebrew, если он есть; если нет — предложи установить Homebrew или скачать программу с официального сайта):
- `git` — `git --version`
- `gh` (GitHub CLI) — `gh --version`, затем `gh auth status`. Если входа нет — `gh auth login --web` и дождись, пока Олеся подтвердит вход в браузере. Без входа шаг 2 не сработает.
- `python3` — `python3 --version` (нужен 3.9+). На маке обычно есть; если нет — `xcode-select --install` или Homebrew.
- Google Chrome — для рендера каруселей в PNG и презентаций в PDF. Проверь: `ls "/Applications/Google Chrome.app"`. Если нет — попроси Олесю установить Chrome с google.com/chrome (сам не скачивай), затем продолжай. Путь к бинарнику для headless-рендера: `/Applications/Google Chrome.app/Contents/MacOS/Google Chrome`.

## 2. Клонирование пакета

```
if [ -d ~/olesya-setup/.git ]; then git -C ~/olesya-setup pull; else gh repo clone maiyamaiya19999-bit/olesya-setup ~/olesya-setup; fi
```

Если ошибка доступа (`Could not resolve to a Repository`, `403`, `404`) — у Олеси либо не принято приглашение в репозиторий, либо `gh` залогинен под другим аккаунтом. Скажи об этом прямо (README, шаг 2) и остановись — дальше без пакета делать нечего.

## 3. Скиллы

Скопируй **все** `*.md` из `$P/skills/` в `~/.claude/commands/` (создай папку, если нет; существующие файлы с теми же именами — перезаписать):

```
mkdir -p ~/.claude/commands && cp "$HOME/olesya-setup/skills/"*.md ~/.claude/commands/
```

Ожидаемый набор (список может быть шире — копируй всё, что лежит в папке):
- guide.md — гайд-лендинг / статья в её фирменном стиле
- presentation.md — презентация к видеоуроку (60/40, место под видео)
- presentation-full.md — полноэкранная презентация + экспорт в PDF
- carousel.md — карусель для Instagram 1080×1350 (PNG)
- tg.md — режим ИИ-продюсера Telegram-канала (подтягивает посты из `~/tg-assistant`)
- tg-posts.md — посты для Telegram
- stories.md — сценарии сторис
- reels-expert.md — сценарии экспертных reels
- reels-story.md — сценарии личных/сторителлинг reels
- lead-magnet.md — лид-магнит
- tg-funnel.md — воронка в Telegram
- progrev.md — прогрев к продукту
- ca-tripwire.md — анализ ЦА и трипваер
- selling-lesson.md — продающий урок

Если какого-то файла из списка нет в `$P/skills/` — не выдумывай его и не создавай пустышку, просто отметь в отчёте «не входит в текущую версию пакета».

## 4. Бренд-файлы

```
mkdir -p ~/.claude/brand
cp "$HOME/olesya-setup/brand/PROFILE.md" "$HOME/olesya-setup/brand/TOV-SAMPLES.md" "$HOME/olesya-setup/brand/style-guide.md" ~/.claude/brand/
```

- `PROFILE.md` — распаковка Олеси (кто она, история, ЦА, голос, границы, продукты). Главный файл: каждый скилл читает его первым.
- `TOV-SAMPLES.md` — её живые тексты, эталон голоса.
- `style-guide.md` — бежево-коричневая палитра и правила оформления.

Если `~/.claude/brand/PROFILE.md` уже существует и отличается от версии в пакете (`diff -q`) — **не перезаписывай молча**: спроси Олесю, редактировала ли она файл; если да — оставь её версию, если нет — обнови.

## 5. Папка ТГ-ассистента

Ставится в **домашнюю папку** `~/tg-assistant`, не на Desktop (TCC macOS блокирует launchd на Рабочем столе).

Если `~/tg-assistant` **нет**:
```
cp -R "$HOME/olesya-setup/tg-assistant-template" ~/tg-assistant
```

Если папка **уже есть** — не затирай её данные. Обновляй только скрипты и документы:
```
cd "$HOME/olesya-setup/tg-assistant-template"
cp *.py *.sh config.example.json ~/tg-assistant/
mkdir -p ~/tg-assistant/.claude && cp .claude/settings.json ~/tg-assistant/.claude/
[ -f ~/tg-assistant/watchlist.json ] || cp watchlist.json ~/tg-assistant/
for f in *.md; do [ -f "$f" ] && cp "$f" ~/tg-assistant/; done
```
Никогда не трогай `~/tg-assistant/posts/`, `~/tg-assistant/drafts/`, `~/tg-assistant/plan/`, `~/tg-assistant/competitors/`, `config.json`, `state.json`.

**config.json.** Файл `~/tg-assistant/config.json` нужен для `sync_channel.py` (через бота) и `scrape_history.py` (публичная страница канала). Если его нет — создай из шаблона и заполни **только тем, что дала Олеся**:
1. Спроси одним сообщением: «Дай, пожалуйста, две вещи: токен твоего бота от @BotFather (бот должен быть добавлен администратором в канал) и юзернейм канала без @».
2. Если ответила — `cp ~/tg-assistant/config.example.json ~/tg-assistant/config.json` и подставь значения.
3. Если бота ещё нет или отвечать сейчас не хочет — оставь `config.json` несозданным, отметь в отчёте «предупреждение: config.json не заполнен» и объясни, что `scrape_history.py --channel имя_канала` работает и без него для публичного канала.
Не вставляй значения-заглушки из `config.example.json` в `config.json` и ничего не придумывай.

Автосинхронизацию (`setup_autosync.sh`) на этапе установки **не включай** — только скажи, что она есть и включается командой `bash ~/tg-assistant/setup_autosync.sh` после того, как заполнен `config.json`.

## 6. Контент и парсер (без установки)

- `$P/content/` — готовые материалы Олеси (гайд «Разреши», книга «Проявленность», планы). Никуда не копируется, живёт в `~/olesya-setup/content/`. Скажи Олесе этот путь.
- `$P/parser/` — гайд по установке парсера reels-monitor под её аккаунт. **Автоматически не устанавливай.** Только сообщи: «Парсер ставится отдельно, инструкция — `~/olesya-setup/parser/`». Если папка пуста — так и скажи: «в этой версии пакета парсер ещё не добавлен».

## 7. Глобальные правила пользователя

Создай (или дополни, **не затирая существующее**) файл `~/.claude/CLAUDE.md`. Перед дописыванием проверь `grep -q "Я — Олеся" ~/.claude/CLAUDE.md` — если блок уже есть, не дублируй. Блок:

```
# Обо мне
Я — Олеся. Язык общения — русский, на «ты». Не переспрашивай лишний раз — делай.

# Мой профиль и голос
Перед любым контентом читай ~/.claude/brand/PROFILE.md и ~/.claude/brand/TOV-SAMPLES.md.

# Фирменный стиль
~/.claude/brand/style-guide.md — бежево-коричневая палитра, Libre Baskerville + Inter, квадратные углы; на тёмном фоне акцент только #D9BFA4.

# Правила
Слова «Claude» и «reels» — всегда латиницей. Темы «дети» и «отношения внутри семьи» публично не раскрываются. Материалы Майи (@maysoulme) не выкладывать в открытый доступ.
```

## 8. Проверки (выполни реально, командами, не на словах)

1. `ls ~/.claude/commands/*.md` — выведи список; сверь с пунктом 3, отметь, каких файлов нет.
2. `ls -la ~/.claude/brand/` — на месте `PROFILE.md`, `TOV-SAMPLES.md`, `style-guide.md`.
3. `python3 -m py_compile ~/tg-assistant/*.py` — все скрипты компилируются без ошибок.
4. `test -f ~/tg-assistant/config.json && echo OK || echo "НЕТ config.json"` — если нет, это предупреждение, а не ошибка (см. пункт 5).
5. Рендер через headless Chrome: создай в `/tmp` файл `test.html` с любым текстом и выполни
   ```
   "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --disable-gpu --hide-scrollbars --window-size=1080,1350 --screenshot=/tmp/test.png /tmp/test.html
   ```
   Проверь, что `/tmp/test.png` появился и не пустой (`ls -la /tmp/test.png`). Тестовые файлы затем удали.
6. `grep -c "Я — Олеся" ~/.claude/CLAUDE.md` — блок правил записан ровно один раз.

## 9. Отчёт

Выведи Олесе таблицу: пункт → статус (готово / предупреждение / ошибка) → комментарий. Отдельными строками: «config.json» и «парсер» (он не ставится — это норма). Если всё готово, скажи, что можно переходить к шагу 4 из README (тест `/reels-expert`), и напомни путь к контенту `~/olesya-setup/content/`.

## 10. Обновление пакета

Когда Олеся просит «обнови пакет» / «обнови скиллы»:

1. `git -C ~/olesya-setup pull`
2. Повтори пункт 3 (скиллы): `cp "$HOME/olesya-setup/skills/"*.md ~/.claude/commands/`
3. Повтори пункт 4 для `TOV-SAMPLES.md` и `style-guide.md`. **`PROFILE.md` — не перезаписывай автоматически:** сравни `diff ~/.claude/brand/PROFILE.md ~/olesya-setup/brand/PROFILE.md`; если файлы различаются — спроси Олесю, вносила ли она правки в свой профиль. Правки были — оставь её версию и покажи, что изменилось в пакете, чтобы она перенесла нужное; правок не было — обнови.
4. Повтори пункт 5 в режиме «папка уже есть» (только скрипты и документы, данные не трогать).
5. Блок в `~/.claude/CLAUDE.md` повторно не дописывай.
6. Короткий отчёт: что обновилось (по `git log --oneline HEAD@{1}..HEAD` можно показать список изменений).
