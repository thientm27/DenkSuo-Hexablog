---
title: 'Isles of Behemoths'
published: false
cover: https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADlGhsakuRub-ySQQCiEGFTf1GHfDWAAJYxjEbA0FpVyLknTwgFMvgAQADAgADdwADNgQ
top_img: https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADlGhsakuRub-ySQQCiEGFTf1GHfDWAAJYxjEbA0FpVyLknTwgFMvgAQADAgADdwADNgQ
swiper_index: 12
top_group_index: 12
background: '#fff'
date: 2025-07-09 18:00:00
tags: [3D, Idle, Simulation, Casual, Mobile, iOS, Android, Unity]
categories: [Game Showcase, Mobile Game]
description: Raise elemental monsters, evolve powerful Behemoths, and harvest resources across mystical islands in this idle creature simulation.
---

## 🐲 Isles of Behemoths — Idle Monster Raising Adventure

**Welcome to the ancient archipelago of power.**  
In **Isles of Behemoths**, you manage your very own mystical islands, raise elemental Behemoths, collect magical fruits, and unlock the secrets of an ancient civilization through idle gameplay and strategic upgrades.

---

### 📝 Overview

- 🎮 **Genre**: Idle / Simulation / Monster Raising
- 🌍 **Platform**: Android, iOS
- 🎨 **Art Style**: 3D Cartoon, Bright Colors, Stylized Islands
- 🧩 **Gameplay Loop**: Raise → Feed → Harvest → Unlock → Evolve

---

### 🌴 Lore & Concept

You’ve arrived at a forgotten archipelago of 10 elemental islands and a central core island.  
Each island is home to a mighty Behemoth, waiting to be hatched and raised.  
The **Central Island** holds 5 elemental trees and the **Potion Machine**, used to:

- 🌱 Grow elemental fruits (Metal, Wood, Water, Fire, Earth)
- ⚗️ Accelerate egg hatching and digestion

---

### ⚙️ Core Gameplay Features

#### 🏝️ 1. Islands & Behemoths

- Each island hosts **1 Behemoth**
- Players unlock new islands using coins
- Hatching a new Behemoth costs:  
  `Cost = 300 * number_of_eggs_purchased_on_island`
- Feeding generates **coins & EXP**
- Behemoths can be released to raise another

---

#### 🥚 2. Egg Hatching

- Each monster has its own incubation time (in hours)
- Speed up using **Magic Potions**

---

#### 🍎 3. Energy Fruits & Potion Machine

| Source             | Purpose                                   |
|--------------------|-------------------------------------------|
| Elemental Trees    | Produce fruits matching Behemoth element  |
| Potion Machine     | Boosts digestion & egg hatch time         |

- ⏱ Production rate: Every 10 minutes
- 📈 Fruit Formula: `Fruits = 3 * (level + 1)`
- 🔧 Upgrade cost: `10 * next_level`

---

#### 📈 4. Behemoth Level Formula

- Next_Level_EXP = Current_Level * Evolution_Index * Base_EXP

---

#### 🌞 5. Harvest & Daily Quests

- Feed Behemoths → Wait → Collect coins & EXP
- Daily Quest Examples:
    - Feed Behemoth: 1 / 3 / 10 times → Get Coins
    - Harvest Fruit: 10 / 20 / 30 fruits → Get Coins

---

### 🗺️ Island Configuration

| ID | Name (EN)         | Name (VI)                 | Unlock Level | Price | Hatch Time (hr) | Base EXP | Evo Index |
|----|-------------------|---------------------------|--------------|-------|---------------|-------|--------|
| 1  | Mystic Meadow     | Đồng Cỏ Huyền Bí          | 1            | 0     | 1             | 100   | 1.2    |
| 2  | Ember Volcano     | Núi Lửa Hừng Cháy         | 5            | 500   | 2             | 120   | 1.3    |
| 3  | Frozen Tundra     | Lãnh Nguyên Băng Giá      | 10           | 1000  | 3             | 150   | 1.4    |
| 4  | Aqua Lagoon       | Đầm Phá Thuỷ Tinh         | 15           | 1500  | 4             | 180   | 1.5    |
| 5  | Rocky Highlands   | Cao Nguyên Đá             | 20           | 2000  | 5             | 200   | 1.6    |
| 6  | Stormy Peaks      | Đỉnh Bão Tố               | 25           | 2500  | 6             | 220   | 1.7    |
| 7  | Shadow Grove      | Rừng Bóng Tối             | 30           | 3000  | 7             | 250   | 1.8    |
| 8  | Crystal Cavern    | Hang Pha Lê               | 35           | 3500  | 8             | 280   | 1.9    |
| 9  | Golden Savannah   | Thảo Nguyên Vàng          | 40           | 4000  | 9             | 300   | 2.0    |
| 10 | Ancient Ruins     | Tàn Tích Cổ Đại           | 45           | 5000  | 10            | 350   | 2.2    |
| 0  | Central Island    | Đảo Trung Tâm             | 1            | 0     | -             | -     | -      |

---

### 🐉 Behemoth Configuration

| ID | Name (EN)     | Name (VI)       | Element | Base EXP | Evo Index | Hatch (hr) | Digest (min) | Rarity (%) |
|----|---------------|-----------------|---------|----------|-----------|-------------|----------------|-------------|
| 1  | Flarehorn     | Sừng Lửa        | Fire    | 100      | 1.2       | 1           | 30             | 50%         |
| 2  | AquaTail      | Đuôi Thuỷ       | Water   | 120      | 1.3       | 2           | 35             | 50%         |
| 3  | Rockback      | Lưng Đá         | Earth   | 150      | 1.4       | 3           | 40             | 30%         |
| 4  | Windpaw       | Chân Gió        | Wood    | 90       | 1.1       | 1           | 25             | 50%         |
| 5  | Ironhide      | Da Sắt          | Metal   | 130      | 1.25      | 2           | 32             | 30%         |
| 6  | Emberclaw     | Vuốt Lửa        | Fire    | 110      | 1.2       | 2           | 30             | 20%         |
| 7  | Frosthorn     | Sừng Băng       | Water   | 125      | 1.3       | 3           | 35             | 20%         |
| 8  | Mudjaw        | Hàm Bùn         | Earth   | 140      | 1.35      | 4           | 38             | 10%         |
| 9  | Skyserpent    | Rồng Trời       | Wood    | 95       | 1.1       | 3           | 28             | 10%         |
| 10 | Steelscale    | Vảy Sắt         | Metal   | 135      | 1.25      | 5           | 32             | 5%          |

---

### 🌟 Elemental Trees (Central Island)

| Element | Start Level | Production Time | Base Output | Upgrade Cost       | Output Formula         |
|---------|-------------|------------------|-------------|---------------------|-------------------------|
| Metal   | 0           | 10 min           | 3 fruits    | `10 * next_level`   | `3 * (level + 1)`       |
| Wood    | 0           | 10 min           | 3 fruits    | `10 * next_level`   | `3 * (level + 1)`       |
| Water   | 0           | 10 min           | 3 fruits    | `10 * next_level`   | `3 * (level + 1)`       |
| Fire    | 0           | 10 min           | 3 fruits    | `10 * next_level`   | `3 * (level + 1)`       |
| Earth   | 0           | 10 min           | 3 fruits    | `10 * next_level`   | `3 * (level + 1)`       |

---

#### 🖼 Screenshots

<div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px;">
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADlGhsakuRub-ySQQCiEGFTf1GHfDWAAJYxjEbA0FpVyLknTwgFMvgAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADlWhsalHbZC4zbokDsIjLo2D2ZoTeAAJZxjEbA0FpV5CN7lKR76ZoAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADk2hsakfBMOhufBC0uvSZmQq9XTVdAAJXxjEbA0FpVxIlZsB-YKUwAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADkmhsakJ3Sg65vd3LkXQ2gmfCfzyvAAJWxjEbA0FpV6aBrrAF7zj9AQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADkGhsajee4-Xso-v28qjjXXOAjnkZAAJUxjEbA0FpVz9Ger81TgOGAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADj2hsajFSKpxD1jivM7VJ0LMKmUHNAAJTxjEbA0FpV4eP2OLXo-hXAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADjmhsaiulPTEiQB8ZpzTUwTOhJ2OPAAJSxjEbA0FpVzDDqZKzmqR0AQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADjmhsaiulPTEiQB8ZpzTUwTOhJ2OPAAJSxjEbA0FpVzDDqZKzmqR0AQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADjWhsaiUbsq9fQH_UKC9PzIL74LqJAAJRxjEbA0FpV1TbWKDQruXDAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADlmhsalW2bg05rv1MyUVlPV-UQ1cyAAJaxjEbA0FpV1oyeb02bV1iAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADl2hsalmKEOJeFEctXJN6vNl5wWCBAAJbxjEbA0FpV_6D8euZzT5yAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADmGhsal0_xQzkJEWP67tzo-kr0HFOAAJcxjEbA0FpV8cFTZb1vsKGAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADmWhsamDWhbpfEpd9TwL7na2W18JRAAJdxjEbA0FpVwrf2OnDD_PiAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADmmhsamRpdlEaPwR03D1Z7zbQZhC3AAJexjEbA0FpVzbqoykDp7BVAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADm2hsammiGe9_9YFmKARyXhU1uH5TAAJfxjEbA0FpV12kAY_PEL60AQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADnGhsam6NhRLQ1KJuXNPtvGFlBwL0AAJgxjEbA0FpV3BjoH2bdIEvAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADnWhsanPFATCtFf33XluMmpmqat8MAAJhxjEbA0FpV0kbixSrdy5gAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
  <img src="https://iamge.benkstudio.com/api/cfile/AgACAgUAAyEGAASLAAFR7QADnmhsancy6vwi395MBeViwwGAhL5tAAJixjEbA0FpV2m6tc4NXanyAQADAgADdwADNgQ" style="width: 100%; border-radius: 8px;" />
</div>

---
*Post by Benk Studio Team*  
*thientm27*


