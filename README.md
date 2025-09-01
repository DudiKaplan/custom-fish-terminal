# Custom Fish Terminal for Mac

> This is a guide, how to configure a custom terminal using Fish and Starship
> In order to succeed in the guide, make sure that `brew` and `vsCode` and `iTerm2` are installed !

### Step 1 :

Install [fish](https://fishshell.com/), Run the following command
`brew install fish`
Install [starship](https://starship.rs/) , Run the following command

```
curl -sS https://starship.rs/install.sh | sh
```

open terminal and write fish and press enter . now write `fish_config` its will be open a new browser to set your favorite theme.

## Step 2 :

Open config.fish File with `code ~/.config/fish/config.fish` and change like this :

```
 if status is-interactive
     fish_add_path $HOME/.krew/bin
     starship init fish | source
 end

```

Open starship.toml File with `code ~/.config/starship.toml` and change like this (exmaple) :

```
[git_status]
ahead = "⇡${count}"
diverged = "⇕⇡${ahead_count}⇣${behind_count}"
behind = "⇣${count}"

[git_state]
format = '[\($state( $progress_current of $progress_total)\)]($style) '
cherry_pick = "[🍒 PICKING](bold red)"

[git_commit]
commit_hash_length = 4
tag_symbol = "🔖 "

[time]
disabled = false
style = "bold yellow"
format = 'b"h 🍺 [$time]($style)'
[line_break]
disabled = false

[nodejs]
format = "node [$symbol($version )]($style)"

[username]
style_user = "white bold underline"
style_root = "black bold"
format = "🧔 [$user]($style) "
disabled = false
show_always = true

[status]
style = "bg:blue"
symbol = "🔴 "
success_symbol = "🟢 SUCCESS"
format = '[\[$symbol$common_meaning$signal_name$maybe_int\]]($style) '
map_symbol = true
disabled = true

[[battery.display]]
threshold = 30
style = "red bold"

[[battery.display]]
threshold = 60
style = "yellow bold"

[[battery.display]]
threshold = 100
style = "green bold"


[kubernetes]
format = 'on [⛵ $context \($namespace\)](blue) '
disabled = true

[aws]
disabled = true
```

## Step 3 :

Change the default of the iTerm2 terminal to work with fish ,Run the following commands

Test fish install location 

`which fish`

```
echo /usr/local/bin/fish | sudo tee -a /etc/shells
chsh -s /usr/local/bin/fish
```

For mack M4  run
```
sudo sh -c 'echo /opt/homebrew/bin/fish >> /etc/shells'
chsh -s /opt/homebrew/bin/fish
```

Change the default of the vsCode terminal to work with fish ,Run the following commands

`> Terminal: Select Default Profile`
and pick the `fish`.

## Step 5 :

`brew install --cask font-hackgen-nerd`

> in vsCode settings.json change like this :

```
 {
   "editor.accessibilitySupport": "off",
   "window.zoomLevel": 2,
   "workbench.colorTheme": "Default Dark+",
   "terminal.integrated.env.osx": {
     "FIG_NEW_SESSION": "1"
   },
   "editor.fontFamily": "Fira Code",
   "editor.fontLigatures": true,
   "terminal.integrated.defaultProfile.osx": "fish",
   "terminal.integrated.fontFamily": "Hack Nerd Font"
 }
```

## for nice search table history

```
brew install fzf
curl -sL https://git.io/fisher | source
fisher install jorgebucaran/fisher
fisher install PatrickF1/fzf.fish
```

Good luck, Dudi Kaplan
