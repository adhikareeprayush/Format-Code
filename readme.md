# GitHub Action: Format Code with Prettier

![GitHub Marketplace Version](https://img.shields.io/github/v/release/adhikareeprayush/format-code?label=Version&logo=github)
![GitHub Releases](https://img.shields.io/github/downloads/adhikareeprayush/format-code/total?label=Downloads&logo=github)
![GitHub Marketplace Stars](https://img.shields.io/github/stars/adhikareeprayush/format-code?label=Stars&logo=github)
![GitHub License](https://img.shields.io/github/license/adhikareeprayush/format-code?label=License)

Automatically format your code with Prettier in GitHub Actions workflows.

## Features

- Format code using Prettier in GitHub Actions workflows.
- Customizable Prettier configuration using `.prettierrc` or `prettier.config.js`.
- Supports formatting JavaScript, TypeScript, CSS, JSON, YAML, and more.

## Usage

To use this GitHub Action in your workflow, add a step like the following:

```yaml
- name: Format Code with Prettier
  uses: adhikareeprayush/format-code@v1
```

You can configure additional options for Prettier by creating a `.prettierrc` or `prettier.config.js` file in your repository.

## Inputs

- `path`: The file or directory path to format (default: `.`).
- `prettier-version`: The version of Prettier to use (default: latest).

```yaml
- name: Format Code with Prettier
  uses: adhikareeprayush/format-code@v1
  with:
    path: 'src/'
    prettier-version: '2.7.1'
```

## Outputs

This action does not provide any outputs.

## Example Workflow

Here's an example workflow that formats code using Prettier:

```yaml
name: Format Code

on: [push, pull_request]

jobs:
  format:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Format Code with Prettier
        uses: adhikareeprayush@gmail.com/format-code@v1
        with:
          path: 'src/'
          prettier-version: '2.7.1'

      - name: Commit formatted code
        run: |
          git config --global user.name 'github-actions[bot]'
          git config --global user.email 'github-actions[bot]@users.noreply.github.com'
          git add .
          git commit -m 'Format code with Prettier'
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        continue-on-error: true
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support or questions, please open an issue in the GitHub repository or contact [adhikareeprayush@gmail.com](mailto:adhikareeprayush@gmail.com).
