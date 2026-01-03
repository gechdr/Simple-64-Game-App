# 🎮 Game 64 - Simple Puzzle Game

<div align="center">

![Android](https://img.shields.io/badge/Android-3DDC84?logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-1.9.0-7F52FF?logo=kotlin&logoColor=white)
![SDK](https://img.shields.io/badge/SDK-34-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green.svg)

**A simplified 2048-style puzzle game on a 3x3 grid - reach 64 to master the game!**

[Features](#-features) • [Screenshots](#-screenshots) • [Installation](#-installation) • [How to Play](#-how-to-play) • [Contributing](#-contributing)

</div>

---

## 📖 Overview

Game 64 is a native Android puzzle game inspired by the popular 2048 game. Instead of the traditional 4x4 grid aiming for 2048, this simplified version uses a 3x3 grid where the goal is to reach the tile value of 64. Slide tiles in four directions, merge matching numbers, and strategize your way to victory!

Built with Kotlin and modern Android development practices using View Binding.

## ✨ Features

### 🎯 Core Gameplay

| Feature | Description |
|---------|-------------|
| **3x3 Grid** | Compact puzzle board for quick gameplay |
| **Tile Merging** | Combine matching tiles to double their value |
| **4-Direction Controls** | Swipe up, down, left, or right |
| **Score Tracking** | Points awarded for each merge |
| **Game Over Detection** | Automatic detection when no moves remain |

### 🎨 Visual Design

- **Color-coded Tiles** - Each value has a unique pastel color
- **Clean UI** - Minimalist design for distraction-free gameplay
- **Smooth Animations** - Tiles slide and merge seamlessly

### 📱 Additional Features

- **How to Play Guide** - In-app instructions for new players
- **SMS Feedback** - Send feedback directly via SMS with auto-generated reference number
- **Quick Restart** - Easy navigation back to menu

### 🎨 Tile Colors

| Value | Color |
|:-----:|:-----:|
| 2 | 🟨 Light Yellow |
| 4 | 🩷 Light Pink |
| 8 | 🟣 Light Purple |
| 16 | 🩵 Light Blue |
| 32 | 🩵 Light Cyan |
| 64 | 🟢 Light Green |

## 📱 Screenshots

| Main Menu | Gameplay | Game Over |
|:---:|:---:|:---:|
| ![Menu](screenshots/menu.png) | ![Play](screenshots/gameplay.png) | ![Over](screenshots/gameover.png) |

| Guide | Feedback |
|:---:|:---:|
| ![Guide](screenshots/guide.png) | ![Feedback](screenshots/feedback.png) |

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| [Kotlin](https://kotlinlang.org/) | Primary programming language |
| [View Binding](https://developer.android.com/topic/libraries/view-binding) | Type-safe view access |
| [Material Components](https://material.io/develop/android) | UI components and theming |
| [ConstraintLayout](https://developer.android.com/training/constraint-layout) | Flexible UI layouts |

## 📋 Requirements

- **Android Studio**: Hedgehog (2023.1.1) or later
- **Minimum SDK**: API 34 (Android 14)
- **Target SDK**: API 34
- **JDK**: 1.8+

## 🚀 Installation

### Clone the Repository

```bash
git clone https://github.com/gechdr/Simple-64-Game-App.git
cd Simple-64-Game-App
```

### Open in Android Studio

1. Launch **Android Studio**
2. Select **File > Open**
3. Navigate to the cloned repository
4. Click **OK** and wait for Gradle sync

### Build and Run

```bash
# Build the project
./gradlew build

# Install on connected device/emulator
./gradlew installDebug
```

Or click the **Run** button (▶️) in Android Studio.

## 📁 Project Structure

```
Simple-64-Game-App/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/tugasm3_6958/
│   │   │   │   ├── MainActivity.kt      # Main menu screen
│   │   │   │   ├── PlayActivity.kt      # Game logic & UI
│   │   │   │   └── GuideActivity.kt     # How to play guide
│   │   │   │
│   │   │   ├── res/
│   │   │   │   ├── layout/
│   │   │   │   │   ├── activity_main.xml    # Menu layout
│   │   │   │   │   ├── activity_play.xml    # Game board layout
│   │   │   │   │   └── activity_guide.xml   # Guide layout
│   │   │   │   ├── drawable/
│   │   │   │   │   └── shape_rounded.xml    # Rounded corners
│   │   │   │   └── values/
│   │   │   │       ├── colors.xml           # Tile colors
│   │   │   │       └── themes.xml           # App theme
│   │   │   │
│   │   │   └── AndroidManifest.xml
│   │   │
│   │   └── test/
│   │
│   └── build.gradle.kts
│
├── gradle/
│
└── README.md
```

## 🏗️ Architecture

### App Flow

```
┌─────────────────┐
│  MainActivity   │
│   (Main Menu)   │
└────────┬────────┘
         │
    ┌────┼────────────┐
    │    │            │
    ▼    ▼            ▼
┌──────┐ ┌──────┐ ┌──────────┐
│ Play │ │Guide │ │ Feedback │
│ Game │ │      │ │  (SMS)   │
└──────┘ └──────┘ └──────────┘
```

### Game Board Structure

```
┌─────────────────────────┐
│  panel11  panel12  panel13  │  Row 0
├─────────────────────────┤
│  panel21  panel22  panel23  │  Row 1
├─────────────────────────┤
│  panel31  panel32  panel33  │  Row 2
└─────────────────────────┘
   Col 0    Col 1    Col 2
```

### Game Logic

```
┌─────────────────────────────────────────┐
│              Player Move                │
│         (Up/Down/Left/Right)            │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│         Slide All Tiles                 │
│    (Move to empty spaces)               │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│         Merge Matching Tiles            │
│    (2+2=4, 4+4=8, etc.)                 │
│    (Add merged value to score)          │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│      Spawn New "2" Tile                 │
│    (Random empty position)              │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│        Check Game Over                  │
│  (No empty tiles + No possible merges)  │
└─────────────────────────────────────────┘
```

## 🎮 How to Play

### Objective

Combine tiles with the same number to create higher values. The goal is to reach **64**!

### Controls

| Button | Action |
|:------:|--------|
| ⬆️ **UP** | Slide all tiles upward |
| ⬇️ **DOWN** | Slide all tiles downward |
| ⬅️ **LEFT** | Slide all tiles left |
| ➡️ **RIGHT** | Slide all tiles right |

### Rules

1. **Start** - Game begins with one tile showing "2"
2. **Slide** - Press a direction button to slide all tiles
3. **Merge** - When two tiles with the same number collide, they merge into one tile with double the value
4. **New Tile** - After each valid move, a new "2" tile appears in a random empty spot
5. **Score** - Each merge adds the merged tile's value to your score
6. **Win** - Reach a tile with value 64
7. **Game Over** - When no valid moves remain (grid full, no possible merges)

### Merge Chain

```
2 → 4 → 8 → 16 → 32 → 64 🏆
```

### Strategy Tips

- **Corner Strategy** - Try to keep your highest tile in a corner
- **Build Chains** - Arrange tiles in ascending order
- **Plan Ahead** - Think about where the new tile might appear
- **Avoid Trapping** - Don't let small tiles block larger ones

## 🔧 Configuration

### Customizing Tile Colors

Edit `app/src/main/res/values/colors.xml`:

```xml
<color name="no2">#FBF8CB</color>   <!-- Tile 2 -->
<color name="no4">#FFCFD2</color>   <!-- Tile 4 -->
<color name="no8">#CEBAEF</color>   <!-- Tile 8 -->
<color name="no16">#8FDBF3</color>  <!-- Tile 16 -->
<color name="no32">#98F5E2</color>  <!-- Tile 32 -->
<color name="no64">#BAFBC1</color>  <!-- Tile 64 -->
```

### Expanding the Grid

To convert to a 4x4 grid (like original 2048):

1. Add additional panels in `activity_play.xml`
2. Expand the `arrPanel` array in `PlayActivity.kt`
3. Update loop ranges from `0..2` to `0..3`
4. Add colors for tiles 128, 256, 512, 1024, 2048

### Changing Starting Tile

Edit `PlayActivity.kt`:

```kotlin
// Change initial tile value (default: 2)
firstBtn.text = ("2").toString()

// Or randomize between 2 and 4
firstBtn.text = if (Random.nextBoolean()) "2" else "4"
```

## 🧪 Testing

### Run Unit Tests

```bash
./gradlew test
```

### Run Instrumented Tests

```bash
./gradlew connectedAndroidTest
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Feature Ideas

- [ ] Swipe gesture controls
- [ ] Undo last move
- [ ] High score persistence
- [ ] 4x4 grid mode (classic 2048)
- [ ] Animations for tile movement
- [ ] Sound effects
- [ ] Dark mode support
- [ ] Multiple difficulty levels
- [ ] Timer mode
- [ ] Leaderboard
- [ ] Achievement system
- [ ] Share score on social media

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

## 🙏 Acknowledgments

- Inspired by [2048](https://play2048.co/) by Gabriele Cirulli
- [Android Developers](https://developer.android.com/) - Official documentation
- [Material Design](https://material.io/) - Design guidelines
- [Kotlin](https://kotlinlang.org/) - Programming language

---

<div align="center">

**Built with Kotlin**

[🔝 Back to Top](#-game-64---simple-puzzle-game)

</div>
