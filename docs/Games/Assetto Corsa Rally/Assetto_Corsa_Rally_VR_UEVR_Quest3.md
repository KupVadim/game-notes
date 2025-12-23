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

<div style="position:relative;max-width:100%;border-radius:8px;overflow:hidden;">
  <a href="https://www.youtube.com/watch?v=rCY9pY0OvLY" target="_blank" rel="noopener">
    <img
      src="https://img.youtube.com/vi/rCY9pY0OvLY/maxresdefault.jpg"
      alt="Assetto Corsa Rally VR через UEVR"
      style="width:100%;display:block;"
    />
    <div style="
      position:absolute;
      top:50%;
      left:50%;
      transform:translate(-50%,-50%);
      width:68px;
      height:48px;
      background:rgba(0,0,0,0.6);
      border-radius:12px;
      display:flex;
      align-items:center;
      justify-content:center;">
      <svg viewBox="0 0 68 48" width="34" height="24">
        <path d="M66.52 7.74a8 8 0 0 0-5.6-5.66C56.05 0.67 34 0.67 34 0.67s-22.05 0-26.92 1.41a8 8 0 0 0-5.6 5.66A83.4 83.4 0 0 0 0 24a83.4 83.4 0 0 0 1.48 16.26 8 8 0 0 0 5.6 5.66C11.95 47.33 34 47.33 34 47.33s22.05 0 26.92-1.41a8 8 0 0 0 5.6-5.66A83.4 83.4 0 0 0 68 24a83.4 83.4 0 0 0-1.48-16.26z" fill="#FF0000"/>
        <path d="M45 24 27 14v20" fill="#fff"/>
      </svg>
    </div>
  </a>
</div>


!!! danger "Важно"
    Assetto Corsa Rally **не имеет нативного VR**.  
    UEVR — это инжектор. Цель гайда — не «красиво», а **стабильно и играбельно**.

---

## 🎯 Цель гайда

- **Стабильные 72 FPS**
- Предсказуемая яркость (без автоэкспозиции)
- Минимум микростаттеров
- Приоритет читаемости трассы и окружения в VR

!!! info "А можно ли больше FPS"
    Я не ставил задачу сделать больше 72. НО! Думаю что да, можно попробовать подрезать качество деревьев и может быть агрессивнее Foveated Rendering в OpenXR Toolkit. Пробуйте :)

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

!!! important "Не забудь"
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

!!! Info "Используешь OBS для записи"
    Тогда готовься резать качество и внутри OBS:

    - Preset: P4
    - MultiPass: Single
    - LookAhead: disabled

    И качество внутри игры. Я обычно таки режу деревья и делаю 70% разрешение.

---

## ✅ Итог

- UEVR Nightly обязателен
- OpenXR Toolkit реально помогает
- Деревья важнее теней
- 72 FPS достижимы
