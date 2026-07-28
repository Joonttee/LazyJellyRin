# LazyJellyRin — Библиотека игр

Коллекция игр стримерши **LazyJellyRin** — ленивой желейки, которая тыкает в игры 🪼💜

Live сайт: **https://Joonttee.github.io/LazyJellyRin/** (после включения GitHub Pages)

Вдохновлено проектами:
- https://joonttee.github.io/MikkleoGame/
- https://joonttee.github.io/Lunar1ya/

## Что внутри

- 244 игры из гугл-таблицы: https://docs.google.com/spreadsheets/d/1aWlR0uCXR2BOVwIgHV-z70IgFwKfdxWE13O7Wnp6vWA/edit?pli=1&gid=0#gid=0
- Статусы: `пройдено`, `в процессе`, `в сердешке <3`, `в списке`, `подарили`, `брошено`, `наигралась`, `отложено` и т.д.
- Жанры из Steam (инди, ролевая, приключение, экшен, хоррор, стратегия и др.)
- Заметки и 🎁 подарки от чата (FunnyIVIan, donstasone91, hogo_chan …)
- Фильтры: по статусу, жанру, доп. статусу, поиску, сортировке
- Темы: Jelly (основная), Deep, Candy
- Адаптив для телефона/планшета/десктопа
- Проверка LIVE статуса Twitch через api.ivr.fi
- Модалки с деталями, копирование ссылки на игру

## Структура

```
/index.html          # сам сайт (single-file, оптимизирован, с встроенными данными)
/data/games.json     # каталог в JSON (244 игры)
```

## Как обновить игры

1. Отредактируй гугл-таблицу (добавь новые строки, статусы, жанры, заметки)
2. Запусти `python tools/parse_sheet.py` (скрипт, который парсит экспорт таблицы в `data/games.json`)
   — сейчас уже есть готовый парсер в `/tmp/parse_sheet.py` и `/tmp/gen_final.py` как пример
3. Закоммить `data/games.json` и `index.html` (если встроил данные)
4. GitHub Pages автоматически обновит сайт

### Формат записи в JSON

```json
{
  "id": "hollow-knight",
  "title": "Hollow Knight",
  "rawTitle": "Hollow Knight",
  "genre": "инди, экшен, приключение",
  "genres": ["инди","экшен","приключение"],
  "year": null,
  "status": "done",
  "rawStatus": "пройдено",
  "tags": [],
  "note": "прониклась с 3 попытки",
  "gift": false,
  "cover": null
}
```

`status` — канонический:
- `playing` — в процессе
- `done` — пройдено / пройдено не на стриме
- `favorite` — в сердешке <3
- `planned` — в списке (куплено / gamepass), хочу
- `gift` — подарили
- `played` — наигралась / пока наигралась / наигралась без стрима
- `dropped` — брошено / брошено нахер
- `postponed` — отложено

## Деплой (GitHub Pages)

1. В репозитории Settings → Pages → Source: Deploy from branch `main` (или `arena/...` для теста) / root
2. Дождись деплоя, сайт появится по адресу `https://Joonttee.github.io/LazyJellyRin/`
3. Не забудь добавить `.nojekyll` файл в корень (уже есть, если нужен)

## TODO / Идеи

- [ ] Подтянуть обложки из Steam (header.jpg по appid или скриншоты)
- [ ] Автоматически получать год релиза через IGDB/Steam API и включить фильтр по эпохам
- [ ] Теги 🕹️ MP / 🤝 Coop для совместных игр (ARC Raiders, PEAK, R.E.P.O., We Were Here …)
- [ ] Админ-панель с PIN (как в MikkleoGame) для локального редактирования статусов
- [ ] Поиск по заметкам и подаркам чата
- [ ] Анимация желейки 🫧 на фоне

Made with 💜 by Joonttee & Arena agent for LazyJellyRin
