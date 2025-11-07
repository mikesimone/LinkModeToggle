# LinkModeToggle — ComfyUI link render mode hotkeys + button

**Make the canvas readable at a glance.** LinkModeToggle adds:

* **Hotkeys:** `F8` or `Ctrl+K` to cycle **Spline → Linear → Straight**
* **Toolbar button:** a small bottom-right canvas button (next to Fit/Zoom/Minimap) with a mini badge showing the current mode
* **Persistence:** remembers your last mode per browser (localStorage)

Designed for the modern ComfyUI frontend (v1.31+), but falls back gracefully on older LiteGraph builds.

---

## Why?

Complex graphs look like spaghetti when every link’s a spline. Straight/linear links reduce visual noise and help you route with intent. Toggling on demand beats digging through menus.

---

## Features

* Zero server changes — pure front-end extension
* **Hotkeys:** `F8`, `Ctrl+K`
* **UI button:** docks into the standard bottom-right canvas control group
* Smart compatibility: tries multiple internal APIs (`setLinkRenderMode`, `links_render_mode`, `render_curved_links`) for different Comfy/LiteGraph builds

---

## Install

Use **ComfyUI-Manager** or manual:

### Manager

* Open *ComfyUI-Manager* → **Install from URL** → paste:

  ```
  https://github.com/YOUR_GITHUB_USERNAME/LinkModeToggle
  ```
* Restart ComfyUI

### Manual

```
ComfyUI/
└─ custom_nodes/
   └─ LinkModeToggle/
      ├─ __init__.py
      └─ web/
         ├─ index.js
         ├─ index.css
         └─ extensions/
            └─ linkmode-toggle.js
```

Restart ComfyUI and hard-refresh the browser (Ctrl+F5).

---

## Usage

* Press **F8** or **Ctrl+K** to cycle modes.
* Click the **curve icon** button in the bottom-right canvas controls.
* The tiny badge shows **S/L/S** for Spline/Linear/Straight.
* Your choice persists across reloads.

---

## Uninstall

Remove `custom_nodes/LinkModeToggle` and restart ComfyUI.

---

## Troubleshooting

* No button? Hard-refresh (**Ctrl+F5**) and ensure `web/index.js` imports `./extensions/linkmode-toggle.js`.
* Button floating? We fall back to a bottom-right floating dock if the toolbar isn’t detected (some forks/themes). It’ll still work.
* Console check:

  ```js
  app?.extensions?.LinkModeToggle
  ```

---

## License

MIT © Mike Simone
