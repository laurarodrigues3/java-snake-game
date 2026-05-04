# Java Snake Game

![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)

A Java-based Snake game demonstrating advanced Object-Oriented Programming (OOP) principles, custom 2D collision algorithms, and automated gameplay modes.

## Features

* **Multiple Gameplay Modes:**
  * **Manual Mode:** Classic arrow-key navigation.
  * **Auto-Play (Pathfinding):** Advanced algorithmic navigation that calculates real-time distances to food vectors to dynamically select the optimal safe path.
  * **Auto-Play (Basic):** Simple coordinate-directed automated movement.
* **Custom Geometric Collision Engine:** Built from scratch to handle exact collisions using custom polygon, circle, and line segment mathematical representations.
* **Dynamic Environment:** Features rotating obstacles, variable arena dimensions, and alternating visual representations for power-ups.
* **Persistent Leaderboard:** Local space data persistence using Java I/O serialization to track high scores.
* **Audio Integration:** Asynchronous in-game soundtrack execution using Java Sound API.

## Architecture & OOP Concepts

The codebase is heavily modularized to demonstrate strict adherence to clean software engineering attributes:

* **Design Patterns:** Implementation of the **Strategy Pattern** for hot-swapping movement algorithms (Manual vs Auto) and **Factory Pattern** nuances for diverse entity generation.
* **Inheritance & Polymorphism:** Abstract foundational classes (`Poligono`, `Comida`) enabling polymorphic dispatch for unified hit-detection and rendering logic.
* **Interfaces:** Completely decoupled movement behavior definitions (`MovimentoSnake`, `MovimentoObstaculo`).
* **Encapsulation:** Substantial isolation of components, restricting inappropriate mutations of `Arena` or `Jogador` states.

## Getting Started

### Prerequisites

* Java Development Kit (JDK) 8 or higher.
* *[Optional]* JUnit 5 for executing the geometric engine test suites.

### Installation & Execution

*(In a professional environment, this project would use Maven or Gradle. Below are instructions for native java execution).*

#### 1. Compile Source Files

Navigate to the project's root folder and compile the Java class files into an `out` directory:

```bash
# Windows (PowerShell)
javac -d out (Get-ChildItem src\*.java | Where-Object { $_.Name -notlike '*Test.java' } | ForEach-Object { $_.FullName })

# Linux / Bash / macOS
javac -d out src/*.java
```

#### 2. Launching

Ensure the `Snake3Music.wav` audio file is present within the execution root directory:

```bash
java -cp out Main
```

*(For developers using IDEs like IntelliJ IDEA or Eclipse: Simply open the project folder, designate the `src` directory as the 'Source Root', and execute the `Main.java` class directly).*

## Project Structure

```text
snakeGame/
├── src/
│   ├── Main.java                 # Entry point
│   ├── Jogo.java                 # Core game loop & session controller
│   ├── Arena.java                # Rendering & state isolation
│   ├── Food System/              # Abstractions for varying consumables
│   ├── Movement System/          # Strategy implementations for entity actions
│   ├── UI Components/            # Swing interfaces (Menu, Settings)
│   ├── Game Services/            # I/O Ranking Persistence & Audio playback
│   ├── Geometry Library/         # Mathematical models for 2D colliders
│   └── Tests/                    # JUnit suite for geometric validation
└── Snake3Music.wav               # Soundtrack resource file
```

## Testing framework

The custom 2D Geometry Engine is heavily guarded by unit tests. If you wish to run the validation suite using the Terminal (assuming JUnit standalone is on your classpath):

```bash
javac -cp ".:junit-platform-console-standalone.jar" src/*.java
java -cp ".:junit-platform-console-standalone.jar" org.junit.platform.console.ConsoleLauncher --class-path src --scan-class-path
```

## Development Notes

Developed to model architecture and clean code applications utilizing native Java components and Swing.

---

This project was developed as part of a university Object-Oriented Programming course.
