# Resell-Bot
## Read the setup section carefully to prevent unwanted stuff from happening ❗
## Setup
```json
{
    "Cookie": "", Your roblox account cookie that will sell the ugcs (MUST HAVE PREMIUM)

    "Under_Cut": {
        "type": "percent", Undercut methode, "percent" will undercut by percentage, "robux" will undercut by robux
        "value": 10 Percent = will undercut the price by 10%. Robux = will undercut the price by 10 R$
    },

    "Auto_Sell": {
        "Ask_Before_Sell": true, If true the bot will ask before selling a limited, if false it will mass sell
        "Hide_OnSale": false, Set it to true to not sell limiteds that are already on sale
        "Keep_Serials": 0, If you keep it at 0 it will ask/sell all your limiteds, if you put it to 10 or any number other number then 0 it will keep all the serials under that number
        "Keep_Copy": 0, If you set this to 0 it will sell all your ugc limiteds (if you have Ask_Before_Sell to true if it will ask before), if you put it to 1 or higher it will keep 1 (or X) copy of each limited you own
        "Blacklist": [] Limited ids that you dont want to sell
    }
}
```
### Features:
- [x] - **Gather all the limiteds that can be resold**
- [x] - **Pretty customizable**
- [x] - **Undercut by robux and %**
- [x] - **Fast**
- [x] - **Checks all the Head, Face, Neck, Shoulder, Front, Back, Waist, Gear, Pants, Shorts, Skirts, T-shirts, Shirts, Sweaters, Jackets accessories**

## IMPORTANT!
- If you don't trust it don't use it.
- If main.py crashs when you run it, uninstall the current python version you have installed and install python version 3.11.x
## Help
If you need help setting up the bot join the [Discord](https://discord.gg/deathsniper)
