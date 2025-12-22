---
title: Assetto Corsa Rally — VR через UEVR (Quest 3)
description: Полный практический гайд по настройке UEVR для Assetto Corsa Rally. Quest 3, Virtual Desktop, RTX 4080 Super. С пояснениями почему именно такие значения.
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
    UEVR — это инжектор. Цель гайда — не «красиво», а **стабильно и играбельно**.

---

## 🎯 Цель гайда

- **Стабильные 72 FPS**
- Предсказуемая яркость (без автоэкспозиции)
- Минимум микростаттеров
- Приоритет читаемости трассы и окружения в VR

---

## 🧩 Начальные требования

### Железо
- GPU: **RTX 4080 Super**
- CPU: **i5-13600KF**
- RAM: 32 GB
- OS: Windows 11

### VR / Streaming
- **Meta Quest 3**
- **Virtual Desktop**
    - VR Graphics Quality: **Ultra**
    - Target FPS: **72**
    - Bitrate: **200 Mbps** - ну или под свой WiFi
    - Wi‑Fi 5 GHz с линком ~2400 Mbps — достаточно

### ПО
- Assetto Corsa Rally 
- **UEVR (Nightly builds)** -> https://github.com/praydog/UEVR-nightly/releases
- OpenXR Toolkit -> https://mbucchia.github.io/OpenXR-Toolkit/#downloads

---

## 🧪 UEVR Nightly Builds

👉 https://github.com/praydog/UEVR-nightly/releases

---

## 🚀 Запуск игры и инжект

1. Запусти **Assetto Corsa Rally**
2. Дождись главного меню
3. Запусти `UEVR.exe`
4. Нажми **Restart as Administrator**
5. Нажми **Inject**
6. Runtime: **OpenXR**

---

## 🎚 UEVR

!!! important
    Включите Advanced Mode -> `Show Advanced Options`



- Console\CVars
    - r.Color.Max = 0.775
    - r.Color.Mid = 0.328
    - r.Color.Min = 0.000
    - r.TonemapperGamma = 2.0
    - r.TonemapperSharpen = 1.3
    - r.MotionBlur.Max = -1
    - r.SceneColorFringe.Max = -1
    - r.TemporalAA.Upsampling = 0

---

## 🧾 Auto Exposure OFF

В Console\CVars нажимаем Display Console и пишем в консоле

```ini
r.DefaultFeature.AutoExposure 0
r.EyeAdaptationQuality 0
```

---

## 🧠 OpenXR Toolkit

👉 https://mbucchia.github.io/OpenXR-Toolkit/#downloads

- Fixed Foveated Rendering
- Mode: **Quality**
- Pattern: **Wide**

Даёт несколько дополнительных FPS и помогает удержать 72.

---

## 🎮 Assetto Corsa Rally — Graphics

!!! note "DLSS 4"
    Я не знаю какой DLSS по умолчанию в игре, но я всегда сразу заменяю на последний DLSS. Скачал тут https://www.techpowerup.com/download/nvidia-dlss-dll/ 
    
    - заменяем `c:\Program Files (x86)\Steam\steamapps\common\Assetto Corsa Rally\Engine\Plugins\nvidia\DLSS\Binaries\ThirdParty\Win64\nvngx_dlss.dll` (или где там у вас игры Steam) на скачанный `nvngx_dlss.dll`

### Upscaling
- DLSS
- Resolution Scale: 75% - в принципе можно увеличивать, если другие параметры понижать
- Frame Generation: OFF

### Quality
- Texture: HIGH
- Shadows: VERY LOW
- Clouds: LOW
- Post Process: LOW
- Foliage: ULTRA - для меня деревья важнее теней. Меня бесит когда прогружаются деревья перед носом. Если хотите выше базовое разрешение - ставьте тогда VeryLow, они хоть не прогружаются, а всегда кривые :)
- Grass: MEDIUM
- Effects: MEDIUM
- Car Damage: HIGH
- Crowd: MEDIUM
- Interactive Elements: VERY LOW
- Car LCD: LOW

---

## ✅ Итог

- UEVR Nightly обязателен
- OpenXR Toolkit реально помогает
- Деревья важнее теней
- 72 FPS достижимы
