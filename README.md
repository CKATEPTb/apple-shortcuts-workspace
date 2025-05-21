# 🍒 CherriLang Shortcut Workspace

This branch provides a Docker-based environment to compile `.cherri` files into signed Apple Shortcuts using [CherriLang](https://github.com/electrikmilk/cherri).

## ⚠️ Requirements

- **Linux** system only
- **Docker** and Docker **Compose** installed
- **Familiarity with Docker and Compose usage** (this repo assumes you know the basics)
- **Visual Studio Code** installed (recommended for development)
- **VSCode Extension:** [`CherriLang`](https://marketplace.visualstudio.com/items?itemName=electrikmilk.cherri-vscode-extension) Provides syntax highlighting, linting, and build task integration for `.cherri` files

## 🧱 Project Structure

```
cherrilang/                    ← Tools for compiling and signing iOS Shortcuts
└── core/                      ← Source code of CherriLang (automatically cloned)
└── docker-compose.yml         ← Entry point for build and export process via Docker
└── Dockerfile                 ← Defines the container environment for building CherriLang

workspace/                     ← Root directory for CherriLang-based shortcut projects
└── Template/                  ← Example CherriLang project
└── .vscode/                   ← VSCode build task
└── dist/                      ← Build output directory for compiled shortcuts
└── build.sh                   ← Shortcut build script (invokes Docker flow)
└── index.cherri               ← Main input file defining the Shortcut
└── .../                       ← You can create multiple projects based on the Template
```

## 🚀 Usage

1. Clone this branch:
   ```bash
   git clone -b cherrilang https://github.com/CKATEPTb/apple-shortcuts-workspace.git
   cd apple-shortcuts-workspace
   ```
2. Rename the `Template` folder to match the name of your automation.
   **This is required and non-optional** – the folder name must exactly match the name of the shortcut you're creating.
   Alternatively, you may copy the `Template` folder and use the copy, but the same naming rule still applies.
3. Open the renamed project folder (not the root of the repo) directly in **Visual Studio Code**.
4. Review and complete all `TODO` comments inside the project folder. These mark places where you must adjust or fill in automation-specific logic.
5. Write your shortcut logic inside the `index.cherri` file using [CherriLang syntax](https://cherrilang.org/language/).
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

- [**`cherrilang`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/cherrilang) – contains a `.cherri` template and Docker-based build & sign flow  (you're here)
- [**`jellycuts`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/jellycuts) – contains a `.jelly`  template and Docker-based build & sign flow
- [**`readme`**](https://github.com/CKATEPTb/apple-shortcuts-workspace/tree/readme) – documentation and repository overview