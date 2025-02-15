# Mac Dev Setup Guide


# General Setup

## Change keyboard shortcuts to my liking

> `Hyper = Ctrl + Opt + CMD + Shift`

- Desktop & Dock -> Shortcuts
  - Set Mission Control to use `Ctrl + Up` and bind it to `Mouse Button 4` (back button)
  - Set Application Window to use `Ctrl + Down` and bind it to `Mouse Button 5` (forward button)
  - Set ShowDesktop to use `Hyper + Down`
- Siri
  - Set Siri to use `Hyper + Space`
- Keyboard
  - Keyboard: Set pressing `Fn/Globe` key twice to start dictation
  - Shortcuts:
    - Mission Control:
      - Set Show Notification Centre to use `Hyper + Right`
      - Set Do Not Disturb On/Off to use `Hyper + Up`
    - Input Sources: Set `Ctrl + Space` to switch input source
    - Spotlight: Disable Spotlight shortcut (Cmd + Space) as we will use it for Raycast / Alfred

## Show hidden files

> `defaults write com.apple.finder AppleShowAllFiles YES`

Then relaunch Finder app (hold OPTION key while right click finder icon in the task bar, then choose relaunch)

## Adjust menu bar icon spacing to fit more icons

The Macbook camera notch is very annoying, you can only use about 40% of screen width for you menu bar icons (the icons will never go pass the camera notch). We can adjust below settings to use a more compact spacing for menu icons to fit more icons

> defaults -currentHost write -globalDomain NSStatusItemSpacing -int 5
> 
> defaults -currentHost write -globalDomain NSStatusItemSelectionPadding -int 6

To revert, use `delete` instead of `write`. To check use `read` instead of `write`. A compact setting is likely to be 6 and 5, and a "normal" setting is like to be 12 and 8.

You also need to restart MacOS for this to take effect.


# Install Software

## Install XCode

Install XCode tool (it is required by Homebrew)
> `xcode-select --install`
A download UI dialog will open fater executing that command. Confirm and start the download.

## Install Homebew

Install Homebrew:
> `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Follow the instructions after installation to add Homebrew to your PATH variable. For example, run these 2 commands after installation:
> `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/tomysaman/.zprofile`
> 
> `eval "$(/opt/homebrew/bin/brew shellenv)"`

Verify Homebrew installation by:
> `brew doctor`

## Install Apps with Homebrew
> `brew install --cask <appName>`

Use [this page](https://formulae.brew.sh/) to check the formula name and the command to run installation

Install these:
- Web browsers:
  - Chrome
  - Firefox
  - Edge
- Communication:
  - Slack
  - Zoom
  - Microsoft Team
  - Discord
- Cloud storage:
  - Dropbox
  - Google Drive (this should also install Google Office apps)
- Music:
  - Spotify 
- Graphic design and photos:
  - qView (photo viewer)
  - ImageOptim (image optimisation tool)
  - GIMP
- Video playback and conversion:
  - VLC
  - Handbrake (converting various video formats)
- Web & text editors:
  - VS Code
  - BBEdit
- Database clients:
  - DBeaver (MSSQL client)
  - Sequel Ace (MySQL client)
- Dev tools #1:
  - Sourcetree
  - GitHub Desktop
  - Docker or OrbStack
  - Postman
  - Postman Agent (helper tool for Postman, such as capturing login session via browser so you can test API as you're already logged in)
  - Firezilla (it is not in Homebrew registry due to ppl saying it has malware in it and MacOS blocks it, but it does seems being working ok for the latest version now)
- Dev tools #2:
  - iTerm2
  - Termius
  - Amazon Q for Command Line (previously known as Fig - a great terminal tool that provides handy functions such as auto-complete)
  - DevToys (a app provides many handy tools and functions for developers)
  - Keystore Explorer (for managing Java keystore)
- Remote desktop and VPN:
  - MS Remote Desktop
  - [Deskflow](https://github.com/deskflow/deskflow)
- Utilities
  - Malwarebytes or AVG AntiVirus
  - Raycast (Alfred alternative)
  - TheUnarchiver
  - Deluge
    - Import IP bloack list using this URL: https://github.com/Naunter/BT_BlockLists/raw/master/bt_blocklists.gz
  - AppCleaner (uninstaller)
  - [MediaInfo](https://github.com/sbarex/MediaInfo)
  - Mounty (free ntfs drive write tool - but currently not working with Ventura)
  - paragon-ntfs (paid ntfs drive write tool, works on the latest Mac hardware & software)
    - After brew install, use Finder to open /opt/homebrew/Caskroom/paragon-ntfs/xx/FSInstaller.app to finish the installation
    - Follow the prompt to change the Mac's system protection settings
      - Settings -> Privacy & Security -> click on Enable System Extensions button -> click Shut Down
      - Mac will shutdown, then turn it back on while holding the Power button to start in the recovery mode
      - Select Options -> your username -> type password to login
      - Launch the Startup Security Utility from the Utilities menu bar
      - Select Limited protection option, and tick the checkbox to enable user managed kernel extensions
      - Restart again
    - Follow the prompt to enable its system extension
      - Go to Settings -> Privacy & Security -> the "Enable System Extensions" button will now become "Allow" for the Paragon NTFS app
      - Click allow button and restart Mac again
    - Follow the prompt to give the app full disk access
      - Go to Settings -> Privacy & Security -> Full Disk Access -> toggle it ON for "com.paragon-software"
    - Go to Settings -> General -> Login Items -> Set the below items to be allowed in the background
      - kextload
      - NTFS for Mac.app
      - Paragon NTFS for Mac
    - Hit the "retry" button at the end of the guided setup, the app should start again and will prompt you for activation
      - Sign in with janicehuangau@yahoo.com.au / 0A..m0
      - If the license already been applied on another machine, login into Paragon website and revoke the product license so it can use again
- Apps 1
  - Stats (system info in menu bar)
  - Rectangle (windows management)
  - Mos (great mouse helper tool)
  - Monitor Control
  - Karabiner-Elements (keyboard keys mapping tool) (follow my github repo to import and use my setup)
- Apps 2
  - SuperDuper (folder sync & drive backup tool)
  - AltTab
  - Kap (screen recording tool)
  - Shottr (better screenshot tool)
  - Netspot (wifi analyser)
- Apps 3
  - HiddenBar
  - xBar
  - Itsycal (quick calendar on menu bar)
  - FlyCut (clipboard tool)
  - Captin (caps lock indicator)
- Apps 4
  - Numi (smart calculator)
  - Kap (screen recording)
  - TRex (OCR tool)
  - Youtube to MP3 (MediaHuam youtube-to-mp3)
  - FreeRuler
- Games
  - Steam
  - Epic Games Launcher
  - OpenEmu

## Install apps with MacPorts

Download & install [MacPorts](https://www.macports.org/install.php)
- Note that we would need to reinstall/upgrade MacPorts every times there is a major MacOS upgrade
- Update MacPorts `sudo port -v selfupdate`
- Install app via MacPorts `sudo port install [app]`

Install these:
- Putty

## Install software from Mac App Store

- Communication:
  - Line
    - or use the web version (much limited functionality and is only available as a [Chrome extension](https://chromewebstore.google.com/detail/line/ophjlpahpchlmihnnnihgmmeilfjmjjc?hl=en))
- Music:
  - MyTuner Radio (listen to live radio worldwide)
    - or use [Radio Garden](https://radio.garden/listen/smooth-fm-95-3/wq6970BS)
- Apps (group 2):
  - Dropover (file/image/text holder for various quick tasks)
  - Later (save your current session such as opened apps and windows, and easily restore them later when you need to)
- Apps (group 3):
  - Amphetamine (makes monitor screen & mac machine always on)
    - or install `caffeine` using homebrew
  - Hand Mirror (quickly show your camera view)
    - or you can just use `raycast`'s `open camera` command

## Install other software

These apps are not in Homebrew nor in Mac App Store, download them from their websites and install

- Communication:
  - Google Chat (open and login into Google Chat website, then click the "Install" icon in the URL bar)
- Remote desktop & VPN:
  - Chrome Remote Desktop
- Google Office
- Hardware device apps:
  - Streamdeck
  - Logitech G Hub (for my G303/G305 mouse)
  - Logitech Option (for my MX Master 2S mouse)
  - Other hardware software...
- Java 8
  - (version 1.8, download from java.com)
- For MacPorts, install:
  - [XQuartz](https://www.xquartz.org/)

## Install terminal commands with Homebrew

Use Homebrew to install these commands:
> `brew install <command>`

Install these:
- eza (`ls` alternative)
  - Note: see the alias section further down, after setting up custom alias you can use eza as below:
  - `l` or `ls` to list files
  - `l --tree` to list files in tree structure
- tldr (simplified `man` page)
  - `tldr <command>` to list a few of examples on how to use that command
- mcfly (a better command history search tool)
  - Add `eval "$(mcfly init zsh)"` to `~/.zshrc` to complete the setup after installing mcfly
  - Use `ctrl + r` to activate
- fd (`find` alternative, search filename using regexp)
  - `fd <search term in regexp>` to find files/directories with name matching the regexp
- fzf (a fuzzy filtering tool that take input and do filtering)
  - `fd | fzf` (or just `fzf`) to filter & search files (i.e. fzf takes the output of fd as input and lets you perform searching and filtering to see result on the fly)
  - `ps aux | fzf` to filter & search processes
- ripgrep (`grep` alternative, search file content using regexp)
  - `rg <search term in regexp>` to find files with content matching the regexp
  - use `-i` switch to not be case-sensitive search
- autojump (smart directory navigation)
  - See the message after brew install to add the required command into `~/.zshrc` to finish the setup
  - `j <directoryName>` to jump to that directory without the need to type out its path
- httpie (`curl` alternative)
  - [docs](https://httpie.io/docs/cli/examples)
  - `https [method] [address] param1=value1 param2=value2...` - where params are either URL var or FORM var
  - `http` to do the same thing but using http instead of https
- wget (download file from the web)
  - `wget <URL>`
- bat (better version of `cat` with syntax highlighting)
  - `bat <file>` to show the file's content
- gdu (see disk & directory space usage info, similar to `ncdu`)
  - `gdu-go` to activate
  - Use `left`/`right` to navigate between child and parent, use `d` key to delete item
- icdiff (diff tool)
  - `icdiff <file1> <file2>` to compare the two files
- lnav (log file viewer) 
  - [docs](https://docs.lnav.org/en/latest/hotkeys.html)
  - `lnav <file>` or `lnav <directory>` to activate
  - Useful hotkeys
    - For most of the hotkeys, use it with `shift` to do the opposite (e.g. key `1` will go down for 10 mins but `shift + 1` will go up for 10 mins)
    - `Left`/`Right` to show & hide sections
    - `PgUp`/`PgDn` & `Home`/`End` to navigate through log content
    - `ctrl + w` to toggle word-wrap
    - `p` to show line parsing result (change the line into parsed items instead of a single full line)
    - `shift` + `p` to format the log content for printing (for example if you have json or xml in log, it will automatically indent the content)
    - Navigate base on time period: `1`=10mins, `2`-20mins, .., `6`=60mins, `d`=24hrs
    - `i` to show histogram (how many lines occur per a period of time frame)
    - `m` to bookmark the line, and then use `u` to go through bookmarks
    - `/` to start searching using regexp, then use `n` to go through search results
    - `:` to trigger command mode, then:
      - Use `:filter-in <searchTerm>` and `:filter-out <searchTerm>` to filter the log content
      - Use `:comment <comment>` to comment on a line, use `:clear-comment` to remove it
      - Use `:tag <tag>` to tag a line, use `:un-tag` to remove it, and use `:delete-tags <tag1 tag2 ...>` to remove multiple tags
      - Use `:save-session <name>` to save the current stage/config to a named session, and use `:load-session  <name>` to load it
    - lnav will remember your commands such filter-in/filter-out and markers, even after you exit it. Use `ctrl + r` to reset the session if you need to
    - `;` to run SQL query against the log data
      - Do a `select * from <fileFormat>` to see what column names we can use for query, some of them are:
        - `log_time`, `log_level`, `log_mark`, `log_comment`, `log_tag`
        - Note that the table name "fileFormat" is the format of the log file, for example use `cflog` if the log file is a CF log
    - Use `tab` to go into filter panel (use `q` to exist)
      - Use `i` to add a filter-in, use `o` to add a filter-out, use `t` to flip your filter (filter in <-> tiler out), and use `spacebar` to enable/disable the filter
    - If the views contains multiple files, use `f` to go to next file
    - Use `:config /ui/theme/ <theme_name>` to change theme
      - default themes are: default, eldar, grayscale, monocai, night-owl, solarized-dark, and solarized-light
  - follow my [github repo](https://github.com/tomysaman/cf-lnav-cfml-logger-format) to import the cflog file rule and also to see how to create your own rule

- `jq` (json parser)
  - [docs](https://jqplay.org/)
  - `jq '[filter]' [json_file]` or `echo [json_content_text] | jq '[filter]'` or `curl [rest_api_endpoint] | jq '[filter]'`
- `btop` (system monitoring)
- `storm` (ssh manager)
  - `storm add`, `storm list`, `storm delete`, `storm web` (fire up a web server with UI for you to use storm)
- `eva` (calculator)
  - [docs](https://github.com/NerdyPepper/eva/)
- `pandoc` (document file converter)
  - [docs](https://pandoc.org/demos.html)
  - also install the pdf engine `basictex` in order to convert to pdf
  - `pandoc [source.md] -o [output.pdf]`
- `pass` (password manager)
  - `pass` to list all pw names
  - `pass <path>/<to>/<name>` to reveal the pw (but don't do this as the pw will be printed in terminal, do `-c` instead)
  - `pass -c <name>` to copy the pw into clipboard
  - `pass insert <name>` to create a pw or `pass generate <name>` to create a pw with a randomly generated password
  - `pass edit <name>` to change a pw, `pass rm <name>` to delete a pw
- `gnupg` (for encryption/decryption)
- `pinentry-mac` (gpg utility used by some of the apps in this list)
- `mailsy` (create temporary email address for you to use)
  - `mailsy g` to create a new email account
  - `mailsy m` to fetch the emails
  - `mailsy me` to show the account details
  - `mailsy d` to delete account
- `nmap` (port scanning utility)
- `task` (TaskWarrior for task management)
  - [docs](https://taskwarrior.org/docs/)
  - `task add <name>`, `task delete <name>`, `task done <number>`, `task next`
- `timewarrior` (time tracking)
  - [docs](https://timewarrior.net/docs/)
  - `timew start <task>`, `timew stop`, `timew continue`, `timew summary`
- speedtest-cli (run speed test in your terminal)
  - `speedtest-cli` to start the test
- youtube-dl (download Youtube video as video or music file)
  - `youtube-dl -x --audio-format mp3 <url>` to download the video as a mp3 file
- fanyi (Chinese translation tool)
  - `fanyi <word>` to translate it between English & Chinese and also pronounce it
- cowsay (output ascii art of a cow saying a sentence)
  - `cowsay -f [art] [text to say]` (or use `cowthink` instead of cowsay)
  - `cowsay -l` to see what arts can be used
- For Git:
  - `git-extras` (provide extra Git commands and aliases)
    - [docs](https://github.com/tj/git-extras/blob/master/Commands.md)
- For Docker:
  - `ctop` (docker system monitoring)
  - `lazydocker` (manage docker containers)
- For Node.js:
  - `node`
- For Python:
  - `python`
- Others:
  - `chroma` (utility used by some of the apps in this list)


# Install Zsh & Oh My Zsh

Install Zsh
> `brew install zsh`

Install Oh My Zsh
> `sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

## Update the Zsh configuration file

The file can be found at: 
`~/.zshrc`

### Plugins

Update `~/.zshrc` file and set the plugins, separate them each by space. For example:

> `plugins=(aliases aws bbedit colored-man-pages colorize copyfile git isodate macos nmap rsync systemadmin sudo themes transfer zsh-navigation-tools)`

See [this page](https://github.com/unixorn/awesome-zsh-plugins) for the full list of plugins. Below is the plugins I install:

- aliases: to list all zsh aliases you currently have
  - `alias`
- aws: for AWS CLI
  - see [plugin page](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/aws)
- bbedit: for BBEdit editor
  - `bb` to start BBEdit
  - `bbpb` to create a new doc in BBEdit and paste the clipboard content
- colorize: give color highlighting capability to cat and less commands 
  - `ccat` (colorized cat)
  - `cless` (colorized less)
- copyfile: `copyfile` (alias to `clipfile`) that copy a file's content into clipboard
- git: see [plugin page](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)
- isodate: `isodate`, `isodate_utc`, `unixstamp` to display current time in various formats
- macos: see [plugin page](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/macos)
  - `cdf` - cd to current Finder directory
  - `ofd` - open current working directory in Finder
  - `pfd` - print current Finder directory
  - `pfs` - print current Finder selection
  - `quick-look` - quick look a file
  - `man-preview` - open a man page in Preview app
  - `flushdns` - flush local dns records
  - `showfiles` / `hidefiles` - show/hide hidden files
  - `spotify` - control spotify (play \[query\], next, prev, pause, pos \[time\], quit)
  - `music` - control itune / apple music (play, next, previous, pause, status, playlist \[title\], quit)
- nmap: `nmap_open_ports`, `nmap_check_for_vulns` to scan ports
- rsync: `rsync-copy`, `rsync-move`, `rsync-update`, `rsync-synchronize`
- systemadmin: see [plugin page](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/systemadmin)
  - `path` - same as `print -l $path` which show your $path environment value
  - `pscpu10` - see top 10 most cpu usage processes
  - `psmem10` - see top 10 most memory usage processes
  - `mkdir` - same as `mkdir -pv` which will create all parent directories if they do not exist
  - `psgrep` - find a process using regexp
- sudo: press `Esc` twice to prefix your command with `sudo`
- themes: change zsh theme - `theme <theme>`, `lstheme` to view install themes, `theme` to change to a random theme
- transfer: using transfer.sh website to share files
  - `transfer <file_or_dir> -ca` to upload
    - it will automatically compress and archive the folder
    - if you don't need encryption, remove the -ca args
  - `curl <fileURL> -o ./<filename>` to download
  - `gpg --decrypt <file_downloaded> > <save_to_file>` to decrypt downloaded file
- zsh-navigation-tools: see [plugin page](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zsh-navigation-tools)
  - `n-kill` - browse process and select to kill
  - `n-env` - browse environment and edit them
  - `n-options` - browse options and toggle them
  - `n-aliases` - browse aliases and edit them
  - `n-functions` - browse functions and edit them

### Alias

Zsh/Oh-my-zsh and their plugins comes with many alias, some useful are:

- `_` = `sudo`
- `cd ...` = `cd ../..`, `cd ....` = `cd ../../..`, ..., `cd ......` = `cd ../../../../..`
- `-` = `cd -` (go to previous working directory)
- `1` = `cd -1`, `2` = `cd -2`, ..., `9` = `cd -9` (go to the nth previous working directory)
- `g` = `git`

### Themes

Update `~/.zshrc` file and set the theme:

> `ZSH_THEME="powerlevel10k/powerlevel10k"`

Availabe themes are
- [Builtin themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) - to use them simply set it in the ~/.zshrc file
  - jonathan
  - obraun
  - rkj-repos
- [External themes](https://github.com/ohmyzsh/ohmyzsh/wiki/External-themes) - download and install manually
  - [Powerlevel10k](https://github.com/romkatv/powerlevel10k) - I like this one the best
    - To install
      - > `git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`
      - Restart zsh with `exec zsh` and follow the installation prompt
    - To customise, edit `~/.p10k.zsh`
    - To find out the colors to use, run below to show the color number codes
       - > `for i in {0..255}; do print -Pn "%K{$i}  %k%F{$i}${(l:3::0:)i}%f " ${${(M)$((i%6)):#3}:+$'\n'}; done`


### Create a GPG key

GPG key is required for the `pass` command to encrypt & decrypt passwords. Follow these to create one:
- `gpg --full-generate-key`
  - Pick RSA -> 3072 -> Does not expire -> Type name & email
  - Type in the password to use with this key
- `gpg --list-keys` to view the generated keys
- `gpg --delete-secret-key <keyUUID>` then `gpg --delete-keys <keyUUID>` to delete a key

### Setup pass password store

The `pass` command need to be initialised using a key we created above. Follow these steps to do so:
- `pass init <keyUUID>`
  - note that you can create a new key with different password and run the above command to replace your key & password combination used to access your pws

### Create alias for commands

Create a oh-my-zsh custom file (can be any name, such as "aliases.zsh" at the following folder:
> `~/.oh-my-zsh/custom/`

- Create `l` and overwrite 'ls' to use **eza** as:
  - > `alias l='eza --all --grid --icons'`
  - > `alias ls='eza --header --long --all --classify --time-style=long-iso --icons'`
  - A helpful switch is `--tree` which lists the content of children dirs, and you use it with the alias likes `l --tree`
- Create `fd` to use **fd** and don't take .gitignore file into consideration:
  - > `alias fd='fd --no-ignore'`
- Overwrite `find` to use **fd** and don't take .gitignore file into consideration, then pipe it to fzf:
  - > `alias find='fd --no-ignore | fzf'`
- Create `rg` to use **rg** and don't take .gitignore file into consideration:
  - > `alias rg='rg --no-ignore'`



# iTerm2

- Setting changes
  - Preferences -> Profiles -> Text
    - Use "Underline" as cursor, and tick "Blinking cursor"
    - Tick "Use built-in Powerline glyphs
    - Pick a better font, such as "JetBrains Mono". See the **Fonts** section below on downloading and installing it
  - Preferences -> Profiles -> Window
    - Use 10% transparency
    - Enable "Blur" at 10%
  - Preferences -> Profiles -> Keys
    - Set Left Option key as Esc+ (so you can do Opt+F & Opt+B instead of Esc+F & Esc+B)

- Useful cursor movement shortcuts
  - `Ctrl + A` = move to the beginning
  - `Ctrl + E` = move to the end
  - `Opt + F` = move forward a word
  - `Opt + B` = move backward a word
  - `Ctrl + K` = delete the rest of the string after cursor position

- Download and install themes
  - Preferences -> Profiles -> Colors
  - "Color Presets" dropdown -> Visit online gallery
  - Download the ZIP file from the page, unzip it
  - "Color Presets" dropdown -> Import
    - Import those *.itermcolors files in the "schemes" folder
  - Pick the Dracula+ theme

- There are some useful optional tools and settings
	- Toolbelt -> Command History | Recent Directories | Paste History | Jobs
    	- For this to work, the Shell Integration need to be installed
    	- Click menu item: iTerm2 -> Install Shell Integration
  	- [The iTerm2 utilities](https://iterm2.com/documentation-utilities.html)

# Fonts

Install fonts into MacOS by:
- Download fonts as TTF format
- Open the "Font Book" app
- Drag the TTF files into Font Book app

Install these fonts and use one of them for VSCode & iTerm2:
- JetBrains Mono

Set JetBrains Mono as the font in:
- iTerm
- VS Code

# SSH key

Check `~/.ssh/`, if there is no .ssh folder or it is empty, generate a SSH key by following [this page](https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/)

My passphrase is usually: t.1..16

1. Generate SSH key files:
  > `sshkeygen`
  - Hit enter to accept default file names. Enter your choosen passphrase when prompted.
2. Add key to SSH agent:
  > `eval 'ssh-agent'`  

  > `ssh-add ~/.ssh/id_rsa`
3. Add a config file in your .ssh folder to let MacOS remember your passphrase so you don't need to type it every times
  > `cd ~/.ssh`

  > `touch config`
4. Add the following to the config file
  > `Host *`

  > `UseKeychain yes`

# Karabiner

- Load my custom rules
  - Get it from [here](https://github.com/tomysaman/karabiner_complex_modifications)
  - Complex modifications rules json files are loaded from `~/.config/karabiner/assets/complex_modifications`
- My json file contains rule that swap CMD and OPTION key
  - If this rule is enabled, ensure there is no custom mapping in the MacOS keyboard setting (Karabiner keyboard name is "Karabiner DriveKit VirtualHIDKeyboard")

# Git

### Git

TBC

### Bitbucket

If you use Bitbucket, consider using SSH over HTTPS when communicate with BitBucket Git. Follow below to setup SSH authentication ([reference](https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/)).

1. Copy the public key content
  > `pbcopy < ~/.ssh/id_rsa.pub`
2. Go to Bitbucket -> Your account -> Personal Settings -> SSH
3. Add a key, and paste your public key content
4. Verify you can communicate with bitbucket Git with ssh by:
  > `ssh -T git@bitbucket.org`

### SourceTree

- Add an user account and authenticate it via Bitbucket.
- Go to Preferences -> Account, edit your account
  - Set auth type = OAuth, protocal = SSH
  - Ensure your username and SSH key values are present
  - Check out repo using SSH style, such as: git@bitbucket.org:your_org_name/your_repo_name.git
  - Note: if you want you can still check out Git with HTTPS style likes: https://your_username@bitbucket.org/your_org_name/your_repo_name.git

# Local Dev

### HOST file

HOST file is in /private/etc/hosts

# CFML Dev

At the time of writing Jan 2022, there is some incompatibility issue between Java/Lucee & Apple M1 chip. So manually install CommandBox and Java, see below:

### CommandBox

CommandBox on Homebrew is bundled with OpenJDK Java, which is not compatible with M1 chip. So download and install CommandBox manually from [CommandBox homepage]() (get the one with JRE). Extract the file and move the **box** binary to your `/usr/local/bin` folder so you can run it anywhere in terminal.

### Java

Download and install Sun/Oracle's [Java 8]() (version 1.8) and install it

### jenv

TBC

# Certificates

TBC

# Dev tools

### VSCode

Use settings sync (login with my GitHub account) to sync all my settings automatically

# OS updates

Sometimes MacOS updates can break things, especially when upgrading to a new major version.

## Xcode command line tools

If you see oh my zsh error message when open up iTerm:  `[oh-my-zsh] Can't update: not a git repository.`; Or you see VSCode says Git cannot be found, that's because Xcode command line tools is not included in the new major version upgrade of MacOS. You will need to re-install it again by running:
> `xcode-select --install"`
