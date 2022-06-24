# ZSH Dev Toolkit

Languages: [🇪🇸] [Español](README.ES.md) - [🇺🇸] [English](README.md)

ZSH setup and productivity tools for development

## Repo

### 1. Clone

On `~` (home) path clone this repo

```bash
git init 
git remote add origin https://github.com/deinsoftware/zsh-dev-toolkit.git
git pull origin main
```

### 2. Setup

On `.zshrc` file add.

```bash
# Helpers
export WINHOME=$(wslpath "$(wslvar USERPROFILE)")
export OPEN="explorer.exe" #wsl2
export BROWSER="${OPEN}" #wsl2

export PATH="$HOME/.helpers/b64/:$PATH"
export PATH="$HOME/.helpers/git/:$PATH"
export PATH="$HOME/.helpers/md/:$PATH"
export PATH="$HOME/.helpers/open/:$PATH"
export PATH="$HOME/.helpers/search/:$PATH"
chmod +x ~/.helpers/**/*

# Custom
export GIT_USER_NAME="user" # private business/work user
export GIT_USER_EMAIL="user@mail.com" # private business/work e-mail
export GITHUB_USER_NAME="user" # public personal user
export GITHUB_USER_EMAIL="user@users.noreply.github.com" # public personal e-mail
[ -f ~/.aliases ] && . ~/.aliases
[ -f ~/.colors ] && . ~/.colors
[ -f ~/.hooks ] && . ~/.hooks
```

> `OPEN` and `BROWSE` constants need to be configured according yor OS. Windows (WSL2) and macOS use the same command to open the file explorer or the default web browser, on Ubuntu (Linux) need to be specified each one.

|SO|`OPEN`|`BROWSER`|
|---|---|---|
|Windows (WSL2)|`"explorer.exe"`|`"${OPEN}"`|
|macOS|`"open"`|`"${OPEN}"`|
|Ubuntu|`"xdg-open"`, `"gnome-open"`, `"nautilus"` ...|`"googlechrome"`, `"firefox"` ...|

> `PACKAGE` constant need to be configured according the package manager you use `"NPM"`, `"YARN"`, `"PNPM"`.

### 3. Permissions

Now add execution permission:

```bash
chmod +x ~/.helpers/**/*
```

### 4. Update

Once finish, save `.zshrc` file, close and reopen all terminals or update his source running `source ~/.zshrc` command.

That's all folks! It's ready to use.

### 5. Extra

Usefull alias to use on PowerShell side to deal with `WSL`.

```powershell
# Alias
function getAliases() {
    echo "(Get-Alias).DisplayName"
    (Get-Alias).DisplayName
}
Set-Alias a -value getAliases

# Profile
function checkIfProfileExist() {
    echo "Test-Path $profile"
    Test-Path $profile
}
Set-Alias pe -value checkIfProfileExist
function createProfile() {
    echo "New-Item -path $PROFILE -type file -force"
    New-Item -path $PROFILE -type file -force
}
Set-Alias pc -value createProfile
function editProfile() {
    echo "code $PROFILE"
    code $PROFILE
}
Set-Alias e -value editProfile
function reloadProfile() {
    echo ". $PROFILE"
    . $PROFILE
}
Set-Alias r -value reloadProfile

# WSL
function editWslConfig() {
    echo "code $HOME/.wslconfig"
    code $HOME/.wslconfig
}
Set-Alias wc -value editWslConfig
function wslShutdown() {
    echo "wsl --shutdown"
    wsl --shutdown
}
Set-Alias ws -value wslShutdown
function wslList() {
    echo "wsl -l -v"
    wsl -l -v
}
Set-Alias wl -value wslList
function wslRun() {
    echo "wsl"
    wsl
}
Set-Alias wr -value wslRun
function wslRunUbuntu() {
    echo "wsl --distribution Ubuntu"
    wsl --distribution Ubuntu
}
Set-Alias wru -value wslRunUbuntu
function wslStatus() {
    echo "wsl --status"
    wsl --status
}
Set-Alias wst -value wslStatus
```

## Folder Structure

```bash
~
├── .cheatsheet
│   └── git.md
│   └── open.md
├── .helpers
│   ├── b64
│   ├── git
│   ├── md
│   ├── open
│   └── search
├── .aliases
├── .colors
├── .hooks
└── .zshrc
```

|Name|Description|
|---|---|
|`.cheatsheet`| Folder with basic markdown file to see a cheatsheet with `helpers` and `alias` |
|`.helpers`| Folder with custom helper functions to use as terminal commands |
| ── `b64`| Helper commands for file conversions to/from base64 |
| ── `git`| Helper commands for git cloning with extra features (WIP) |
| ── `md`| Helper commands to see MarkDown files on terminal (WIP) |
| ── `open`| Helper commands to open file/folder on the File Explorer or open files/url on the Browser |
| ── `search`| Helper commands to search text inside files |
|`.aliases`| File for aliases definitions |
|`.colors`| File with terminal colors to use in other scripts |
|`.hooks`| ZSH hooks file with custom functions to run as validation before and after run commands |
|`.zshrc`| ZSH source file |

## ZSH plugins

There are a lot of [plugins for ZSH](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins), those are the most useful that I found.

### Official

* [git](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)
* [git-lfs](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git-lfs)
* [history-substring-search](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/history-substring-search)
* [node](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/node)
* [npm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/npm)
* [sudo](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sudo)
* [ubuntu](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ubuntu)
* [web-search](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/web-search)
* [z](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/z)

### Extras

* [zsh-nvm](https://github.com/lukechilds/zsh-nvm)
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
* [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

## Article Series

* [Useful Alias for ZSH](https://dev.to/equiman/useful-alias-for-zsh-1j8b)
* [Reveal the command behind an alias with ZSH](https://dev.to/equiman/reveal-the-command-behind-an-alias-with-zsh-4d96)
* [Command validations with ZSH](https://dev.to/equiman/command-validations-with-zsh-2boa)
* [Open File Explorer and Browser from ZSH](https://dev.to/equiman/open-file-explorer-and-browser-mbb)
* [Automatic change directory after git clone](https://dev.to/equiman/automatic-change-directory-after-git-clone-8ei)
* [ZSH cheatsheet for git plugin](https://dev.to/equiman/zsh-cheatsheet-for-git-plugin-1f6a)
* [Move WSL File System to another Drive](https://dev.to/equimancho/mover-el-sistema-de-archivos-de-wsl-a-otro-disco-3fbi)

---

## About

### Built With

* [VS Code](https://code.visualstudio.com/) - Code editing redefined.
* [Widows Terminal](https://github.com/Microsoft/Terminal/) - A modern terminal application for users of command-line tools and shells.

### Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [ZSH Dev Toolkit](https://github.com/deinsoftware/zsh-dev-toolkit/tags) on GitHub.

### Authors

- **Camilo Martinez** [[Equiman](http://github.com/equiman)]

See also the list of [contributors](https://github.com/deinsoftware/zsh-dev-toolkit/contributors) who participated in this project.

### Sponsors

If this project helps you, consider buying me a cup of coffee.

[![paypal](https://img.shields.io/badge/-PayPal-gray?style=flat&labelColor=00457C&logo=paypal&logoColor=white&link=https://paypal.me/equiman/3)](https://paypal.me/equiman/3)
[![ko-fi](https://img.shields.io/badge/-Ko–Fi-gray?style=flat&labelColor=fd444a&logo=ko-fi&logoColor=white&link=https://ko-fi.com/equiman)](https://ko-fi.com/equiman)

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details.
