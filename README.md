# Theme Studio

Static HTML, CSS, and browser JavaScript theme playground. There is no React, Next.js, Tailwind build, package install, or Node server at runtime. The existing Tailwind utility styles are included in `styles.css`.

## Run locally

On Windows, double-click `start.cmd` or run it from a terminal:

```powershell
.\start.cmd
```

Keep that window open, then visit <http://127.0.0.1:8000>. To choose another port, run `.\start.cmd --port 9000`.

You can also start the server directly with Python:

```bash
python serve.py
```

If port 8000 is already in use, run `python serve.py --port 9000` and open <http://127.0.0.1:9000>.

You can also place these files on any static host. Keep `index.html`, `styles.css`, `app.js`, `brand-checks.js`, `media/`, `brand-assets/`, and the three root icon files together. The Brand tab's format checks require an HTTP server because browsers do not allow its asset fetches from `file://`.

## Edit the theme

- Edit the CSS variables in the **Live CSS editor** to preview changes immediately, then use **Copy CSS** to save them.
- To change the starting theme for everyone, edit the `:root` and `.dark` rules in the `#live-theme` style and `#theme-css` textarea in `index.html` together. The textarea contains the editor's reset value.
- `styles.css` contains the compiled utility styles and component rules from the previous Tailwind setup. It is committed, so running the site needs no build step. Edit this file directly when changing component styles or adding utility classes.
- `app.js` handles tabs, the light/dark toggle, editor, form, icons, dashboard navigation, order book, and trading panel. `brand-checks.js` validates the included brand assets.

## Theme presets

The **Theme** picker in the header swaps the whole token set. The current Aeris theme stays the default. Each preset is a file in `themes/` with the same `:root` (light) and `.dark` (dark) token blocks as the default, so the light/dark toggle still works:

| Preset | File | Light / dark variants |
| --- | --- | --- |
| Tokyo Night | `themes/tokyo-night.css` | Day / Night |
| Catppuccin | `themes/catppuccin.css` | Latte / Mocha |
| GitHub | `themes/github.css` | Light / Dark |
| One Dark / Light | `themes/one.css` | Atom One Light / One Dark Pro |
| Dracula | `themes/dracula.css` | Alucard / Dracula |
| Solarized | `themes/solarized.css` | Light / Dark |
| Gruvbox | `themes/gruvbox.css` | Light / Dark (medium) |

Choosing a preset loads its file into the Live CSS editor, so you can tweak it there and **Copy CSS** exports it. **Reset** returns to the selected preset. The choice is saved in the browser. Presets are fetched, so they need the local HTTP server, like the Brand checks.

To add a preset, copy one of the files in `themes/`, change the values, and add an `<option>` with the file name (without `.css`) to the `#theme-preset` select in `index.html`.

Brand asset guidance is in [brand-assets/usage.md](brand-assets/usage.md).
