# labyrinthmc-map

Published [BlueMap](https://bluemap.bluecolored.de/) output for the Labyrinth
Minecraft server — 3D web maps of every world.

**Live:** [map.labyrinthmc.org](https://map.labyrinthmc.org)

## ⚠️ This repository is generated output, not source

Nothing here is hand-written. The entire tree is produced by BlueMap on the
Minecraft server and pushed to this repo, which GitHub Pages serves at the
domain in `CNAME`.

**Do not edit files here.** Any change will be overwritten by the next map
update. To change how the map looks or behaves, change the BlueMap
configuration on the server and let it regenerate.

## How it updates

An automated job on the Minecraft server runs BlueMap and pushes the result.
Commits look like:

```
Map update 2026-08-20 18:00 UTC
Map update 2026-08-19 23:00 UTC
Map update 2026-08-19 22:00 UTC
```

Roughly hourly while the server is active. There is **no GitHub Actions
workflow** in this repo — the push comes from the server side, so if the map
stops updating, the problem is there, not here.

## Layout

| Path | Contents |
|---|---|
| `index.html` | The BlueMap web app |
| `settings.json` | BlueMap client config — which maps exist, default view, zoom limits |
| `maps/` | Generated tile data, one directory per world |
| `assets/` | BlueMap's compiled JS/CSS bundles and fonts |
| `lang/` | BlueMap UI translations |
| `CNAME` | GitHub Pages custom domain (`map.labyrinthmc.org`) |

### Worlds

`maps/` currently contains six generated worlds:

`world` · `world_nether` · `world_the_end` · `creative` · `hub_rainbow` ·
`parkour_biome_run_remix`

Note that `settings.json` only *lists* four of them:

```json
"maps": ["parkour_biome_run_remix", "world", "creative", "hub_rainbow"]
```

`world_nether` and `world_the_end` have tile data on disk but are not exposed
in the map switcher. That is BlueMap's server-side config deciding what to
publish — if the Nether and End should be browsable, they need enabling there,
not here.

The default view opens on `hub_rainbow`.

## Size

~2,500 files. Because every update rewrites tile data, this repository's
history grows steadily. If clone size ever becomes a problem, the fix is to
squash history or start the repo fresh — the tiles are reproducible from the
world files, so nothing of value is lost by discarding old commits.

## Related

- **labyrinthmc.org** — the main server website
- **Labyrinth-Press-App** — unrelated; that's the student newspaper
