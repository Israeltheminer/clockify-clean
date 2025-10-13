# 🧹 Clockify Clean

> Intelligently clean up Clockify autotracker entries by removing non-work time tracking data

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![macOS](https://img.shields.io/badge/platform-macOS-lightgrey)](https://www.apple.com/macos/)
[![Shell](https://img.shields.io/badge/shell-zsh-blue)](https://www.zsh.org/)

## Overview

**Clockify Clean** is a powerful command-line tool that helps you maintain clean and accurate time tracking data in Clockify Desktop by intelligently removing unwanted autotracker entries. Perfect for developers and professionals who want to keep only work-related time entries.

### Features

✨ **Smart Filtering**
- Whitelist/blacklist apps and domains automatically
- Group similar entries by domain for bulk decisions
- Interactive review for undecided entries

🎯 **Flexible Modes**
- **Dry-run mode**: Preview what would be deleted
- **Batch mode**: Review all entries, then delete in one go
- **Auto mode**: Skip confirmation prompts

⚡ **Performance**
- Direct SQLite database access for speed
- Efficient entry grouping and processing
- Handles hundreds of entries quickly

## Installation

### Prerequisites

- macOS (tested on macOS Sonoma and later)
- Clockify Desktop app installed
- `sqlite3` (pre-installed on macOS)
- `zsh` shell (default on modern macOS)

### Quick Install

```bash
# Download the script
curl -o ~/.local/bin/clockify-clean https://raw.githubusercontent.com/Israeltheminer/clockify-clean/main/clockify-clean

# Make it executable
chmod +x ~/.local/bin/clockify-clean

# Ensure ~/.local/bin is in your PATH
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Manual Install

1. Clone this repository:
   ```bash
   git clone https://github.com/Israeltheminer/clockify-clean.git
   cd clockify-clean
   ```

2. Copy the script to your local bin:
   ```bash
   cp clockify-clean ~/.local/bin/
   chmod +x ~/.local/bin/clockify-clean
   ```

3. Ensure `~/.local/bin` is in your PATH (add to `~/.zshrc` if needed)

## Usage

### Basic Usage

```bash
# Preview what would be deleted (last 7 days)
clockify-clean --dry-run

# Review and delete entries interactively
clockify-clean

# Check last 30 days
clockify-clean -d 30

# Batch mode: review all at once
clockify-clean --batch
```

### Command-Line Options

| Option | Description |
|--------|-------------|
| `-d, --days <num>` | Number of days back to check (default: 7) |
| `--dry-run` | Show what would be deleted without actually deleting |
| `--batch` | Show all entries first, then confirm batch deletion |
| `-y, --yes` | Skip confirmation prompts (use with caution!) |
| `-v, --verbose` | Show detailed output for all operations |
| `-h, --help` | Show help message |

### Examples

```bash
# Preview last 7 days without deleting
clockify-clean --dry-run

# Interactively review and delete entries from last 14 days
clockify-clean -d 14

# Batch mode: see all entries first, then decide
clockify-clean --batch --verbose

# Auto-delete last 30 days (skips prompts - be careful!)
clockify-clean -d 30 -y
```

## How It Works

### Filtering Strategy

The script uses a three-tier filtering approach:

#### 1. **Whitelist (Always Keep)**
- **Apps**: Cursor, Figma, Microsoft Teams, Tor Browser, Docker Desktop
- **Domains**: github.com, localhost, vercel.com, console.cloud.google.com, etc.

These entries are automatically kept as they're considered work-related.

#### 2. **Blacklist (Always Delete)**
- **Apps**: Spotify, Netflix, Mail, Finder, Clockify Desktop, Messages, Preview
- **Domains**: x.com, linkedin.com, youtube.com, coinmarketcap.com, tradingview.com, etc.

These entries are automatically deleted as they're typically non-work activities.

#### 3. **Interactive Review**
Entries not in whitelist or blacklist are grouped by domain/app and presented for your decision:
- Review grouped entries
- See how many entries share the same domain
- Choose to delete all or keep all from that domain

### Database Access

The script directly accesses the Clockify Desktop SQLite database located at:
```
~/Library/Application Support/Clockify Desktop/Clockify_*.sqlite
```

**Note**: Close the Clockify Desktop app before running to avoid database locks.

## Configuration

### Customizing Filters

You can customize the whitelist/blacklist by editing the script directly. Look for these sections:

```bash
# App filtering configuration
WHITELIST_APPS=("Cursor" "Figma" "Microsoft Teams" ...)
BLACKLIST_APPS=("loginwindow" "Spotify" "Netflix" ...)

# Domain filtering configuration
WHITELIST_DOMAINS=("github.com" "localhost" ...)
BLACKLIST_DOMAINS=("x.com" "linkedin.com" ...)
```

## Safety Features

- **Dry-run mode**: Test before deleting
- **Confirmation prompts**: Asks before each deletion (unless `-y` is used)
- **Batch review**: See everything before committing
- **Database locking detection**: Warns if Clockify is running
- **Verbose logging**: Track what's happening with `-v` flag

## Troubleshooting

### Database Locked Error
```
[ERROR] Database is locked - please close Clockify Desktop app and try again
```
**Solution**: Quit the Clockify Desktop application before running the script.

### Script Not Found
```
zsh: command not found: clockify-clean
```
**Solution**: Ensure `~/.local/bin` is in your PATH:
```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### No Entries Found
```
[INFO] No unsaved autotracker entries found in the specified date range
```
This is normal - it means all your autotracker entries have already been added to time entries or there are no entries in the date range.

## Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit your changes**: `git commit -m 'Add some amazing feature'`
4. **Push to the branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Ideas for Contributions

- [ ] Support for Linux/Windows
- [ ] Configuration file support (YAML/JSON)
- [ ] Pattern matching for descriptions
- [ ] Export deleted entries before removal
- [ ] Undo/restore functionality
- [ ] GUI interface

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built for the [Clockify](https://clockify.me/) time tracking platform
- Inspired by the need for clean, accurate time tracking data

## Disclaimer

This tool directly modifies the Clockify Desktop database. While it includes safety features, always:
- **Backup your Clockify data** before use
- **Test with `--dry-run`** first
- **Close Clockify Desktop** before running

Use at your own risk. The author is not responsible for any data loss.

---

Made with ❤️ by [Israel Iyanda](https://github.com/Israeltheminer)

**Star this repo if you find it useful!** ⭐