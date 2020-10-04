# windows-terminal-config
Useful stuff for Windows Terminal.

## Make it pretty, add fonts and auto complete

```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

Change `powershell` $PROFILE, by adding script below. When Powershell core is started this code will be applied.
From `powershell` run `notepad $PROFILE` and add the content below:
```
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox

for($i = 1; $i -le 5; $i++){
  $u =  "".PadLeft($i,"u")
  $unum =  "u$i"
  $d =  $u.Replace("u","../")
  Invoke-Expression "function $u { push-location $d }"
  Invoke-Expression "function $unum { push-location $d }"
}
```

Install the font CascadiaPL: https://github.com/microsoft/cascadia-code/releases

Save and restart Windows Terminal.

## Add Keyboard shortcuts, schemes and config sample
```json
// To view the default settings, hold "alt" while clicking on the "Settings" button.
// For documentation on these settings, see: https://aka.ms/terminal-documentation

{
  "$schema": "https://aka.ms/terminal-profiles-schema",

  "defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",

  "profiles": [
    {
      // Make changes here to the powershell.exe profile
      "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
      "name": "Windows PowerShell",
      "commandline": "powershell.exe",
      "hidden": true
    },
    {
      // Make changes here to the cmd.exe profile
      "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
      "name": "cmd",
      "commandline": "cmd.exe",
      "hidden": true
    },
    {
      "guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
      "hidden": false,
      "name": "PowerShell Core",
      "source": "Windows.Terminal.PowershellCore",
      "startingDirectory": "c:\\Users\\MJC-PC\\source\\repos",
      "fontFace": "Cascadia Code PL",
      "colorScheme": "Subliminal"
    },
    {
      "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
      "hidden": false,
      "name": "Azure Cloud Shell",
      "colorScheme": "Subliminal",
      "source": "Windows.Terminal.Azure"
    },
    {
        "guid": "{07b52e3e-de2c-5db4-bd2d-ba144ed6c273}",
        "hidden": false,
        "name": "Ubuntu-20.04",
        "source": "Windows.Terminal.Wsl"
    }
  ],

  // Add custom color schemes to this array
  "schemes": [
    {
      "name": "Ubuntu",
      "black": "#2e3436",
      "red": "#cc0000",
      "green": "#4e9a06",
      "yellow": "#c4a000",
      "blue": "#3465a4",
      "purple": "#75507b",
      "cyan": "#06989a",
      "white": "#d3d7cf",
      "brightBlack": "#555753",
      "brightRed": "#ef2929",
      "brightGreen": "#8ae234",
      "brightYellow": "#fce94f",
      "brightBlue": "#729fcf",
      "brightPurple": "#ad7fa8",
      "brightCyan": "#34e2e2",
      "brightWhite": "#eeeeec",
      "background": "#300a24",
      "foreground": "#eeeeec"
    },
    {
      "name": "Spacedust",
      "black": "#6e5346",
      "red": "#e35b00",
      "green": "#5cab96",
      "yellow": "#e3cd7b",
      "blue": "#0f548b",
      "purple": "#e35b00",
      "cyan": "#06afc7",
      "white": "#f0f1ce",
      "brightBlack": "#684c31",
      "brightRed": "#ff8a3a",
      "brightGreen": "#aecab8",
      "brightYellow": "#ffc878",
      "brightBlue": "#67a0ce",
      "brightPurple": "#ff8a3a",
      "brightCyan": "#83a7b4",
      "brightWhite": "#fefff1",
      "background": "#0a1e24",
      "foreground": "#ecf0c1"
    },
    {
      "name": "Subliminal",
      "black": "#7f7f7f",
      "red": "#e15a60",
      "green": "#a9cfa4",
      "yellow": "#ffe2a9",
      "blue": "#6699cc",
      "purple": "#f1a5ab",
      "cyan": "#5fb3b3",
      "white": "#d4d4d4",
      "brightBlack": "#7f7f7f",
      "brightRed": "#e15a60",
      "brightGreen": "#a9cfa4",
      "brightYellow": "#ffe2a9",
      "brightBlue": "#6699cc",
      "brightPurple": "#f1a5ab",
      "brightCyan": "#5fb3b3",
      "brightWhite": "#d4d4d4",
      "background": "#282c35",
      "foreground": "#d4d4d4"
    },

    {
      "name": "midnight-in-mojave",
      "black": "#1e1e1e",
      "red": "#ff453a",
      "green": "#32d74b",
      "yellow": "#ffd60a",
      "blue": "#0a84ff",
      "purple": "#bf5af2",
      "cyan": "#5ac8fa",
      "white": "#ffffff",
      "brightBlack": "#1e1e1e",
      "brightRed": "#ff453a",
      "brightGreen": "#32d74b",
      "brightYellow": "#ffd60a",
      "brightBlue": "#0a84ff",
      "brightPurple": "#bf5af2",
      "brightCyan": "#5ac8fa",
      "brightWhite": "#ffffff",
      "background": "#1e1e1e",
      "foreground": "#ffffff"
    },
    {
      "name": "TheHulk",
      "black": "#1b1d1e",
      "red": "#269d1b",
      "green": "#13ce30",
      "yellow": "#63e457",
      "blue": "#2525f5",
      "purple": "#641f74",
      "cyan": "#378ca9",
      "white": "#d9d8d1",
      "brightBlack": "#505354",
      "brightRed": "#8dff2a",
      "brightGreen": "#48ff77",
      "brightYellow": "#3afe16",
      "brightBlue": "#506b95",
      "brightPurple": "#72589d",
      "brightCyan": "#4085a6",
      "brightWhite": "#e5e6e1",
      "background": "#1b1d1e",
      "foreground": "#b5b5b5"
    }
  ],

  // Add any keybinding overrides to this array.
  // To unbind a default keybinding, set the command to "unbound"
  "keybindings": [
    {
      "keys": [ "ctrl+shift+d" ],
      "command": {
        "action": "splitPane",
        "split": "auto",
        "splitMode": "duplicate"
      }
    },
    {
      "command": "closeTab",
      "keys": [ "ctrl+w" ]
    },
    {
      "command": "newTab",
      "keys": [ "ctrl+t" ]
    },
    {
      "command": {
        "action": "splitPane",
        "split": "auto"
      },
      "keys": [ "ctrl+shift+s" ]
    },
    {
      "keys": [ "ctrl+shift+d" ],
      "command": {
        "action": "splitPane",
        "split": "auto",
        "splitMode": "duplicate"
      }
    }
  ]
}

```