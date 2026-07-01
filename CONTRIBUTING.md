# 🤝 Contributing to fancybash

First off — **thank you for considering a contribution!** Every alias, bug fix, and idea makes fancybash better for developers everywhere.

<div align="center">

[![GitHub Issues](https://img.shields.io/github/issues/rihadjahanopu/fancybash?style=for-the-badge&color=a855f7)](https://github.com/rihadjahanopu/fancybash/issues)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-22c55e?style=for-the-badge)](https://github.com/rihadjahanopu/fancybash/pulls)

</div>

---

## 📋 Table of Contents

- [Code of Conduct](#-code-of-conduct)
- [Ways to Contribute](#-ways-to-contribute)
- [Getting Started](#-getting-started)
- [Development Workflow](#-development-workflow)
- [What to Work On](#-what-to-work-on)
- [Coding Standards](#-coding-standards)
- [Commit Message Format](#-commit-message-format)
- [Pull Request Process](#-pull-request-process)
- [Testing Your Changes](#-testing-your-changes)

---

## 📜 Code of Conduct

This project follows our [Code of Conduct](CODE_OF_CONDUCT.md).  
By participating, you agree to uphold a welcoming and respectful environment.

---

## 💡 Ways to Contribute

| Type | Examples |
|------|---------|
| 🐛 **Bug Fix** | Fix a broken alias, handle edge case in a function |
| ✨ **New Feature** | Add a new alias category, interactive script, or prompt metric |
| 📖 **Documentation** | Improve README, fix typos, add examples |
| 🌐 **Web** | Improve `web/` landing page design or Linux App list |
| 🐚 **Zsh/PS port** | Port a Bash feature to Zsh or PowerShell |
| 🔧 **CI/CD** | Improve GitHub Actions workflows |
| 💬 **Ideas** | Open an issue with a suggestion |

---

## 🚀 Getting Started

### 1. Fork & Clone

```bash
# Fork on GitHub first, then:
git clone https://github.com/YOUR_USERNAME/fancybash.git
cd fancybash
```

### 2. Understand the Structure

Read [ARCHITECTURE.txt](ARCHITECTURE.txt) — it explains every file and
every section of `config.sh` in detail.

### 3. Create a Branch

```bash
git checkout -b feat/my-awesome-feature
# or
git checkout -b fix/broken-docker-alias
```

---

## 🔄 Development Workflow

```
1. Edit config.sh (and config.zsh if applicable)
2. Test locally: source config.sh in a test shell
3. Run shellcheck: shellcheck -s bash config.sh
4. Update README.md if the feature is user-facing
5. Update keep() function if adding a new command
6. Commit with proper message format
7. Open a Pull Request
```

---

## 🎯 What to Work On

Check the [open issues](https://github.com/rihadjahanopu/fancybash/issues) for tasks labeled:

- `good first issue` — great for newcomers
- `help wanted` — maintainer needs community help
- `enhancement` — approved feature ideas
- `bug` — confirmed bugs that need fixing

---

## 🧑‍💻 Coding Standards

### Shell Scripts (`config.sh`, `config.zsh`)

```bash
# ✅ DO: Use local variables
my_function() {
  local result="hello"
  echo "$result"
}

# ✅ DO: Check command availability before using
node_version() {
  command -v node >/dev/null 2>&1 || return
  echo "🟢 $(node -v)"
}

# ✅ DO: Double-quote variables
echo "$my_var"    # correct
echo $my_var      # wrong — may break on spaces

# ✅ DO: Use [[ ]] in bash/zsh
[[ -n "$var" ]]   # correct
[ -n "$var" ]     # outdated

# ❌ DON'T: Use set -e in config files (breaks interactive shell)
# ❌ DON'T: Use hardcoded paths like /home/user/...
# ❌ DON'T: Add slow commands (network calls, heavy parsing) in prompt
```

### Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Simple alias | 2–4 chars | `gs`, `nrd`, `brd` |
| Complex function | verb + noun | `parse_git_branch`, `get_duration` |
| Docker alias | `d` prefix | `dps`, `drm`, `dsh` |
| Internal helper | `_` prefix | `_ui_patch_tsconfig` |

### Web Files (`web/`)

- Run Prettier before committing: `npx prettier --write web/`
- Use CSS custom properties — no hardcoded hex values
- Test responsiveness at 375px, 768px, and 1440px

---

## 📝 Commit Message Format

```
type(scope): short description (max 72 chars)

Optional longer body explaining WHY (not WHAT).
```

**Types:**

| Type | When to use |
|------|------------|
| `feat` | Adding a new feature |
| `fix` | Fixing a bug |
| `docs` | Documentation only |
| `style` | Formatting, whitespace |
| `refactor` | Code change with no feature/fix |
| `chore` | CI, tooling, build changes |

**Examples:**

```
feat(docker): add dwatch for live container filesystem monitoring
fix(prompt): handle missing sensors on alpine linux gracefully
docs(readme): add makecpp usage example to project init section
chore(ci): add shellcheck linting to PR workflow
```

---

## 🔃 Pull Request Process

1. **One PR per feature/fix** — keep changes focused
2. **Update documentation** — README.md if command is user-facing
3. **Test in Docker** — see [Testing Your Changes](#-testing-your-changes)
4. **Fill the PR template** — describe what and why
5. **Wait for review** — maintainer will respond within a few days

### PR Title Format

```
feat: add dwatch function for Docker container monitoring
fix: handle missing sensors command on Alpine Linux
docs: improve prompt customization section in README
```

---

## 🧪 Testing Your Changes

### Quick Local Test

```bash
# Source your modified config in current shell
source config.sh

# Test your new function/alias
my_new_function
```

### Full Clean Test (Recommended)

```bash
# Test installer from scratch in a fresh container
docker run --rm -it ubuntu:latest bash -c "
  apt update -qq && apt install -y curl &&
  bash <(curl -fsSL YOUR_GIST_URL)
"
```

### Idempotency Test

```bash
# Run installer twice — second run must exit cleanly
bash <(curl -fsSL ...) && bash <(curl -fsSL ...)
```

### Shellcheck

```bash
shellcheck -s bash config.sh
shellcheck -s bash install.sh
```

---

## ❓ Questions?

- Open a [GitHub Discussion](https://github.com/rihadjahanopu/fancybash/discussions)
- Or open an [Issue](https://github.com/rihadjahanopu/fancybash/issues)

---

<div align="center">

Made with ❤️ in Bangladesh · MIT License

</div>
