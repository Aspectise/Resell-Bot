# Resell Bot

A fast and efficient Roblox UGC Limited reselling tool with automatic 2FA handling and price floor protection.

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL%203.0-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![GitHub](https://img.shields.io/badge/GitHub-Aspectise-black?logo=github)](https://github.com/Aspectise)
[![Open Source](https://img.shields.io/badge/Open%20Source-Contributions%20Welcome-green.svg)](#contributing)

> ⚠️ **Read the setup section carefully to prevent unwanted sales!**

## Features

- ✅ **2FA Support** - Automatic TOTP authentication handling
- ✅ **Price Floor Protection** - Prevents listing below Roblox's minimum price
- ✅ **Smart Caching** - Batches API requests for maximum efficiency
- ✅ **Concurrent Processing** - Configurable thread count
- ✅ **Undercut Options** - By percentage or fixed Robux amount
- ✅ **Serial Protection** - Keep your best serials
- ✅ **Copy Protection** - Keep X copies of each item
- ✅ **Blacklist Support** - Exclude specific items from selling
- ✅ **Minimum Profit Filter** - Only sell items above profit threshold
- ✅ **Rate Limit Handling** - Automatic retry with exponential backoff
- ✅ **Premium Check** - Validates account has Premium before selling

### Supported Asset Types

| Category | Types |
|----------|-------|
| Accessories | Hat, Hair, Face, Neck, Shoulder, Front, Back, Waist |
| Clothing | T-Shirts, Shirts, Pants, Jackets, Sweaters, Shorts, Dresses/Skirts |

## Requirements

```
pip install aiohttp rich
```

## Configuration

```json
{
    "Cookie": "",
    "TOTP_Secret": "",
    "Undercut": {
        "Type": "percent",
        "Value": 10
    },
    "Settings": {
        "Threads": 5,
        "Ask_Confirmation": true,
        "Hide_On_Sale": false,
        "Keep_Best_Serials": 0,
        "Keep_Copy": 0,
        "Min_Profit_Robux": 0
    },
    "Blacklist_AssetIDs": []
}
```

### Configuration Options

| Option | Type | Description |
|--------|------|-------------|
| `Cookie` | string | Your `.ROBLOSECURITY` cookie (account must have Premium) |
| `TOTP_Secret` | string | Your 2FA authenticator secret key (for automatic 2FA solving) |

#### Undercut Settings

| Option | Type | Description |
|--------|------|-------------|
| `Type` | string | `"percent"` or `"robux"` |
| `Value` | number | Amount to undercut (e.g., `10` = 10% or 10 R$) |

#### General Settings

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `Threads` | number | `5` | Number of concurrent requests |
| `Ask_Confirmation` | boolean | `true` | Prompt before listing items |
| `Hide_On_Sale` | boolean | `false` | Skip items already listed for sale |
| `Keep_Best_Serials` | number | `0` | Keep serials ≤ this number (0 = disabled) |
| `Keep_Copy` | number | `0` | Keep X copies of each item (0 = sell all) |
| `Min_Profit_Robux` | number | `0` | Minimum profit after 30% tax (0 = disabled) |
| `Blacklist_AssetIDs` | array | `[]` | Asset IDs to exclude from selling |

## Usage

```bash
python main.py
```

The bot will:
1. Authenticate and validate your account
2. Scan your inventory for resellable UGC limiteds
3. Check current market prices and price floors
4. Display items matching your criteria
5. Ask for confirmation (if enabled)
6. List items for sale

## Example Config

### Conservative (Safe)
```json
{
    "Cookie": "your_cookie_here",
    "TOTP_Secret": "your_2fa_secret",
    "Undercut": {
        "Type": "percent",
        "Value": 5
    },
    "Settings": {
        "Threads": 3,
        "Ask_Confirmation": true,
        "Hide_On_Sale": true,
        "Keep_Best_Serials": 100,
        "Keep_Copy": 1,
        "Min_Profit_Robux": 50
    },
    "Blacklist_AssetIDs": [123456789, 987654321]
}
```

### Aggressive (Fast)
```json
{
    "Cookie": "your_cookie_here",
    "TOTP_Secret": "your_2fa_secret",
    "Undercut": {
        "Type": "robux",
        "Value": 1
    },
    "Settings": {
        "Threads": 10,
        "Ask_Confirmation": false,
        "Hide_On_Sale": true,
        "Keep_Best_Serials": 10,
        "Keep_Copy": 0,
        "Min_Profit_Robux": 10
    },
    "Blacklist_AssetIDs": []
}
```

## Getting Your TOTP Secret

If you have 2FA enabled on your Roblox account, you'll need the TOTP secret to allow the bot to automatically solve 2FA challenges:

1. When setting up 2FA, Roblox shows a QR code
2. Instead of scanning it, look for the "Can't scan?" or manual entry option
3. Copy the secret key (usually a string of letters/numbers)
4. Paste it in the `TOTP_Secret` field

> ⚠️ If you already have 2FA set up, you'll need to disable and re-enable it to get the secret.

## Logs

All activity is logged to `bot_log.txt` for debugging purposes.

## Contributing
This project is **open source** and contributions are welcome! If you'd like to fix a bug, optimize performance, or add new features:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

## License
This project is licensed under the **GNU General Public License v3.0** - see the [LICENSE](https://github.com/Aspectise/Resell-Bot/blob/main/LICENSE) file for details.

## Help

If you need help setting up the bot, join the [Discord](https://discord.gg/deathsniper)
