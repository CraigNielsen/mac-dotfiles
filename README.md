# Dotfiles

Craig's macOS configuration for skhd, yabai and Vim.

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
