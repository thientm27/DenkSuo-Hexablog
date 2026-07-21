---
title: 'The Unity Architecture I Reuse Across Casual Game Projects'
cover: https://telegraph-image-denkstudio.pages.dev/api/cfile/AgACAgUAAyEGAASLAAFR7QACAQ5qXztwb3bHdFvCcqBdqhZOhhXpigAC2hFrG3NK-Fb14sCoTjQJDgEAAwIAA3cAAz0E
top_img: https://telegraph-image-denkstudio.pages.dev/api/cfile/AgACAgUAAyEGAASLAAFR7QACAQ5qXztwb3bHdFvCcqBdqhZOhhXpigAC2hFrG3NK-Fb14sCoTjQJDgEAAwIAA3cAAz0E
swiper_index:
top_group_index:
background: '#fff'
date: 2026-07-21 10:00:00
updated:
top: 10
tags: [Unity, C#, Architecture, Singleton, Design Pattern, MVC, Tutorial]
categories: [Dev Blog, Unity Architecture]
keywords: unity architecture, singleton pattern, MVC unity, game architecture, scriptable object architecture
description: A breakdown of the Unity code architecture I keep reusing across casual game projects — from the Singleton system, UI management, to event-driven data with Scriptable Object Architecture.

---

## 🧩 Why bother with a standard architecture?

After shipping several casual/hyper-casual projects, I learned that without a clear framework from day one, code turns messy fast — especially when handing off, extending features, or coming back to fix things months later. This post walks through the code structure I reuse in most of my projects, along with real code samples.

### 📌 Overall system diagram

<div style="background: #ffffff; border-radius: 12px; padding: 24px; margin: 24px 0;"> <svg width="100%" viewBox="0 0 680 526" role="img" style="font-family: Arial, Helvetica, sans-serif; max-width: 680px; display: block; margin: 0 auto;"> <title>Overall Unity architecture diagram</title> <desc>Entry scene spawns a persistent manager group (UIManager, ResourcesManager, SoArchitecture, SaveDataHandler, AudioManager). Below it, a scene Controller bridges gameplay objects and the View/Popup UI layer.</desc> <defs> <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse"><path d="M2 1L8 5L2 9" fill="none" stroke="#5F5E5A" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></marker> </defs> <rect x="260" y="20" width="140" height="44" rx="8" fill="#F1EFE8" stroke="#5F5E5A" stroke-width="0.5"/> <text x="330" y="42" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#444441">Entry scene</text> <line x1="330" y1="64" x2="330" y2="110" stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/> <rect x="40" y="110" width="580" height="196" rx="20" fill="#EAF3DE" stroke="#3B6D11" stroke-width="0.5"/> <text x="330" y="132" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#27500A">Persistent managers</text> <text x="330" y="150" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#3B6D11">Spawned once, DontDestroyOnLoad</text> <rect x="60" y="160" width="170" height="56" rx="10" fill="#E1F5EE" stroke="#0F6E56" stroke-width="0.5"/> <text x="145" y="178" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#085041">UIManager</text> <text x="145" y="196" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#0F6E56">Views &amp; popups</text> <rect x="245" y="160" width="170" height="56" rx="10" fill="#E1F5EE" stroke="#0F6E56" stroke-width="0.5"/> <text x="330" y="178" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#085041">Resources manager</text> <text x="330" y="196" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#0F6E56">Shared ScriptableObjects</text> <rect x="430" y="160" width="170" height="56" rx="10" fill="#E1F5EE" stroke="#0F6E56" stroke-width="0.5"/> <text x="515" y="178" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#085041">SoArchitecture</text> <text x="515" y="196" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#0F6E56">Event hub (observer)</text> <rect x="150" y="230" width="170" height="56" rx="10" fill="#E1F5EE" stroke="#0F6E56" stroke-width="0.5"/> <text x="235" y="248" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#085041">Save data handler</text> <text x="235" y="266" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#0F6E56">PlayerPrefs + JSON</text> <rect x="340" y="230" width="170" height="56" rx="10" fill="#E1F5EE" stroke="#0F6E56" stroke-width="0.5"/> <text x="425" y="248" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#085041">Audio manager</text> <text x="425" y="266" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#0F6E56">Music &amp; SFX</text> <line x1="330" y1="306" x2="330" y2="350" stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/> <rect x="230" y="350" width="200" height="56" rx="10" fill="#EEEDFE" stroke="#534AB7" stroke-width="0.5"/> <text x="330" y="368" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#3C3489">Scene controller</text> <text x="330" y="386" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#534AB7">Singleton, not persistent</text> <line x1="145" y1="430" x2="270" y2="406" stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/> <line x1="390" y1="406" x2="515" y2="430" stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/> <rect x="50" y="430" width="170" height="56" rx="10" fill="#F1EFE8" stroke="#5F5E5A" stroke-width="0.5"/> <text x="135" y="448" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#444441">Gameplay objects</text> <text x="135" y="466" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#5F5E5A">CarController, ...</text> <rect x="460" y="430" width="170" height="56" rx="10" fill="#FAECE7" stroke="#993C1D" stroke-width="0.5"/> <text x="545" y="448" text-anchor="middle" dominant-baseline="central" font-size="14" font-weight="500" fill="#712B13">View / popup</text> <text x="545" y="466" text-anchor="middle" dominant-baseline="central" font-size="12" fill="#993C1D">Only renders data</text> </svg> </div>

---

## 🏗️ Core principle: the Controller is the single point of communication

The most important rule in this architecture: **objects inside a scene are never allowed to call GUI/View directly**. Every interaction between gameplay and UI must go through that scene's **Controller**.

```
Gameplay Object (e.g. CarController)
        │
        ▼
   Scene Controller (e.g. GameController)
        │
        ▼
      UIView (e.g. GameView) ── only receives data to display
```

For example, inside `GameController`, every frame it pulls data from `CarController` and pushes it to `GameView` to render — `CarController` never calls `GameView` directly:

```csharp
private void UpdateGameplayStats()
{
    if (carController == null || gameView == null) return;

    float distance = carController.DistanceTraveled;

    gameView.UpdateSpeed(carController.CurrentSpeed);
    gameView.UpdateDistance(distance);
}
```

The benefit: gameplay logic stays fully decoupled from UI. Swapping the UI or adding a new view never requires touching gameplay logic.

---

## 🔁 The Singleton system — 3 flavors for 3 different lifetimes

I keep a single `BaseSingleton.cs` file defining 3 kinds of singleton, picked depending on the lifetime I need:

| Type | Behavior | Used for |
|---|---|---|
| `Singleton<T>` | Plain class (`where T : new()`), creates its own instance lazily | Pure logic classes that don't need MonoBehaviour |
| `ManualSingletonMono<T>` | Only returns an instance that **already exists** in the scene — never creates one, logs an error if missing | Manager classes that must be set up in a scene/prefab (UIManager, ResourcesManager, GameController...) |
| `AutoSingletonMono<T>` | Automatically spawns a new GameObject if no instance exists yet | Utility helpers that don't need manual setup |

The neat part: `ManualSingletonMono<T>` never calls `DontDestroyOnLoad` itself — whether it persists across scenes is entirely decided by **where it's instantiated** (see the Entry Scene section below), not by the Singleton base class.

---

## 🚪 Entry Scene — where every persistent system gets bootstrapped

The very first scene (`Entry`) has one job: show a loading bar, then **DontDestroyOnLoad** a single `manager` prefab holding every system-level Manager, before switching to the `Main` scene.

```csharp
private void Awake()
{
    Application.targetFrameRate = 60;
    loadDuration = Random.Range(2, 3);
    DontDestroyOnLoad(manager);
}

private void Start()
{
    slider.value = 0f;
    slider.DOValue(100f, loadDuration)
        .SetEase(Ease.OutCubic)
        .OnComplete(() => { SceneManager.LoadScene(GameConstants.SceneMain); })
        .OnUpdate(() => { textPercenst.text = "Loading..." + Mathf.RoundToInt(slider.value) + "%"; });
}
```

Thanks to this, the managers below **live for the entire lifetime of the app**, independent of scene reloads:

- **UIManager** — manages every Canvas in the game (View + Popup + Alert), spawned from the Entry scene, `DontDestroyOnLoad`.
- **ResourcesManager** — stores and manages shared ScriptableObjects, `DontDestroyOnLoad`.
- **SoArchitectureManager** — the event hub (Scriptable Object Architecture), `DontDestroyOnLoad`.
- **SaveDataHandler** — reads/writes local save data (PlayerPrefs), `DontDestroyOnLoad`.
- **AudioManager** — manages background music and sound effects, `DontDestroyOnLoad`.
- **GameConstants** — shared constants: scene names, popup resource paths...

---

## 🎮 Controller — the brain of each scene

Unlike the Managers above, a **Controller is a singleton but is NOT `DontDestroyOnLoad`** — it only lives within its own scene (`MainController` for the Main scene, `GameController` for the Game scene).

```csharp
public class GameController : ManualSingletonMono<GameController>
{
    private void Start()
    {
        RegisterEvents();
        UIManager.Instance.ViewManager.ShowView(UIViewName.GameView);
        gameView = UIManager.Instance.ViewManager.GetViewByName<GameView>(UIViewName.GameView);
    }
    ...
}
```

The Controller's job:
- Acts as the **only** bridge between the current scene and the `DontDestroyOnLoad` Managers above (UIManager, SoArchitectureManager...).
- Drives input, gameplay state (pause/resume/end game), and pushes data to the matching View.
- Registers/unregisters events right inside `RegisterEvents()` / `UnregisterEvents()` — preventing listener leaks when switching scenes.

---

## 🖼️ The UI system: UIManager → ViewManager & PopupManager

### UIManager
`UIManager` is a `DontDestroyOnLoad` singleton holding references to 3 sub-managers: `ViewManager`, `PopupManager`, `AlertManager`. It also handles the loading screen and scene-transition effects (using DOTween scale in/out).

### View — a full-screen canvas per scene
`UIViewManager` manages **Views** (full-screen canvases per scene, e.g. `MainView`, `GameView`). Built-in features include:
- A history stack of shown views (`LastShownView`) to support a Back button.
- `HideOthersView()` auto-hides other views when showing a new one, avoiding overlapping UI.
- `OnShownCallBack` / `OnHideCallBack` callbacks to keep the topbar and back button in sync.

### Popup — toggle on/off and reused
`UIPopupManager` manages **Popups** (SettingPopup, ShopPopup, TutorialPopup, UpgradePopup...) using 2 dictionaries:
- `_dictPopup`: caches created popup instances → **reused** instead of being recreated over and over.
- `_dictPopupControllers`: dedicated controllers driving the show/hide/animation logic for each popup.

```csharp
public UIPopup GetPopupFromCacheOrCreate(UIPopupName name)
{
    UIPopup popup = GetPopup(name);
    if (popup) return popup; // already exists -> reuse

    popup = CreateDefaultPopup(name); // doesn't exist -> create & cache it
    ...
    return popup;
}
```

Each Popup inherits from `UIPopup` and overrides `OnShowing()` / `OnHiding()` to handle its own logic (e.g. `SettingPopup` pauses/resumes the game automatically when opened/closed).

---

## 📡 Data & Events: SoArchitectureManager, ResourcesManager, SaveDataHandler

### SoArchitectureManager — an Observer pattern built on ScriptableObjects
Instead of systems calling each other directly (which quickly creates tangled dependencies), everything communicates through a **GameEvent** ScriptableObject:

```csharp
public class SoArchitectureManager : ManualSingletonMono<SoArchitectureManager>
{
    public IntGameEvent OnMoneyChangedEvent;
    public GameEvent PauseGame;
    public GameEvent ResumeGame;
}
```

Anything can `AddListener`/`RemoveListener` or `Raise()` without knowing who's listening — reducing coupling between systems (Controllers, Views, and Popups can all listen to `OnMoneyChangedEvent` without holding a direct reference to each other).

### ResourcesManager
A single place to store and load ScriptableObjects shared across the whole game (item data, config...), instead of scattering `Resources.Load` calls everywhere.

### SaveDataHandler
Persists local data via `PlayerPrefs` + `JsonUtility`, auto-saving on app pause/quit/disable, and exposing `RequestSave()` to batch multiple changes and save once in `Update()` instead of saving on every single change (which would cause hitches):

```csharp
private void Update()
{
    if (_requestSave)
    {
        _requestSave = false;
        OnSaveData();
    }
}
```

---

## 🔊 AudioManager

Manages background music and sound effects (SFX), keeps separate volume settings for music/SFX, and is called directly by Popups/Views whenever needed (e.g. `SettingPopup` syncs the volume sliders, `GameView` plays an SFX on button press).

---

## 🧰 Shared Utilities

- **SimplePool** — a lightweight object pool, avoiding repeated Instantiate/Destroy calls (extremely handy for bullets, coins, or any object that spawns constantly in a casual game).
- **SafeArea** — automatically fits UI to the screen's safe area on notched devices, attached directly to the RectTransform of whichever panel needs it.

---

## ✅ Summary: a full play session flow

1. **Entry scene** → `EntryController` shows the loading bar, `DontDestroyOnLoad`s the `manager` prefab, then loads the `Main` scene.
2. **Main scene** → `MainController` shows `MainView`, waiting for the player to hit Play.
3. Pressing Play → `UIManager.Instance.ShowTransition()` → loads the `Game` scene.
4. **Game scene** → `GameController` shows `GameView`, registers events from `SoArchitectureManager`, and every frame pushes gameplay data (`CarController`) to `GameView` to render.
5. Game over → `GameController.ShowEndGame()` → `UIManager.Instance.PopupManager.ShowPopup(...)`.

Throughout this whole flow, every piece only talks to the others through Controllers + Managers + Events — no gameplay object ever reaches into the UI, and no UI ever reaches into gameplay.

---

## 🎯 When is this architecture worth it?

Best suited for:
- **Casual/hyper-casual** projects that need to move fast with several simple scenes (Entry → Main → Game).
- Small teams that need a shared standard new members can onboard onto quickly.

It can feel like overkill for a tiny 1-2 screen prototype — in that case, dropping the Controller/Event layer and calling things directly is often faster.

---

*This post is based on the code framework I keep reusing across projects at Denk Studio.*