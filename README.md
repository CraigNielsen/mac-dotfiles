# Dotfiles

Craig's macOS configuration for skhd, yabai, Vim and Prezto/Zsh.

| Repository file | Active location |
| --- | --- |
| `skhd/skhdrc` | `~/.config/skhd/skhdrc` |
| `yabai/yabairc` | `~/.config/yabai/yabairc` |
| `vim/vimrc` | `~/.vimrc` |

These are snapshots of the existing configuration. Creating this repository
has not replaced active files or restarted services. The Vim file is the Mac
Vim configuration, not the separate remote Neovim configuration.

## Use on a machine

Install skhd, yabai and Vim separately. Review the files, back up existing
configuration, then copy the corresponding files to the locations above.
Alternatively, after moving existing files aside, symlink them from this repo:

```sh
DOTFILES="$HOME/git_repos/dotfiles"
mkdir -p "$HOME/.config/skhd" "$HOME/.config/yabai"
ln -s "$DOTFILES/skhd/skhdrc" "$HOME/.config/skhd/skhdrc"
ln -s "$DOTFILES/yabai/yabairc" "$HOME/.config/yabai/yabairc"
ln -s "$DOTFILES/vim/vimrc" "$HOME/.vimrc"
```

The link commands intentionally do not overwrite existing files. With links,
configuration changes also appear as changes in this repository.

Vim uses vim-plug and a comma leader. Install vim-plug separately, then run
`:PlugInstall`. Some plugins need additional dependencies or compilation.
The inherited F6 mapping references `~/.config/nvim/init.vim`, which is not
included here. Some inherited mappings depend on plugins not declared in vimrc.

Yabai's configuration uses `sudo yabai --load-sa`; the scripting addition and
permissions must already be configured appropriately on the target machine.
The repository does not perform that setup. skhd includes a shortcut that
terminates iTerm2 (`alt + shift + return`), and assumes a multi-display setup.

## Publishing changes

Only reviewed files are allowed by .gitignore. Keep local secrets, caches,
plugin installations and editor state outside this repository. Inspect
`git diff` and `git diff --cached` before committing or pushing.

## Prezto and Zsh

`prezto/` contains the live Mac startup configuration captured on 2026-10-13:
`.zpreztorc`, `.zshrc`, `.zshenv`, `.zprofile`, `.zlogin`, and `.zlogout`.
These files map to the same names in your home directory (or your configured
ZDOTDIR). Install Prezto separately in `~/.zprezto` before using them.
Back up existing files before copying or linking each of these six files.
No changes were made to the original live configuration.

The public snapshot omits SSH endpoints, deployment aliases and a cloud project
ID. Absolute user-home paths have been replaced with `$HOME`. Put personal
connection/deployment aliases in `~/.zpreztorc.local`; the public `.zpreztorc`
sources it when present. Never add that local file to this repository.

The configuration uses the smiley prompt, syntax highlighting, history substring
search and custom aliases. It expects macOS/Homebrew, pyenv, kubectl and several
project-specific scripts to exist; review those dependencies on a new machine.
The Prezto framework itself, shell history and installed modules are not included.
