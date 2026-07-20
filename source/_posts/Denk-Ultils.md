---
title: Denk Ultils
cover: https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QAD1GjrjRp6IMf2AUOFA3kDCXNZyRHDAAK5DGsbkilgV7obd2b7C-aWAQADAgADdwADNgQ
top_img: https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QAD1GjrjRp6IMf2AUOFA3kDCXNZyRHDAAK5DGsbkilgV7obd2b7C-aWAQADAgADdwADNgQ
swiper_index: 10
top_group_index: 10
background: '#fff'
date: 2025-10-12 18:10:18
tags: [ Tutorial, Unity, C#, Utilities, Open Source ]
categories: [ Internal Documentation ]
decription: A lightweight providing commonly used helpers for UI, math, transforms, collections, enums, logging, and more.
top: 10
---

# 🧰 denk-unity-utils

A lightweight **utility library for Unity 6**, providing commonly used helpers for UI, math, transforms, collections,
enums, logging, and more.  
All methods are static and ready to use out-of-the-box.
> 🔗 **GitHub Repository:**  
> [https://github.com/DenkSuo/denk-unity-utils](https://github.com/DenkSuo/denk-unity-utils)

---

## 📦 Table of Contents

| Section                                                        | Description                                                 |
|----------------------------------------------------------------|-------------------------------------------------------------|
| [Installation](#Installation)                                  | How to install and use in Unity                             |
| [DLogger](#DLogger)                                            | Colored log system with tag & custom color                  |
| [LogColors Reference](#LogColors-Reference)                    | List of available log colors                                |
| [DateUtils](#DateUtils)                                        | Date/time parsing and UTC conversion utilities              |
| [EnumExtensions](#EnumExtensions)                              | Add string value attributes to enums                        |
| [RectTransformExtensions](#RectTransformExtensions)            | Quick utilities for UI anchoring and layout                 |
| [UIMath](#UIMath)                                              | Math and geometry helpers for UI and general calculations   |
| [UISetExtensions](#UISetExtensions)                            | Set UI values without triggering callbacks                  |
| [MathExtensions](#MathExtensions)                              | Math operations: clamp, repeat, abs, float↔byte conversions |
| [TransformExtensions](#TransformExtensions)                    | Transform helpers for local/global positions                |
| [OtherExtensions](#OtherExtensions)                            | Miscellaneous handy helpers (Vector3, Color, etc.)          |
| [GameObjectExtension](#GameObjectExtension-(Children-Helpers)) | Get all direct children                                     |
| [MaskExtensions](#MaskExtensions)                              | LayerMask contains check                                    |
| [ActionExtensions](#ActionExtensions)                          | Null-safe Action invoke                                     |
| [ArrayExtensions](#ArrayExtensions)                            | Shuffle, safe index, random element                         |
| [BadWordExtension](#BadWordExtension)                          | Bad word filtering                                          |
| [Credits & Contribution](#Credits--Contribution)               | Credits and contribution info                               |

---

## Installation

1. Download **`denk-unity-utils.unitypackage`** from the **[Releases](../../releases)** page.
2. Double-click the file to automatically import into Unity.
3. Or install via UPM (local package):  
   👉 [Unity Docs](https://docs.unity3d.com/2020.1/Documentation/Manual/upm-ui-local.html)

```csharp
using Utilities;
using Utilities.Exts;
```

---

## DLogger

Lightweight logging utility with colorized tags.  
Ideal for debugging complex systems while keeping your console clean and readable.

### Example Usage

```csharp
DLogger.Log("Hello World");
DLogger.LogWarning("Potential issue!");
DLogger.LogError("Critical failure!", "MySystem", "#FF0000");
```

### Console Output (Unity-like)

### Console Output (Unity-like)

<table>
  <thead>
    <tr>
      <th>Message</th>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
    <tr style="color:#FFFFFF; background-color:#2b2b2b;">
      <td>[DLogger] Hello World</td>
      <td>Info</td>
    </tr>
    <tr style="color:#FFD700; background-color:#2b2b2b;">
      <td>[DLogger] Potential issue!</td>
      <td>Warning</td>
    </tr>
    <tr style="background-color:#2b2b2b;">
      <td>
        <span style="color:#FF0000;">[MySystem]</span>
        <span style="color:#FF6347;"> Critical failure!</span>
      </td>
      <td style="color:#FF6347;">Error</td>
    </tr>
  </tbody>
</table>


> 💡 Works only when `#if !RELEASE` is active — automatically disabled in release builds.  
> Combine with **Scripting Define Symbols** to control build-time logs.

---

## LogColors Reference

Use the `LogColors` static class for consistent color tags in your logs.

```csharp
DLogger.Log("Download Complete", "Network", LogColors.Aqua);
DLogger.LogWarning("Low FPS detected", "Performance", LogColors.Gold);
DLogger.LogError("Missing reference!", "GameManager", LogColors.OrangeRed);
```

<table> <thead> <tr> <th>Color Name</th> <th>Hex Code</th> <th>Preview</th> </tr> </thead> <tbody> <tr><td style="color:#FFFFFF;">White</td><td>
`#FFFFFF`</td><td><div style="width:30px;height:20px;background:#FFFFFF;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#00FFFF;">Aqua</td><td>
`#00FFFF`</td><td><div style="width:30px;height:20px;background:#00FFFF;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#7FFFD4;">Aquamarine</td><td>
`#7FFFD4`</td><td><div style="width:30px;height:20px;background:#7FFFD4;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#40E0D0;">Turquoise</td><td>
`#40E0D0`</td><td><div style="width:30px;height:20px;background:#40E0D0;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#98FB98;">PaleGreen</td><td>
`#98FB98`</td><td><div style="width:30px;height:20px;background:#98FB98;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#9ACD32;">YellowGreen</td><td>
`#9ACD32`</td><td><div style="width:30px;height:20px;background:#9ACD32;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#00FF00;">Lime</td><td>
`#00FF00`</td><td><div style="width:30px;height:20px;background:#00FF00;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#7FFF00;">Chartreuse</td><td>
`#7FFF00`</td><td><div style="width:30px;height:20px;background:#7FFF00;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#ADFF2F;">GreenYellow</td><td>
`#ADFF2F`</td><td><div style="width:30px;height:20px;background:#ADFF2F;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#32CD32;">LimeGreen</td><td>
`#32CD32`</td><td><div style="width:30px;height:20px;background:#32CD32;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FFD700;">Gold</td><td>
`#FFD700`</td><td><div style="width:30px;height:20px;background:#FFD700;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FFA500;">Orange</td><td>
`#FFA500`</td><td><div style="width:30px;height:20px;background:#FFA500;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF4500;">OrangeRed</td><td>
`#FF4500`</td><td><div style="width:30px;height:20px;background:#FF4500;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF6347;">Tomato</td><td>
`#FF6347`</td><td><div style="width:30px;height:20px;background:#FF6347;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF7F50;">Coral</td><td>
`#FF7F50`</td><td><div style="width:30px;height:20px;background:#FF7F50;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF8C00;">DarkOrange</td><td>
`#FF8C00`</td><td><div style="width:30px;height:20px;background:#FF8C00;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF1493;">DeepPink</td><td>
`#FF1493`</td><td><div style="width:30px;height:20px;background:#FF1493;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#FF00FF;">Magenta</td><td>
`#FF00FF`</td><td><div style="width:30px;height:20px;background:#FF00FF;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#EE82EE;">Violet</td><td>
`#EE82EE`</td><td><div style="width:30px;height:20px;background:#EE82EE;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#8A2BE2;">BlueViolet</td><td>
`#8A2BE2`</td><td><div style="width:30px;height:20px;background:#8A2BE2;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#DA70D6;">Orchid</td><td>
`#DA70D6`</td><td><div style="width:30px;height:20px;background:#DA70D6;border:1px solid #ccc;"></div></td></tr> <tr><td style="color:#BA55D3;">MediumOrchid</td><td>
`#BA55D3`</td><td><div style="width:30px;height:20px;background:#BA55D3;border:1px solid #ccc;"></div></td></tr> </tbody> </table>
---

## DateUtils

Utilities for parsing, converting, and formatting date/time in UTC.

### Highlights

- Parse strings to `DateTime`
- Convert milliseconds / seconds / days to UTC
- Get current UTC timestamps
- Format timespans and readable date strings

### Methods

| Method                                         | Description                                           |
|------------------------------------------------|-------------------------------------------------------|
| `ParseStringToDate(string str, string format)` | Parses a string into a `DateTime` object.             |
| `MilisecondToUtcDate(long milliSec)`           | Converts milliseconds since epoch to UTC DateTime.    |
| `SecondToUtcDate(long second)`                 | Converts seconds since epoch to UTC DateTime.         |
| `DayToUtcDate(int day)`                        | Converts day count to UTC DateTime.                   |
| `HourToUtcDate(int hours)`                     | Converts hour count to UTC DateTime.                  |
| `UtcDayNow()`                                  | Gets current UTC day number since epoch.              |
| `UtcSecondNow()` / `UtcMilisecondNow()`        | Gets current UTC timestamp.                           |
| `DateToUtcSecond(DateTime date)`               | Converts a DateTime to epoch seconds.                 |
| `ParseTimeSpanToHHMMSS(TimeSpan span)`         | Formats TimeSpan as `HH:mm:ss`.                       |
| `ToIso8601Weeknumber(DateTime date)`           | Gets ISO week number.                                 |
| `DateToString(DateTime date)`                  | Returns compact string (shows only time if same day). |
| `StartOfWeek()`                                | Returns UTC start of the current week.                |

---

## EnumExtensions

Attach readable strings to enums and retrieve them easily.

```csharp
public enum Fruit
{
    [EnumStringValue("Sweet Apple")] Apple,
    [EnumStringValue("Juicy Orange")] Orange
}

string label = Fruit.Apple.GetStringValue(); // "Sweet Apple"
```

### Members

| Item                                          | Description                                         |
|-----------------------------------------------|-----------------------------------------------------|
| `EnumStringValueAttribute`                    | Attribute to store string labels for enum values.   |
| `GetStringValue<TEnum>(this TEnum enumValue)` | Extension method to fetch the string label or name. |

---

## RectTransformExtensions

A collection of helper methods to manipulate UI layout easily.

### Example

```csharp
var rect = GetComponent<RectTransform>();
rect.FullScreen(true);
rect.SetWidth(300);
rect.SetLeftTopPosition(new Vector2(20, -50));
```

### Common Methods

| Method                                                                          | Purpose                           |
|---------------------------------------------------------------------------------|-----------------------------------|
| `SetDefaultScale()`                                                             | Sets localScale = `Vector3.zero`. |
| `SetPivotAndAnchors(Vector2)`                                                   | Sets pivot and both anchors.      |
| `GetSize()` / `GetWidth()` / `GetHeight()`                                      | Returns rect size info.           |
| `SetLeftTopPosition(Vector2)` / `SetRightBottomPosition(Vector2)`               | Position by corners.              |
| `SetSize(Vector2)` / `SetWidth(float)` / `SetHeight(float)`                     | Resize.                           |
| `Copy(RectTransform from)`                                                      | Copy layout & anchors.            |
| `FullScreen(bool)`                                                              | Match parent bounds.              |
| `Center(bool)`                                                                  | Center in parent.                 |
| `ResetAnchoredPosition3D()` / `ResetLocalPosition()` / `ResetLocalScaleToOne()` | Quick resets.                     |
| `AnchorMinToZero()` / `AnchorMaxToOne()` / `CenterPivot()`                      | Anchor helpers.                   |

---

## UIMath

A compact collection of math helpers—great for UI, color conversion, and positioning.

### Features

- Safe `Lerp`, `ClampIndex`, `RepeatIndex`
- Color ↔ Int/Hex conversion
- Angle wrapping (`WrapAngle`)
- Rect/UV ↔ Pixel conversions
- DPI adjustments & pixel-perfect
- Framerate-independent spring damp/lerp

### Sample

```csharp
float ang = UIMath.WrapAngle(370f); // 10
var uv = UIMath.ConvertToTexCoords(new Rect(0,0,64,64), 256, 256);
```

---

## UISetExtensions

Set values on UI elements **without triggering `OnValueChanged`** events.

### Example

```csharp
myToggle.Set(true, false);
mySlider.Set(0.5f, false);
myDropdown.Set(2);
```

### Supported Components

| Component   | Method                                        |
|-------------|-----------------------------------------------|
| `Toggle`    | `Set(bool value, bool sendCallback = false)`  |
| `Slider`    | `Set(float value, bool sendCallback = false)` |
| `Scrollbar` | `Set(float value, bool sendCallback = false)` |
| `Dropdown`  | `Set(int value)` *(refresh UI)*               |

---

## MathExtensions

General-purpose math helpers for clamping, absolute values, range looping, and data conversion. :
contentReference[oaicite:0]{index=0}

### Features

- `Repeat()` for looping integers or floats between bounds
- `Abs()` / `Clamp()` / `AbsClamp()` chaining
- `ToInt()` for rounded float-to-int
- Convert `float` in range [-1,1] ↔ byte [0,255]

### Methods

| Method                                          | Description                               |
|-------------------------------------------------|-------------------------------------------|
| `Repeat(int value, int min, int max)`           | Loops integer between min/max.            |
| `Repeat(float value, float min, float max)`     | Loops float between min/max.              |
| `Abs(this float value)` / `Abs(this int value)` | Absolute value shortcut.                  |
| `Clamp(this float value)`                       | Clamps between 0 and 1.                   |
| `Clamp(this float value, float min, float max)` | Clamp with custom bounds.                 |
| `AbsClamp()`                                    | Applies Abs then Clamp.                   |
| `ToInt()`                                       | RoundToInt wrapper.                       |
| `ToByte01()` / `ToFloat01()`                    | Encode/decode byte from normalized float. |

### Example

```csharp
float angle = MathExtentions.Repeat(370f, 0f, 360f); // 10
float clamped = (-0.5f).AbsClamp();                  // 0.5
byte encoded = 0.25f.ToByte01();                     // 160
```

---

## TransformExtensions

Helper methods for directly manipulating global, local, and anchored positions. :contentReference[oaicite:1]{index=1}

### Features

- Set global/local X/Y/Z directly
- Work with `RectTransform` anchored positions
- Traverse hierarchy safely
- Fetch topmost parent with specific component

### Common Methods

| Method                                   | Description                                   |
|------------------------------------------|-----------------------------------------------|
| `SetGlobalX/Y/Z()`                       | Change world position axes individually.      |
| `SetLocalX/Y/Z()`                        | Change localPosition axes individually.       |
| `SetAnchoredX/Y/Z()`                     | Change anchoredPosition axes individually.    |
| `CheckParent(this Transform, Transform)` | Checks if transform is child of given parent. |
| `GetTopmostParentComponent<T>()`         | Finds highest ancestor with given component.  |

### Example

```csharp
transform.SetLocalY(2f);
if (transform.CheckParent(root)) Debug.Log("Inside root");
var canvas = child.GetTopmostParentComponent<Canvas>();
```

---

## OtherExtensions

Miscellaneous extra helpers for vectors, colors, and object manipulation (from `OtherExtentions.cs`).  
*(Summary below based on your script content.)*

### Highlights

- **Vector3/2** manipulation (normalize, clamp length, convert)
- **Color extensions** for adjusting alpha or copying RGB
- **Random range** and sign helpers
- **GameObject checks** (`IsDestroyed`, `SetLayerRecursively`, etc.)

### Example

```csharp
Vector3 pos = myTransform.position.WithY(5);
Color halfAlpha = myImage.color.WithAlpha(0.5f);
float randomSign = 1f.RandomSign();
```

---

## GameObjectExtension (Children Helpers)

Helpers to quickly list **direct children** of a `GameObject` or `Transform`. :contentReference[oaicite:5]{index=5}

### Methods

| Method                               | Description                                        |
|--------------------------------------|----------------------------------------------------|
| `GetAllChilds(this GameObject go)`   | Returns `List<GameObject>` of all direct children. |
| `GetAllChilds(this Transform trans)` | Returns `List<Transform>` of all direct children.  |

### Example

```csharp
List<GameObject> childGOs = myGO.GetAllChilds();
List<Transform> childTs  = myGO.transform.GetAllChilds();
```

---

## MaskExtensions

Fast check if a **layer** is contained in a `LayerMask`. :contentReference[oaicite:6]{index=6}

### Method

| Method                                        | Description                          |
|-----------------------------------------------|--------------------------------------|
| `LayerInMask(this LayerMask mask, int layer)` | `true` if `layer` belongs to `mask`. |

### Example

```csharp
if (myMask.LayerInMask(other.gameObject.layer)) { /* hit */ }
```

---

## ActionExtensions

Null-safe helpers to invoke `System.Action` without repetitive null checks. :contentReference[oaicite:7]{index=7}

### Methods

| Method                                                       | Description                         |
|--------------------------------------------------------------|-------------------------------------|
| `SafeInvoke(this Action action)`                             | Invoke if not `null`.               |
| `SafeInvoke<P>(this Action<P> action, P p)`                  | Invoke with 1 param if not `null`.  |
| `SafeInvoke<P1,P2>(this Action<P1,P2> action, P1 p1, P2 p2)` | Invoke with 2 params if not `null`. |

### Example

```csharp
OnCompleted.SafeInvoke();
OnScoreChanged.SafeInvoke(score);
OnPair.SafeInvoke(a, b);
```

---

## ArrayExtensions

Collection helpers: shuffle, safe indexing, random choice. :contentReference[oaicite:8]{index=8}

### Methods

| Method                                  | Description                                         |
|-----------------------------------------|-----------------------------------------------------|
| `Shuffle<T>(this IEnumerable<T> list)`  | Fisher–Yates shuffle (returns new IEnumerable).     |
| `GetSafe<T>(this T[] array, int index)` | Safe index access (`default` if out of range/null). |
| `RandomChoice<T>(this List<T> list)`    | Random element (`Debug.LogError` if null/empty).    |

### Example

```csharp
var shuffled = myList.Shuffle().ToList();
var itemSafe = myArray.GetSafe(5);
var rnd      = myList.RandomChoice();
```

---

## BadWordExtension

VN-friendly bad-word **initialization**, **validation**, and **filtering** utilities.  
Supports diacritics and ignores interleaved symbols (e.g. `b@a#d!` still matches). :contentReference[oaicite:9]{index=9}

### Quick Start

```csharp
// 1) Init once (e.g., on load)
BadWordExtension.Init(new List<string> { "badword", "xấu", "cấm" });

// 2) Validate allowed characters (VN + digits + underscores + spaces)
bool okChars = "tên_hợp_lệ".IsMatchAcceptChars();

// 3) Detect bad words
bool hasBad = "nội dung badword here".IsContainBadwords();

// 4) Filter to "*beep*"
string clean = "đoạn này xấu quá".FilterBadwords();
```

### Methods

| Method                                  | Description                                                              |
|-----------------------------------------|--------------------------------------------------------------------------|
| `Init(List<string> badWords)`           | Prepares regex matchers once. (Must be called before use)                |
| `IsMatchAcceptChars(this string input)` | `true` if only allowed chars (VN diacritics, digits, spaces, `_`, etc.). |
| `IsContainBadwords(this string input)`  | `true` if any bad-word matched.                                          |
| `FilterBadwords(this string input)`     | Replace matched words with `*beep*`.                                     |

> Notes:
> - If not initialized or list empty → returns input unchanged.
> - Pattern tolerates symbols between letters to catch obfuscation.

---

## Credits & Contribution

Developed and maintained by **Benk Studio**.  
Tested and verified on **Unity 6 (6000.0.28f1)**.

🧠 **Contributions Welcome!**  
If you want to add more utilities, extensions, or optimizations — feel free to fork and submit a pull request!

---

**© 2025 Benk Studio — MIT License**  
“Small, clean, and efficient utilities for modern Unity.”

