# 🪼 Jellycuts Shortcut Workspace

This branch provides a Docker-based environment to compile `.jelly` files into signed Apple Shortcuts using [Open-Jelly](https://github.com/OpenJelly/Open-Jellycore).

## ⚠️ Requirements

- **Linux** system only
- **Docker** and Docker **Compose** installed
- **Familiarity with Docker and Compose usage** (this repo assumes you know the basics)
- **Visual Studio Code** installed (recommended for development)
- **VSCode Extension:** [`Jellycuts`](https://marketplace.visualstudio.com/items?itemName=ActuallyZach.jelly-language-support) Provides syntax highlighting, linting, and build task integration for `.jelly` files

## 🧱 Project Structure

```
jellycore/                     ← Tools for compiling and signing Apple Shortcuts
└── core/                      ← Source code of Jellycore (automatically cloned)
└── docker-compose.yml         ← Entry point for build and export process via Docker
└── Dockerfile                 ← Defines the container environment for building Jellycuts

workspace/                     ← Root directory for jellycuts-based shortcut projects
└── Template/                  ← Example jellycuts project
└── .vscode/                   ← VSCode build task
└── dist/                      ← Build output directory for compiled shortcuts
└── build.sh                   ← Shortcut build script (invokes Docker flow)
└── index.jelly                ← Main input file defining the Shortcut
└── .../                       ← You can create multiple projects based on the Template
```

## 🚀 Usage

1. Clone this branch:
   ```bash
   git clone -b jellycuts https://github.com/CKATEPTb/apple-shortcuts-workspace.git
   cd apple-shortcuts-workspace
   ```
2. Rename the `Template` folder to match the name of your automation.
   **This is required and non-optional** – the folder name must exactly match the name of the shortcut you're creating.
   Alternatively, you may copy the `Template` folder and use the copy, but the same naming rule still applies.
3. Open the renamed project folder (not the root of the repo) directly in **Visual Studio Code**.
4. Review and complete all `TODO` comments inside the project folder. These mark places where you must adjust or fill in automation-specific logic.
5. Write your shortcut logic inside the `index.jelly` file using [Jellycuts syntax](https://docs.jellycuts.com).
6. Build the project by either:
   * Running the build.sh script:
   ```bash
   ./build.sh
   ```
   * Using the default build task in VSCode (e.g., `Ctrl+Shift+B` on Linux)

   After successful compilation and signing, the final output will appear in:
    ```pgsql
    ./dist/
    ├── unsigned.shortcut          ← Raw (unsigned) shortcut
    └── [name].shortcut            ← Signed, ready-to-import shortcut
    ```

## 🔀 Branches

- [**`cherrilang`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/cherrilang) – contains a `.cherri` template and Docker-based build & sign flow
- [**`jellycuts`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/jellycuts) – contains a `.jelly`  template and Docker-based build & sign flow (you're here)
- [**`readme`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/readme) – documentation and repository overview