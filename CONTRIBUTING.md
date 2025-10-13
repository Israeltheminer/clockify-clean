# Contributing to Clockify Clean

First off, thank you for considering contributing to Clockify Clean! It's people like you that make this tool better for everyone.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates. When you create a bug report, include as many details as possible:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples** (command you ran, expected vs actual output)
- **Describe the behavior you observed and what you expected**
- **Include system information** (macOS version, Clockify Desktop version)
- **Include relevant logs** (use `--verbose` flag for detailed output)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description** of the suggested enhancement
- **Explain why this enhancement would be useful** to most users
- **List any alternative solutions** you've considered

### Pull Requests

1. Fork the repo and create your branch from `main`
2. If you've added code, test it thoroughly
3. Ensure your code follows the existing style
4. Update the README.md if needed
5. Write a clear commit message

## Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/clockify-clean.git
cd clockify-clean

# Make the script executable
chmod +x clockify-clean

# Test your changes
./clockify-clean --dry-run
```

## Code Style Guidelines

- Use clear, descriptive variable names
- Add comments for complex logic
- Follow existing code structure and patterns
- Use shell best practices (set -euo pipefail, quote variables, etc.)
- Test with various scenarios before submitting

## Testing Checklist

Before submitting a PR, test the following:

- [ ] Dry-run mode works correctly
- [ ] Batch mode works correctly
- [ ] Interactive mode works correctly
- [ ] Verbose mode shows appropriate detail
- [ ] Error handling works (database locked, no entries, etc.)
- [ ] Works with different date ranges
- [ ] Handles edge cases (empty descriptions, no URLs, etc.)

## Commit Message Guidelines

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters
- Reference issues and pull requests after the first line

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
