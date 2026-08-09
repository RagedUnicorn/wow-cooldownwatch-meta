# Gallery Images

Static overview images for the CooldownWatch pages on
[wago.io](https://addons.wago.io/addons/cooldownwatch/gallery) and
[CurseForge](https://www.curseforge.com/wow/addons/cooldownwatch). They give visitors a quick
visual summary of CooldownWatch's target cooldown bar and configuration straight from the
gallery/screenshot strip - the embedded screenshots and full context live in the
project's `DESCRIPTION.md`. This rarely needs updating; this folder is the source of
truth when it does.

**How these are made:** normally you do not build them by hand - the `wow-media-capture`
skill's `postprocess-shots.ps1` crops each in-game screenshot to the logged frame rect and
writes the 16:9 gallery variant automatically. The rest of this section is the manual
fallback, and documents exactly what that script runs.

Start from a fresh screenshot (any size) and normalize it to a 16:9 canvas under 2 MB:

```
magick <name>.png -resize 1600x900 -background black -gravity center -extent 1600x900 <name>.png
```

Use `magick`, not ffmpeg. The earlier recipe used
`ffmpeg -vf "scale=...:force_original_aspect_ratio=decrease,pad=..."`, but ffmpeg's docker
wrapper hangs when run synchronously from a non-interactive shell (it blocks on the
inherited null-device stdin even with `-nostdin`), whereas magick over the identical
wrapper completes. Same visual result.

Both tools are containerised, so `cd` into the folder first and pass **relative**
filenames - magick parses a leading `C:` as the raw cyan-channel coder and dies with
`must specify image size`.

Black bars blend into the dark WoW scenes, and 16:9 keeps wide captures from rendering as
thin strips. Sizes stay under **2 MB** to clear CurseForge's 2 MB cap (wago allows up to
3072 KB). Drop the box to `1440x810` for noisy full-scene shots that creep over 2 MB at
1600×900.

**Shrink-only matters.** Plain `-resize` *enlarges* a crop smaller than the box to fill it,
where the old ffmpeg `decrease` recipe only ever shrank - an in-world crop smaller than the
box would be blown up before padding. `postprocess-shots.ps1` resizes only when the crop
exceeds the box, so small crops are padded at native size.

Doing it by hand, append `>` to the geometry so it never upscales:

```
magick <name>.png -resize "1600x900>" -background black -gravity center -extent 1600x900 <name>.png
```

That works from Git Bash. It does **not** work from PowerShell: `magick` is a `.cmd`
wrapper, so an unquoted `>` reaching cmd.exe is parsed as output redirection and the command
fails with ``no decode delegate for `black'``. That is why the script decides in code rather
than relying on the geometry flag.

**Titles vs. descriptions:** CurseForge gallery images take both a **title** and a
**description**; wago only takes a description. The heading of each section below is used
as the CurseForge title, and the caption block is the description (and the wago caption).

Upload it by hand in the gallery section of each dashboard.

---

## Not captured yet

CooldownWatch is unreleased and has no in-game captures, so this folder holds no images yet
and there is no `wow-media-capture` manifest for the addon under the skill's
`reference/media/`. The strip is expected to cover, in this order:

1. **Target Cooldown Bar** - the bar tracking a target's cooldowns during a fight.
2. **Cooldown Selection** - the per-category spell list with cooldowns enabled and disabled.
3. **Worst Case & Overrides** - the per-spell worst case toggle and cooldown override field.
4. **Configuration Profiles** - the Profiles tab with export/import.

Once the captures exist, replace this section with one `## <n>. <Title>` block per image -
the embedded `![](<file>.png)`, the caption in a fenced block, and a `**File:**` line -
matching `wow-pulse-meta/assets/gallery/README.md`.
