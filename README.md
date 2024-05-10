# autovenv

This script finds the closest Python 3 virtualenv and activates it.

If no venv is found in the current or directories up to $HOME, this script will create a venv for the current directory.

If it does find a venv in an ancestor directory but you want to force a new venv in the current directory, use the `force` option.

Rename the autovenv-created active venv with `./autovenv mv $new_name`.
Remove the autovenv-created active venv with `./autovenv rm`.

## Use with zsh

Add this to your ~/.zshrc, updating the path to this file:

```zsh
function autovenv_cd_hook() { eval $(PRINT_VARS=1 ~/path/to/autovenv); }
autoload -U add-zsh-hook
add-zsh-hook chpwd autovenv_cd_hook

plugins(... virtualenv)
ZSH_THEME="autovenv"
```

Show the virtualenv in your zsh prompt with oh-my-zsh! for example:

```zsh
# ~/.oh-my-zsh/custom/themes/autovenv.zsh-theme
PROMPT='$(virtualenv_prompt_info) '
PROMPT+="%(?:%{$fg_bold[green]%}%1{➜%} :%{$fg_bold[red]%}%1{➜%} ) %{$fg[cyan]%}%c%{$reset_color%}"
PROMPT+=' $(git_prompt_info)'
ZSH_THEME_VIRTUALENV_PREFIX="(🐍"
ZSH_THEME_VIRTUALENV_SUFFIX=")"
ZSH_THEME_GIT_PROMPT_PREFIX="%{$fg_bold[blue]%}git:(%{$fg[red]%}"
ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%} "
ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[blue]%}) %{$fg[yellow]%}%1{✗%}"
ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[blue]%})"
```
