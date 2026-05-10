# dotfiles

Personal dotfiles managed with [chezmoi](https://chezmoi.io).

> productivity setup for someone who spends 80% of time configuring it

## Before you begin

**Import your GPG key first.**

## Quick start

```sh
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply kathlind
```

During initialization chezmoi will prompt for three values that are stored locally and never committed:

- `git name` — your display name for git commits
- `git email` — personal email
- `school email` — email used inside `~/school/`

## What's inside

### Package installation

`.chezmoiscripts/run_onchange_darwin-install-packages.sh.tmpl` installs Homebrew if missing, then runs `brew bundle` with the package list from `Brewfile`.

The script only runs on macOS and re-runs automatically when the package list changes.

### External repos

`.chezmoiexternal.toml` pulls in two separate configs as git repos (refreshed every 7 days):

| Path             | Repo                                                            |
| ---------------- | --------------------------------------------------------------- |
| `~/.config/nvim` | [kathlind/nvim-config](https://github.com/kathlind/nvim-config) |
| `~/.config/zsh`  | [kathlind/zsh-config](https://github.com/kathlind/zsh-config)   |

### Git config

`dot_config/git/config.tmpl` sets up name, email, nvim as editor, delta for diffs, and auto-includes `school` identity for any repo under `~/school/`.

### Ghostty

`dot_config/ghostty/config` — JetBrainsMono Nerd Font 14pt, Catppuccin Macchiato theme, 90% opacity with blur.

### Zsh

`dot_zshenv` sets `ZDOTDIR` to `~/.config/zsh`, delegating the rest to the external zsh-config repo.

## Requirements

- macOS (the install script is Darwin-only)
- GPG key imported (see [Before you begin](#before-you-begin))
- SSH key added to GitHub (external repos are cloned over SSH)

---

## License

WTFPL — do whatever you want with it.
