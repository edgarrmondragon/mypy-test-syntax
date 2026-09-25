## mypy-test-syntax

A simple VS Code extension that adds syntax highlighting for [mypy's test case files](https://github.com/python/mypy/blob/v2.3.1/test-data/unit/check-enum.test) (`test-data/unit/*.test`).

It highlights the `[case ...]` / `[file ...]` / `[out]` section markers and `--` comments, and embeds Python syntax highlighting for the code in between.

### Install

This isn't published to the Marketplace. Clone it, then symlink the clone into VS Code's extensions folder, using the `publisher.name-version` naming convention VS Code expects (built from the `publisher`, `name`, and `version` fields in `package.json`):

```sh
git clone https://github.com/edgarrmondragon/mypy-test-syntax.git
ln -s "$(pwd)/mypy-test-syntax" ~/.vscode/extensions/local.mypy-test-syntax-1.0.0
```

Then fully quit and reopen VS Code. Future edits to this repo take effect after a restart, with no reinstall step.

Any file matching `**/test-data/unit/*.test` is associated with this language automatically.

### Customize colors

Section markers use dedicated scopes (`keyword.control.section.mypy-test`, `entity.name.function.mypy-test`, `punctuation.definition.tag.mypy-test`) that most themes won't render distinctly out of the box. Force specific colors or bold via `editor.tokenColorCustomizations`, e.g. in the target repo's `.vscode/settings.json`:

```json
{
  "editor.tokenColorCustomizations": {
    "textMateRules": [
      { "scope": "keyword.control.section.mypy-test", "settings": { "foreground": "#c586c0", "fontStyle": "bold" } },
      { "scope": "entity.name.function.mypy-test", "settings": { "foreground": "#4ec9b0", "fontStyle": "bold" } },
      { "scope": "punctuation.definition.tag.mypy-test", "settings": { "foreground": "#808080" } }
    ]
  }
}
```
