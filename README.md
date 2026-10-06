# OR 45 · Digital Twin (iPhone version)

A phone-friendly web page for the OR 45 Gaussian-splat scan. Open the GitHub Pages link on any iPhone, iPad or computer: no app, no login.

## Publish (one time, about 5 minutes)

1. On github.com, create a new repository called `or45`. Set it to **Public**, because free GitHub Pages needs a public repo.
2. On the new repo's page, click **uploading an existing file**. Drag in everything *inside* this folder: `index.html`, `viewer.js`, `viewer.css`, `icon-180.png`, `preview.jpg`, `README.md` and the `scene` folder. Then click **Commit changes**.
3. Go to **Settings → Pages**. Under "Build and deployment", choose **Deploy from a branch**, then **main** and **/ (root)**, and click **Save**.
4. After a minute or two the link appears at the top of that page. It looks like `https://YOUR-USERNAME.github.io/or45/`.

## Updating the live site

Replace the changed files in this folder. Then, in GitHub Desktop, write a short summary, click **Commit to main**, then **Push origin**. The live link updates within a minute or two. If an iPhone still shows the old version, reload the page.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The page: loading screen, how-to card, view buttons |
| `viewer.js`, `viewer.css` | PlayCanvas SuperSplat viewer v1.37 (engine 2.23), plus a three-line resolution patch |
| `scene/` | The scan as streamed levels of detail (6M → 3M → 1.5M → 600k → 240k splats) |
| `icon-180.png` | Home-screen icon |
| `preview.jpg` | Image shown when the link is pasted into iMessage, WhatsApp or Slack |

Phones show the coarsest level within seconds and sharpen as more detail streams in. Each device draws no more splats than it can handle: about 2M on a phone and up to 4M on a desktop.

## Image quality settings

- **Full resolution when still.** The stock viewer renders phones at half resolution all the time. This page renders at full resolution whenever the camera is still, and drops to 60% only while you're dragging, so movement stays smooth. `viewer.js` has a small patch for this (search for `OR45 patch`).
- **2M splats on phones**, double the stock 1M.
- **Background prefetch.** Once the first view has loaded, finer detail downloads quietly in the background, so turning around doesn't show blurry patches while it streams.
- **Light sharpening and a little extra contrast.** Add `?sharp=0&grade=0` to the link to see the image without them.
- **Escape hatch for old phones.** If an older phone stutters, add `?fast` to the link to get the stock half-resolution, 1M-splat mode.

## Editing the view buttons

The buttons are set in `index.html`, in the `VIEWS` list near the top of the script. Each one has a `label`, a camera `position`, a `target` it looks at, and a `fov` (zoom). To try out a pose, add `?cam=x,y,z,tx,ty,tz,fov` to the link.

Useful link options: `?webgl` forces WebGL instead of WebGPU, `?ministats` shows the frame rate, `?budget=1` caps splats at 1 million, `?noprefetch` turns off background downloading, and `?motionscale=1` keeps full resolution while moving.
