# 📋 Changelog

All notable changes to **fancybash** are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] — 2026-06-01

### ✨ Added
- **Docker Swiss Army Knife** — 50+ docker aliases and functions (`dps`, `dsh`, `dwatch`, `dbackup`, `dclean`, `dkill-force`, etc.)
- **Docker tab completion** — press `Tab` after `dsh`, `dlogs`, `dstop` to auto-complete container names
- **`uup` Mega Updater** — interactive `fzf` menu to update OS, Snap, Flatpak, Bun, Node.js, NPM in one shot
- **`uu` Universal Uninstaller** — fuzzy picker across apt/snap/flatpak/AppImage with size & install date info
- **`makecpp`** — advanced C/C++ boilerplate generator (auto cd, Makefile, git init, VSCode tasks)
- **`vite` function** — interactive Vite scaffolder with optional Tailwind CSS v4 setup
- **`ui` function** — Shadcn/UI installer with fzf component picker
- **`css` function** — auto-detects package manager, installs Tailwind + clsx + tailwind-merge
- **`gwip`** — smart WIP commit + auto push to current branch
- **`pg`** — interactive `package.json` generator
- **`run`** — interactive JS/TS file runner via Bun
- **Zsh config** (`config.zsh`) — full port of `config.sh` with zsh-specific features
- **PowerShell config** (`config.ps1`) — initial port (WIP)
- **Linux App Ecosystem page** (`web/linux-setup.html`) — searchable, filterable app browser
- **Zed IDE installer** (`zed/install-settings.sh`) — writes to both Flatpak and native paths
- `ARCHITECTURE.txt` — detailed contributor architecture document
- `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md` — open source standards

### 🔄 Changed
- Prompt system refactored — default is now minimal single-line for speed; full two-line is opt-in
- `pending_updates()` now supports Arch (`checkupdates`), Debian, and fallback apt-get methods
- `cpu_temp()` color thresholds adjusted: green ≤55°C, yellow 55–70°C, red >70°C
- Installer scripts (`install.sh`, `install.zsh`) now validate downloaded file is not an HTML error page
- `setuppc()` updated to include Zsh, fzf, and modern tooling bootstrap

### 🐛 Fixed
- `get_duration()` timer reset issue on rapid command execution
- `ex()` archive extractor — added `.7z` support
- `check_readonly()` false positive on certain network-mounted directories

---

## [1.0.1] — 2025-11-15

### ✨ Added
- `kp <port>` — kill process by port number
- `iploc` — show IP + city/region/org info via ipinfo.io
- `deno` support in `rt()` runtime installer
- `battery_info()` prompt metric for laptop users
- `check_readonly()` — shows 🔒 when directory is not writable

### 🔄 Changed
- `rand_emoji()` now detects `bun`, `py`, `proj` folder patterns
- `gwip` now falls back to "Work in progress (Save Point)" if no message given
- Improved installer header with box-drawing characters

### 🐛 Fixed
- `parse_git_branch()` — no longer prints error in non-git directories
- `ff()` — now correctly skips `.git` and `node_modules`
- `gen()` — fixed output truncation for lengths > 64

---

## [1.0.0] — 2025-08-01

### 🎉 Initial Release
- Core prompt system with `rand_color()`, `rand_emoji()`, `parse_git_branch()`
- System monitoring: `cpu_temp()`, `disk_usage()`, `load_avg()`, `get_duration()`
- Navigation aliases: `..`, `...`, `....`, `dev`, `fr`, `ba`, `fu`
- NPM aliases: `ni`, `nid`, `nr`, `nrd`, `nrb`, `nrs`
- Bun aliases: `bi`, `br`, `brd`, `brb`, `brs`, `html`
- Git shortcuts: `gs`, `ga`, `gcm`, `gps`, `gpl`, `gl`, `gco`, `gcb`, `gd`
- Git stash: `gst`, `gsta`, `gpop`
- Utility tools: `mkd`, `rmd`, `rmf`, `bak`, `trash`, `ex`, `ff`, `gen`, `h`
- System tools: `update`, `clean`, `myip`, `ports`, `serve`, `rel`
- `keep()` — inline command reference cheatsheet
- `init()` — interactive Bun/NPM project initializer
- `next()` — Next.js scaffolder
- `setuppc()` — new PC bootstrap script
- One-line installer with spinner, backup, and idempotency guard
- MIT License
- Static website (`web/`) on Netlify

---

[2.0.0]: https://github.com/rihadjahanopu/fancybash/compare/v1.0.1...v2.0.0
[1.0.1]: https://github.com/rihadjahanopu/fancybash/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/rihadjahanopu/fancybash/releases/tag/v1.0.0
