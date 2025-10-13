# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-10-13

### Added
- Initial release of Clockify Clean
- Smart filtering with whitelist/blacklist for apps and domains
- Three operation modes: dry-run, batch, and interactive
- Domain/app grouping for efficient bulk decisions
- Verbose logging option for detailed output
- Direct SQLite database access for performance
- Comprehensive error handling and user feedback
- Safety features (confirmations, dry-run, database lock detection)
- Colorized console output for better readability
- Support for macOS with zsh shell

### Features
- Auto-delete blacklisted entries (Spotify, Netflix, social media, etc.)
- Auto-keep whitelisted entries (Cursor, Figma, GitHub, localhost, etc.)
- Interactive review for undecided entries
- Batch mode for reviewing all entries before deletion
- Days back filter (default 7 days, customizable)
- Skip confirmation option for automation
- Database locking detection and helpful error messages

### Documentation
- Comprehensive README with installation and usage instructions
- MIT License
- Contributing guidelines
- Code of conduct (implicit in contributing guidelines)

[1.0.0]: https://github.com/Israeltheminer/clockify-clean/releases/tag/v1.0.0
