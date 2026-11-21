# Contributing to ferropod

Thank you for your interest in contributing to **ferropod**!

## Development Workflow

1. Fork the repository and create a topic branch from `main`.
2. Ensure formatting and checks pass before opening a Pull Request:
   ```bash
   cargo fmt --check
   cargo clippy --all-targets
   cargo test
   ```
3. Keep PRs focused and well-scoped. Reference related issues or milestones in your PR description.

## Architecture & Contracts

Before making structural changes, please review:
- [Architecture Specification](https://github.com/ferropod/ferropod/blob/main/docs/ARCHITECTURE.md)
- [WIT Host Binding Contract](https://github.com/ferropod/ferropod/blob/main/wit/platform.wit)

## License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.
