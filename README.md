# A-Frame AR Example (winter thing)

This is my solution for **Exercise 05 (Virtual & Augmented Reality)**.
It’s based on the example repo and uses **A-Frame 1.7.1**.

## What it is / what you can do

Basically it’s a tiny winter AR “decorator”:
- it tries to find a flat surface (floor/table) (in real AR)
- it shows a small **reticle ring**
- you **tap to place** an object at the reticle (I made **snowman** + **pine tree**)
- it alternates snowman/tree so you can see both quickly

## Running it locally (no AR)

This works on any normal browser, it’s just the 3D scene (no real AR sensors):

```bash
cd aframe-ar-example
python -m http.server 8080
```

Open: `http://localhost:8080`

## Desktop “AR simulation” mode (because I don’t have Android)

So the original exercise wants WebXR AR hit-test (works mainly on **Chrome Android**).
I don’t have an Android phone, so I added a simple fallback so I can still show the idea on my laptop:

- there is a visible **ground plane** (pretend it’s the detected floor/table)
- the **reticle follows the mouse** (raycast)
- clicking places the snowman/tree at the reticle (same placement logic as AR)

This is done in a small component called `desktop-hit-test`.
It’s not “real AR”, but it demonstrates how I would solve the interaction (reticle + tap-to-place).

## Hosting (HTTPS) for “real” AR

AR needs **HTTPS**, so use GitHub Pages:

1. Push to GitHub
2. Repo → **Settings → Pages**
3. Source: *Deploy from branch*
4. Branch: `main` and folder: `/ (root)`
5. Wait a bit and open your Pages URL

Note: iPhone/iOS usually won’t run this WebXR AR hit-test flow, so don’t rely on it for the demo.

### iPhone “camera mode” (pseudo‑AR)

I added a button **Enable Camera** on the page.
This turns on the phone camera and shows it behind the 3D scene, so it *looks* like AR.
But it’s still not real plane detection (the placement is still on my fake plane / raycast).
It’s mostly so I can show something closer to the assignment on iPhone.

## Notes (what I changed vs the starter)

- starter repo was moving one object with `ar-hit-test="target: #objects"`
- mine moves a **reticle** (`ar-hit-test="target: #reticle"`) and **spawns new objects on tap** (bonus task)
