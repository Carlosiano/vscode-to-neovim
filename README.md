# VISUAL STUDIO CODE TO VIM/NEOVIM

## 1. Install Vscodium

Kita akan banyak mengubah `settings.json` dan `keybindings.json`.

Jadi untuk menjaga setingan normal dari vscode tetap ada, kita akan mengubah `settings.json` dan `keybindings.json` yang ada pada vscodium.

Sehingga kita punya konfigurasi normal vscode kita dan konfigurasi neovim pada vscodium kita

### [Official Website](https://vscodium.com/#install)

### Windows

#### [Windows Package Manager (WinGet)](https://github.com/microsoft/winget-cli)
```
winget install vscodium
```

#### [Chocolatey](https://chocolatey.org)
```
choco install vscodium
```

#### [Scoop](https://scoop.sh/)
```
scoop bucket add extras
scoop install vscodium
```

### MacOs

#### [Homebrew]()
```
brew install --cask vscodium
```

### Linux

#### Install mennggunakan [snapd](https://snapcraft.io/docs/installing-snapd)
```
snap install codium --classic
```

#### Parrot OS
```
sudo apt update && sudo apt install codium
```

#### Debian / Ubuntu

- Tambah GPG key dari repository vscodium
    ```
    wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg \
    | gpg --dearmor \
    | sudo dd of=/usr/share/keyrings/vscodium-archive-keyring.gpg
    ```

- Tambah repository dari vscodium
    ```
    echo 'deb [ signed-by=/usr/share/keyrings/vscodium-archive-keyring.gpg ] https://download.vscodium.com/debs vscodium main' \
    | sudo tee /etc/apt/sources.list.d/vscodium.list
    ```

- Update & Install vscodium
    ```
    sudo apt update && sudo apt install codium
    ```
    
#### Fedora / Centos / OpenSUSE

- Tambah GPG key dari repository vscodium
    ```
    sudo rpmkeys --import https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg
    ```
    
- Tambah repository dari vscodium
    - Fedora/RHEL
        ```
        printf "[gitlab.com_paulcarroty_vscodium_repo]\nname=download.vscodium.com\nbaseurl=https://download.vscodium.com/rpms/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg\nmetadata_expire=1h" | sudo tee -a /etc/yum.repos.d/vscodium.repo
        ```
    - openSUSE/SUSE
        ```
        printf "[gitlab.com_paulcarroty_vscodium_repo]\nname=gitlab.com_paulcarroty_vscodium_repo\nbaseurl=https://download.vscodium.com/rpms/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg\nmetadata_expire=1h" | sudo tee -a /etc/zypp/repos.d/vscodium.repo
        ```
- Install vscodium
    - Fedora/RHEL
        ```
        sudo dnf install codium
        ```
    - OpenSUSE/SUSE
        ```
        sudo zypper in codium
        ```

#### Nix(OS)
```
nix-env -iA nixpkgs.vscodium
```

#### Arch Linux
- Aura
    ```
    sudo aura -A vscodium-bin
    ```
- Yay
    ```
    yay -S vscodium-bin
    ```

#### Flatpak Option
```
flatpak install flathub com.vscodium.codium
```

 

## 2. Install Neovim

### Windows

Hanya suport Windows 8+ . Windows 7 dan versi dibawahnya tidak suported.

#### [Chocolatey](https://chocolatey.org)

- **Release (v0.5):** `choco install neovim` (gunakan -y untuk automatis skip dari pesan konfirmasi)
- **Development (pre-release):** `choco install neovim --pre`

#### [Scoop](https://scoop.sh/)

- **Release:** `scoop install neovim`
- **Development (pre-release):**
  ```
  scoop bucket add versions
  scoop install neovim-nightly
  ```
### Mac

#### [Homebrew](https://scoop.sh/)

- **Release:** `brew install neovim`

- **Development (pre-release):** `brew install --HEAD neovim # Latest`

### Ubuntu

- **Release:** `sudo apt install neovim`

- **Development (pre-release):** `NANTI DI ISI`

### Arch

- **Release:** `sudo pacman -S neovim`

- **Development (pre-release):** `yay -S neovim-git # Latest`


## 3. Install neovim plugin


PASTIKAN TIDAK ADA FOLDER `nvim` PADA `~/.config` DI LINUX/MAC ATAU PADA `~/AppData/Local` DI WINDOWS

- Linux/Mac

  ```
  git clone https://github.com/Carlosiano/vscode-to-neovim.git ~/.config/nvim
  ```

- Windows

  ```
  git clone https://github.com/Carlosiano/vscode-to-neovim.git ~/.AppData/Local/nvim
  ```
  

## 4. Install python & node support

```
pip install pynvim
```

```
npm i -g neovim
```

## Install clipboard support

- Di Mac pbcopy biasanya sudah ada

- Ubuntu

  ```
  sudo apt install xsel
  ```

- Arch

  ```
  sudo pacman -S xsel
  ```

## (Optional) Install python & node support menggunakan virtual environments

Pastikan untuk menambahkan path ini ke file init.vim kalian

```
let g:python3_host_prog = expand("<path / lokasi python3 terinstall>")

let g:node_host_prog = expand("<path / lokasi nodejs terinstall>")
```

contoh
```
let g:python3_host_prog = expand("~/.miniconda/envs/neovim/bin/python3.8")

let g:node_host_prog = expand("~/.nvm/versions/node/v12.16.1/bin/neovim-node-host")
```

## Daftar Program yang mungkin harus kamu

- ranger
- ueberzug
- ripgrep
- silver_searcher
- fd
- universal-ctags
- lazy git
- lazy docker

Explanations and installation instruction can be found on my blog

## Language Servers

Since CoC doesn't support all languages in there extensions
I recommend installing some language servers from scratch
and adding them to your `coc-settings.json` file

Example:

- bash

  `npm i -g bash-language-server`

  ```
  "languageserver": {
  "bash": {
    "command": "bash-language-server",
    "args": ["start"],
    "filetypes": ["sh"],
    "ignoredRootPaths": ["~"]
    }
  }
  ```

## For FAR to work

```
:UpdateRemotePlugins
```

## TabNine

To use TabNine enter the following in a buffer:

```
TabNine::config
```

**NOTE** This extension can take up a ton of memory

## Vim Gists

To use **vim-gists** you will need to configure the following:

```
git config --global github.user <username>
```

## VSCodium & Neo Vim Extension

[VSCodium](https://github.com/VSCodium/vscodium) contains build files to generate free release binaries of Microsoft's VS Code.

You can install it on multiple platforms:

- Mac

  ```
  brew cask install vscodium
  ```

- Arch

  ```
  yay -s vscodium-bin
  ```

- Snap

  ```
  snap install codium
  ```

[The Neo Vim Extension](https://github.com/asvetliakov/vscode-neovim) is available in the VSCode marketplace

I recommend using this alongside the VSCode `which-key` extension

Along with some of my config files you can find in `utils/vscode_config`

## TODO

- Better Documentation
- Improve VSCode which-key config

## CoC extensions to check out

- coc-fzf
- coc-stylelintplus
- coc-floaterm
- coc-actions
- coc-bookmark

## 0.5

- native lsp
- treesitter

## LOW PRIORITY TODO

If anyone reading this has any suggestions about implementing any of the following I will accept a PR, but these are not priority.

- ale
- multiple cursors
- markdown table
- spaceline (add colorscheme for mach2)
- tpope/vim-dadbod
- neovide
- People asked about vimwiki I kinda hate it but maybe I'll add it
- vimspector this is included but I don't plan on using it much
  - can be used with jdb, pdb, gdb, etc...
- later manually link pylance
- resize with arrows in addition to meta
- how to support meta key on for macOS?
