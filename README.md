# SpaceBots

SpaceBots is a Unity-based space battle game and research playground combining real-time gameplay in C# with supporting Wolfram Language scripts for procedural generation and AI prototyping.

> Unity project location: `sumo-sim/` (open that folder with Unity Hub or Unity Editor)

Quick facts
- Repository: mxsonwabe/SpaceBots
- Primary languages: Wolfram Language and C# (gameplay)
- Recommended Unity Editor (from project): m_EditorVersion: 6000.3.8f1 (see `sumo-sim/ProjectSettings/ProjectVersion.txt`)

Table of contents
- About
- Features
- Requirements
- Getting started
  - Open in Unity
  - Run in Editor
- Running builds
- Controls
- Project structure
- Data exchange (Wolfram <> Unity)
- Contributing
- License

About

SpaceBots is a small-scale Unity space combat game featuring pilotable robots, configurable AI opponents, and procedurally generated arenas. The repository includes the Unity project (under `sumo-sim/`) and Wolfram Language notebooks/scripts used for content generation, simulation, and analytics.

Features
- Player-controlled SpaceBots with configurable loadouts
- Procedural arena generation and simulation tools implemented in Wolfram Language
- C# gameplay and UI implemented as Unity scripts
- Export/import pipeline to consume Wolfram-generated data in Unity (JSON/CSV recommended)

Requirements
- Unity Editor matching project version (see `sumo-sim/ProjectSettings/ProjectVersion.txt` for exact version). The project was created with:

  m_EditorVersion: 6000.3.8f1

  Open the project in the matching Unity Editor version via Unity Hub to avoid upgrade prompts.
- .NET runtime included with Unity (no separate .NET SDK required to open/runs inside the Editor)
- Mathematica / Wolfram Engine / wolframscript if you want to run the Wolfram notebooks/scripts locally
- Git for cloning

Getting started

1. Clone the repository

```bash
git clone https://github.com/mxsonwabe/SpaceBots.git
cd SpaceBots
```

2. Open the Unity project

- Launch Unity Hub, click "Add", and select the `sumo-sim/` folder inside the cloned repository. Alternatively, open Unity and choose "Open" → select `sumo-sim/`.
- Use the exact Editor version shown in `sumo-sim/ProjectSettings/ProjectVersion.txt` to avoid automatic project upgrades.
- Let Unity import assets (this may take a few minutes on the first import).

3. Run in the Editor

- In the Unity Editor, open the main scene (look under `sumo-sim/Assets/Scenes/` for a scene file such as `Main.unity` — if the scene name differs, open the project and check the Scenes folder).
- Press the Play button to start the game in the Editor.

Running builds

- Open File → Build Settings in Unity.
- Add the main scene(s) to the build list.
- Select target platform and click Build (or Build and Run).

Controls
(These are typical defaults; adjust to the actual Input configuration in the project)
- Movement: WASD or Arrow keys
- Aim / Camera: Mouse
- Primary fire: Left mouse button
- Secondary fire / special: Right mouse button or Space
- Pause / Menu: Esc

Project structure (high-level)
- sumo-sim/
  - Assets/ — Unity assets: scenes, scripts, prefabs, materials, audio
  - ProjectSettings/ — Unity project settings (contains ProjectVersion.txt)
  - Packages/ — Unity package manifest (if present)
- wolfram/ or notebooks/ (if present) — Wolfram Language notebooks and scripts for generation and simulation
- tools/ — helper scripts (exporters, importers, automation)

Data exchange (Wolfram <> Unity)
- Use Wolfram to prototype procedural generation and AI behavior.
- Export generated data from Wolfram as JSON or CSV (JSON recommended for structured data).
- Place exported files in a folder Unity can read at runtime or include them in `Assets/StreamingAssets/` so they are accessible via Application.streamingAssetsPath.

Example Wolfram export pattern

```wolfram
Export["exports/arena1.json", arenaData, "JSON"]
```

Then in Unity, load and parse the JSON into data classes and instantiate scene objects accordingly.

Development notes
- Keep the Unity project version consistent across collaborators to avoid upgrade conflicts.
- Keep data interchange formats (JSON schema) stable; update importers when the schema changes.
- Add unit tests for C# logic where feasible (NUnit/Unity Test Runner).

Contributing
- Fork the repo, create a feature branch (git checkout -b feat/my-bot), make changes, and open a pull request describing your changes and how to test them.
- Include build/run instructions and note any new external dependencies.

License
- No LICENSE file is present in the repository. Add a LICENSE (for example MIT) to make usage terms explicit.

Contact
- Repository owner: mxsonwabe on GitHub

----

If you'd like, I can:
- Open a branch and commit this README.md to the repository (default branch: master), or
- Modify the README to include exact scene names, controls, or screenshots if you point me to them in the repo.
