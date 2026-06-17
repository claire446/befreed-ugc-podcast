# BeFreed audio prototype

Single-file web app (`index.html`). Open it directly, or serve the folder:

```bash
cd befreed-app
python3 -m http.server 8000
# open http://localhost:8000
```

> Tip: serve over http (not double-clicking `file://`) so the audio-wave
> analyser can read amplitude. It still works on `file://` — it just falls
> back to a synthetic bounce animation.

## Flow
Library (tap a book) → 5-4-3-2-1 countdown → Podcast player (audio auto-plays,
bars + book bounce to the audio, karaoke captions) → tap **Talk** (audio pauses,
caption → "Listening…", mic + X appear) → tap **mic** (plays your staged reply
clip) → tap **X** (back to podcast, narration resumes). `‹` returns to library.

## What to drop in
Edit the `BOOKS` array near the top of the `<script>` in `index.html`:

| field       | what it is |
|-------------|------------|
| `cover`     | cover image path, e.g. `assets/cover-head.jpg` (leave `""` for the CSS placeholder) |
| `audio`     | narration that auto-plays in podcast mode |
| `talkAudio` | staged reply clip played when the mic is tapped in talk mode |
| `captions`  | `[{ t: seconds, text: "..." }]` — shown karaoke-style; line changes when `currentTime` passes each `t` |

Put the files in `assets/`. Responsive: phone = 2-col grid, iPad = 3-col, player centered.
