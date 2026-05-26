# setup-ardent

GitHub Action to install the [ardent](https://github.com/idleberg/ardent) NSIS formatter CLI.

## Usage

### Basic

```yaml
- name: Setup ardent
  uses: idleberg/setup-ardent@v1
```

### With specific version

```yaml
- name: Setup ardent
  uses: idleberg/setup-ardent@v1
  with:
    version: "0.3.1"
```

## Inputs

| Input     | Description                  | Required | Default  |
| --------- | ---------------------------- | -------- | -------- |
| `version` | Version of ardent to install | No       | (latest) |

## Rust Toolchain

This action automatically installs a minimal Rust toolchain if `cargo` is not already available. If your workflow already sets up Rust (e.g. via [actions-rust-lang/setup-rust-toolchain](https://github.com/actions-rust-lang/setup-rust-toolchain)), the existing installation will be used instead.

## Example Workflow

```yaml
name: Format NSIS Scripts

on:
  push:
    branches: [main]

jobs:
  format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup ardent
        uses: idleberg/setup-ardent@v1

      - name: Format scripts
        run: ardent format --write **/*.nsi
```

## License

This work is licensed under [The MIT License](LICENSE).MIT
