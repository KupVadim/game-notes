---
title: Assetto Corsa Rally — VR через UEVR (Quest 3)
description: Практический гайд по настройке UEVR для Assetto Corsa Rally. Quest 3, Virtual Desktop, RTX 4080 Super.
tags:
  - VR
  - UEVR
  - Assetto Corsa Rally
  - Quest 3
  - Virtual Desktop
  - OpenXR Toolkit
---

# 🥽 Assetto Corsa Rally в VR через UEVR

!!! warning "Важно"  
    Assetto Corsa Rally **не имеет нативного VR**.  
    Всё ниже — компромисс между качеством, FPS и стабильностью.

---

## 🎯 Цель гайда

- Получить **стабильные 72 FPS**
- Минимизировать укачивание
- Понять, **где пределы UEVR**

---

## 🧩 Сетап

- "Железо"
    - GPU: **RTX 4080 Super**
    - CPU: i5 / i7 (не критично)
    - RAM: 32 GB
    - OS: Windows 11

- "VR"
    - **Meta Quest 3**
    - **Virtual Desktop**
    - Target FPS: **72**

- "ПО"
    - Assetto Corsa Rally
    - **UEVR (Universal Unreal Engine VR Injector)**

---

## 🧪 UEVR Nightly Builds (рекомендуется)

Используй актуальные **nightly-сборки UEVR** — они чаще всего стабильнее релизов:

👉 https://github.com/praydog/UEVR-nightly/releases

!!! info
    Nightly-версии часто содержат исправления под конкретные версии Unreal Engine  
    и лучше подходят для UEVR-инжекта.

!!! warning
    Это экспериментальные сборки.  
    Если появились баги — просто откатись на предыдущую версию.

---

## 🧠 OpenXR Toolkit (опционально)

OpenXR Toolkit может использоваться для:

- апскейла
- шарпинга
- foveated rendering
- eye-tracking (если поддерживается шлемом)

👉 Документация:  
https://mbucchia.github.io/OpenXR-Toolkit/#eye-tracking-feature

!!! warning
    **OpenXR Toolkit не всегда стабилен в связке с UEVR.**  
    Возможны:
    - вылеты при старте
    - чёрный экран
    - потеря ввода
    - некорректный scale / projection

!!! tip
    Если появились проблемы — **первым делом отключи OpenXR Toolkit**  
    и проверь работу UEVR без него.

---

## ⬇️ Установка UEVR

1. Скачай нужную версию UEVR (release или nightly)
2. Распакуй в отдельную папку

!!! warning
    Антивирус может ругаться — это нормально для инжекторов.

---

## 🚀 Запуск игры и инжект

1. Запусти **Assetto Corsa Rally** обычным способом
2. Дождись главного меню
3. Запусти `UEVR.exe`
3. Нажми **Restart as Administrator** если запускал не под админом
4. Нажми **Inject**

!!! tip
    Если экран чёрный — Alt+Tab и проверь активное окно игры.

---

## 🛠 Настройки UEVR

### Рекомендованный минимум

```text
Projection: Stereo
World Scale: 1.0
Stereo Separation: Default
```

!!! danger
    Не крути все ползунки подряд.  
    UEVR **не про «накрутить красиво»**, а про стабильность.

---

## 📡 Virtual Desktop — ключевые параметры

- "Streaming"
    - Codec: **HEVC**
    - Bitrate: 120–150 Mbps
    - SSW: **Off / Auto**

- "Performance"
    - Spacewarp: по ситуации
    - Snapdragon Super Resolution: *опционально*

!!! note
    Spacewarp может спасти FPS, но ухудшает отклик руля.

---

## 🎮 Настройки Assetto Corsa Rally

### Отключить сразу
- Motion Blur
- Eye Adaptation
- Film Grain

### Оставить осторожно
- Shadows: Medium
- Textures: High

!!! warning
    «Мыло» часто идёт от апскейла, а не от VR.

---

## 🧯 Частые проблемы

### Просадки FPS при записи
- ❌ Запись VR напрямую
- ✅ Запись **Companion / Desktop window**

### Чёрный экран после инжекта
- Проверить fullscreen mode
- Перезапустить игру **без перезапуска UEVR**

---

## ✅ Итог

- UEVR **работает**
- Это **не нативный VR**
- Nightly-сборки предпочтительнее
- OpenXR Toolkit — **опционально и осторожно**
- 72 FPS — реалистичная цель
- Для ралли VR даёт **лучшее чувство машины**
