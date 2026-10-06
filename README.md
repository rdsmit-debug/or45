# OR 45 · Digital Twin (iPhone version)

A phone-friendly web page for the OR 45 Gaussian-splat scan. Open the GitHub Pages link on any iPhone, iPad or computer: no app, no login.

## Publish (one time, about 5 minutes)

1. On github.com, create a new repository called `or45`. Set it to **Public**, because free GitHub Pages needs a public repo.
2. On the new repo's page, click **uploading an existing file**. Drag in everything *inside* this folder: `index.html`, `viewer.js`, `viewer.css`, `icon-180.png`, `preview.jpg`, `README.md` and the `scene` folder. Then click **Commit changes**.
3. Go to **Settings → Pages**. Under "Build and deployment", choose **Deploy from a branch**, then **main** and **/ (root)**, and click **Save**.
4. After a minute or two the link appears at the top of that page. It looks like `https://YOUR-USERNAME.github.io/or45/`.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The page: loading screen, how-to card, view buttons |
| `viewer.js`, `viewer.css` | PlayCanvas SuperSplat viewer v1.37 (engine 2.23), unchanged |
| `scene/` | The scan as streamed levels of detail (6M → 3M → 1.5M → 600k → 240k splats) |
| `icon-180.png` | Home-screen icon |
| `preview.jpg` | Image shown when the link is pasted into iMessage, WhatsApp or Slack |

Phones show the coarsest level within seconds and sharpen as more detail streams in. Each device draws no more splats than it can handle: about 1–2M on a phone and up to 4M on a desktop.

## Editing the view buttons

The buttons are set in `index.html`, in the `VIEWS` list near the top of the script. Each one has a `label`, a camera `position`, a `target` it looks at, and a `fov` (zoom). To try out a pose, add `?cam=x,y,z,tx,ty,tz,fov` to the link.

Useful link options: `?webgl` forces WebGL instead of WebGPU, `?ministats` shows the frame rate, and `?budget=1` caps splats at 1 million.
