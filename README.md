# A-Frame AR Example

Winter-themed AR demo based on the A-Frame AR example (A-Frame 1.7.1).

## What it does

- Detects a **horizontal surface** (floor / table) in WebXR AR.
- Shows a small **reticle** where a surface is detected.
- **Tap to place** a winter object at the reticle (alternates between **snowman** and **pine tree**).

## Local preview (no AR, just 3D)

You can preview the scene in any desktop browser with a simple static server:

```bash
cd aframe-ar-example
python -m http.server 8080
```

Then open `http://localhost:8080`.

### Desktop “AR simulation” (no Android required)

If you don’t have an Android phone, this project still demonstrates the intended AR interaction:

- A visible **ground plane** stands in for “the detected real-world plane”.
- A **reticle** follows your mouse over the plane (raycast).
- Click / tap places objects exactly like AR placement would.

This is implemented via a small fallback component (`desktop-hit-test`) and is useful for explaining “how we wanted to solve it” during the exam.

## AR on Android (HTTPS required)

AR hit-test only works reliably in **recent Chrome on Android**, and you must load the page over **HTTPS**.

Recommended workflow:

1. Create an empty GitHub repo (or fork this repo).
2. Push your code to GitHub.
3. Enable **Settings → Pages → Deploy from branch → `main` / (root)**.
4. Open: `https://YOUR_GITHUB_USERNAME.github.io/aframe-ar-example/`

## Notes for the exam

- The original example moved a single object with `ar-hit-test="target: #objects"`.
- This version instead moves a **reticle** (`ar-hit-test="target: #reticle"`) and spawns **new clones on tap**.
