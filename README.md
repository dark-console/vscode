# Dark Console — VS Code

The Dark Console color theme for Visual Studio Code. One port in the [dark-console](https://github.com/dark-console) suite — the palette lives in [`dark-console/core`](https://github.com/dark-console/core)'s `palette.json`, this repo ships the VS Code concrete file.

## Install

```bash
npx @vscode/vsce package
code --install-extension dark-console-vscode-1.0.0.vsix --force
```

Then in VS Code: `Ctrl+K, Ctrl+T` → pick **Dark Console**.

## Don't edit `themes/dark_console.json` by hand

Every color traces to `dark-console/core/palette.json`. If a value needs to change, it changes *there first*; then re-build the port. (For now: bump `palette.json`, re-copy the values in, re-`vsce package` — the generator path for this port is a TODO; the drift-checker in `core/scripts/validate.py` is the hard stop until it lands.)

## Per-user color rules (read-first, never-forced)

- **Font.** Our theme does *not* set any `fontFamily` key. VS Code's `editor.fontFamily` and `editor.fontLigatures` wins always. When the user sets them, they own it.
- **Density.** Our theme does not force `workbench.view` widths or editor padding. The user's layout is the layout.
- **Accent override.** If a user wants a different `editorCursor.foreground` / `workbench.activityBarBadge.background` / etc., the sanctioned mechanism is `workbench.colorCustomizations` in user settings — that's exactly the per-user resilient layer the suite's [design/settings.md](https://github.com/dark-console/core/blob/master/design/settings.md) describes.

## Token coverage

This port exposes ~337 semantic VS Code color keys (`colors`), 47 TextMate scopes (`tokenColors`), and 24 semantic highlight slots (`semanticTokenColors`). Count, call, and spelling of keys are *VS Code's schema*, not the suite's. The suite's contract is only: the *hexes* in those keys come from the palette.

## License

MIT — see [LICENSE](LICENSE).
