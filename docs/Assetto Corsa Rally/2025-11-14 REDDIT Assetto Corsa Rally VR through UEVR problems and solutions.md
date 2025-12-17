---
created: 2025-12-17T02:15:17+01:00
reviewed:
url: "https://www.reddit.com/r/assettocorsarally/comments/1owtibo/assetto_corsa_rally_vr_through_uevr_problems_and/"
tags:
  - "reddit"
  - "VR"
  - "performance"
  - "exposure"
title: "Assetto Corsa Rally VR through UEVR: problems and solutions"
published: 2025-11-14T12:00:55+01:00
subreddit: "r/assettocorsarally"
description: "Community thread about running Assetto Corsa Rally in VR via UEVR: users share fixes and tips for crashes (often caused by OpenXR Toolkit), exposure/auto‑exposure tweaks via UEVR CVars, performance tuning (DLSS, shadows, reflections), controller/cursor workarounds (JoyToKey, UEVR cursor option), and rendering fixes (Native Stereo, Virtual Desktop settings); general consensus is that the nightly UEVR build + CVars are workable stopgaps until official VR support or engine-side fixes arrive."
---

#webclip/unread

> Posted in **r/assettocorsarally** by *Right-Opportunity810* at 2025-11-14T12:00:55+01:00 (⬆️ 25)

# Assetto Corsa Rally VR through UEVR: problems and solutions





## Comments (50)

## Summary of comments and community opinions

- Overall impression
  - Players are successfully running Assetto Corsa Rally (ACR) in VR by using UEVR (nightly build reported as more stable than the stable build). The experience is generally positive but requires several workarounds for crashes, brightness (auto‑exposure), controls, and some rendering artifacts.

- Main problems reported
  1. Crashes on injection
     - Commonly caused by OpenXR Toolkit (per‑app settings can conflict). Several users solved crashes by disabling the toolkit for ACR or switching to OpenVR. One user fixed injection by switching UEVR’s VR_RenderingMethod to “Native Stereo.”
  2. Brightness / auto‑exposure (overexposed outside world)
     - Unreal Engine auto‑exposure / eye adaptation causes large exposure swings, especially from darker cockpits to bright exteriors. Many users tried CVars and UEVR sliders to reduce bloom/eye‑adaptation and adjust tone mapping. Some report certain CVARs are blocked by the game; others can tweak exposure via UEVR or external injectors (UUU). Recommended CVars include r.DefaultFeature.AutoExposure, r.EyeAdaptationQuality, r.ExposureOffset, r.Color.Mid, r.ToneMapperGamma.
  3. Mouse cursor & UI issues
     - Cursor either hidden or constantly reappearing in VR. UEVR includes an option to always show the cursor; others want auto‑hide. No universal cure reported; some workarounds (JoyToKey for menu navigation or UEVR cursor option) help.
  4. Controls mapping / wheel issues
     - D‑pad and some wheel controls don’t register correctly; suggested fixes include mapping D‑pad to keyboard (JoyToKey) or checking Steam controller mappings and in‑game axis inversion for pedals.
  5. Stereo / sharpness problems and single‑eye displays
     - Some users saw blurry/out‑of‑alignment stereo or in‑car LCD visible only in one eye. Fixes: set LCD quality to LOW (reported), check render method (Native Stereo), and adjust scaling or disable upscalers.
  6. Misc artifacts (corner disappearing objects, odd alignment after headset sleep)
     - Possibly headset/VD or Quest‑specific bugs (Quest 3 sleep bug reported). Users recommended disabling Quest sleep options or verifying Virtual Desktop settings.

## What people recommended (actions & resources)
- Use UEVR nightly build rather than stable for better compatibility and OpenXR support (community observation). (thread: https://www.reddit.com/r/assettocorsarally/comments/1owtibo/assetto_corsa_rally_vr_through_uevr_problems_and/)
- Disable/untick OpenXR Toolkit for the ACR executable (per‑app) to avoid crashes. If you need OpenXR Toolkit for other games, exclude ACR specifically.
- Virtual Desktop settings
  - Use Virtual Desktop with VDXR (or Native Stereo rendering method in UEVR) for better results when streaming to Quest headsets. Virtual Desktop: https://www.meta.com/virtual-desktop/
- Cursor & controls
  - JoyToKey (map D‑Pad to arrow keys or wheel inputs to keyboard) to workaround unmapped inputs: https://joytokey.net/en/
  - UEVR in‑game option: “always show cursor” — helpful when cursor is invisible in VR.
- Exposure / brightness fixes
  - Use UEVR advanced CVars/overlay to tweak exposure/tone mapping live: r.Color.Mid, r.Color.Max/Min, r.ToneMapperGamma, r.ExposureOffset, r.EyeAdaptationQuality. When possible try: r.DefaultFeature.AutoExposure 0 or r.EyeAdaptationQuality 0 (some users report those are blocked by the game). See Unreal auto‑exposure docs for background: https://docs.unrealengine.com/en-US/RenderingAndGraphics/PostProcessEffects/AutoExposure/index.html
  - Disable bloom, lens flare, HDR in game if possible as temporary mitigations.
  - UUU or other injectors can allow runtime console entry for CVars when UEVR cannot write them.
- Upscaling and performance
  - Use DLSS as an upscaler (many found DLSS gives best perf/quality tradeoff); beware frame‑generation doesn’t work for VR — disable FG if you only want upscaling: https://www.nvidia.com/en-us/geforce/technologies/dlss/
  - Reduce certain settings (shadows, dynamic reflections) to improve frame rates. Tip: game + UEVR allow instant slider changes without restarts.
- Other tips
  - If multiple GPUs are present, disable extra GPUs in Device Manager (some users had no image errors because Windows saw many GPUs).
  - If one-eye LCD or stereoscopic offset occurs, try setting the in‑game LCD quality to LOW and verify render method / headset sleep settings.

## CVars & quick test workflow (community suggested)
1. Inject UEVR and launch ACR. Open UEVR → Show Advanced Options → Console/CVars.  
2. Try: r.DefaultFeature.AutoExposure 0 (if accepted). If blocked, test: r.EyeAdaptationQuality 0 (disable) or 2 (different behavior).  
3. Tweak: r.ExposureOffset (recommended range -0.5 to -2.0 for over‑exposure) and r.ToneMapperGamma (~1.8–1.9 reported as usable), r.Color.Mid for midtone control.  
4. Use r.EyeAdaptation.VisualizeDebugType 1 to see what luminance ranges are being sampled (advanced debug). Reference: Unreal docs above.

## My assessment of relevance and likely effectiveness
- Most immediately effective fixes: (1) disable OpenXR Toolkit for the ACR exe (crashes), (2) set UEVR VR_RenderingMethod to Native Stereo (stereo/launch issues), (3) use Virtual Desktop VDXR + correct scaling for Quest users (streaming stability). These are low‑risk and directly address common faults.
- Exposure/auto‑exposure is the single largest quality complaint. CVars via UEVR can help significantly, but some CVars may be blocked by the game build; real fix requires developer changes (exposure metering masks or disabling eye adaptation in certain camera views). So community fixes are mostly stopgaps and will need re‑tuning per stage/time of day.
- Input mapping and cursor issues are solvable via JoyToKey or UEVR cursor toggle; they’re inconvenient but workable.
- Performance tuning (DLSS + reducing reflections/shadows) is very relevant and effective — many report good FPS with high settings and DLSS upscaling.

## Conclusion (practical checklist)
- If ACR crashes on injection: disable OpenXR Toolkit for the ACR exe, or try OpenVR instead; ensure UEVR VR_RenderingMethod = Native Stereo.  
- If brightness/auto‑exposure bothers you: open UEVR advanced CVars and try r.ExposureOffset (-0.5 to -2), r.Color.Mid, r.ToneMapperGamma; disable bloom/HDR in the game; if CVars are blocked, consider UUU or wait for upstream fixes. See Unreal auto‑exposure docs for context: https://docs.unrealengine.com/en-US/RenderingAndGraphics/PostProcessEffects/AutoExposure/index.html
- For missing controls / cursor: try JoyToKey (https://joytokey.net/en/) or UEVR’s cursor option; check Steam controller mappings.
- For performance: use DLSS (NVIDIA): https://www.nvidia.com/en-us/geforce/technologies/dlss/ and tune shadows/reflections; use Virtual Desktop when using Quest headsets: https://www.meta.com/virtual-desktop/

Community thread (source): https://www.reddit.com/r/assettocorsarally/comments/1owtibo/assetto_corsa_rally_vr_through_uevr_problems_and/

If you want, I can extract the exact CVars and values mentioned in the thread into a short, copy‑pasteable list for testing.