# PacenotePal — установка русского голосового пакета **VadimInGame**

Это руководство описывает установку и настройку моего русского голосового пакета для **PacenotePal**.

Гайд ориентирован на быстрый запуск без лишних действий.

---

## 📥 Шаг 1. Скачиваем PacenotePal

Скачайте последнюю версию PacenotePal со страницы релизов:

https://github.com/Koenvh1/PacenotePal/releases

Выбирайте `.zip`.

!!! note
    PacenotePal — портативное приложение. Установка в систему не требуется.

---

## 📂 Шаг 2. Разархивируем PacenotePal

Разархивируйте скачанный архив **в любую удобную папку**.

Пример:

```
D:\Games\PacenotePal\
```

---

## 🎙 Шаг 3. Скачиваем голосовой пакет

Скачайте мой голосовой пакет:

[VadimInGame - Русский штурман](https://release-assets.githubusercontent.com/github-production-release-asset/1099346847/b8fb4e02-d46a-4650-b571-d884ee0556ba?sp=r&sv=2018-11-09&sr=b&spr=https&se=2025-12-27T02%3A29%3A02Z&rscd=attachment%3B+filename%3DPacenotePal.zip&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9515b896b4de&skt=2025-12-27T01%3A28%3A16Z&ske=2025-12-27T02%3A29%3A02Z&sks=b&skv=2018-11-09&sig=6Ds2WOmCNRkmXZa7SHdQsAeemx%2FRN3yFJ3fHslVkSik%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc2NjgwMjQ5NiwibmJmIjoxNzY2Nzk4ODk2LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.THcaZafbMRj6igV4HivxLRWev3bxTcIX0yYgaEiA2ps&response-content-disposition=attachment%3B%20filename%3DPacenotePal.zip&response-content-type=application%2Foctet-stream)

---

## 📁 Шаг 4. Установка голосового пакета

1. Разархивируйте скачанный архив
2. Внутри будет папка:

```
VadimInGame - Русский
```

3. Скопируйте эту папку в каталог:

```
PacenotePal\voices\
```

В итоге структура должна выглядеть так:

```
PacenotePal\
 └─ voices\
    └─ VadimInGame - Русский\
```

!!! warning
    Важно копировать **именно папку**, а не отдельные файлы внутри неё.
    Иначе голос не появится в списке.

---

## ▶️ Шаг 5. Запуск PacenotePal и выбор голоса

1. Запустите **PacenotePal**
2. Перейдите в меню **Settings**
3. В параметре **Voice** выберите:
```
VadimInGame - Русский
```
4. Нажмите Save

---

## 🎮 Шаг 6. Настройки игры

1. Запустите игру
2. Перейдите в:

```
Settings → Audio
```

3. Установите параметр **Co-Driver Volume** в значение `0`

!!! warning
    Если не отключить встроенного штурмана, вы будете слышать **два голоса одновременно**.

---

## 🏁 Шаг 7. Выбор спецучастка и запуск PacenotePal

1. В игре выберите спецучасток, который планируете ехать
2. Дождитесь загрузки в гонку
3. Переключитесь в окно **PacenotePal**
4. Выберете спец участов в Select a Stage
4. Нажмите кнопку **Start**

!!! note
    Кнопку **Start** в PacenotePal нужно нажимать **после выбора конкретного спецучастка**.
    Если нажать раньше, синхронизация штурмана может работать некорректно.

---

## 🚦 Шаг 8. Старт штурмана

1. Подъезжайте к стартовой линии
2. Нажмите **пробел**

Если вы услышали **короткий сигнал “бип”**, значит:

- PacenotePal успешно запущен
- стенограмма синхронизирована
- штурман готов к работе

!!! tip
    В настройках PacenotePal можно назначить **другую клавишу старта**.
    Также можно использовать `HandbrakeHelper.exe`, чтобы привязать старт к ручнику.

!!! note
    С моим ручником `HandbrakeHelper.exe` не сработал, поэтому я использую **пробел**.

---

## 🔊 Если голос звучит тихо

Если штурман слышен плохо:

- уменьшите **громкость звука игры**

---

## ✅ Готово

Если после сигнала вы слышите мой голос —
**значит всё настроено правильно**.

Приятных заездов и чистых прохождений 🏁
