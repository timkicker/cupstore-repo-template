# Wii U Mod Store: Repository Template

This is the official template for hosting mods on the **Wii U Mod Store** app.

## How to use

1. Fork this repository
2. Edit `repo.json` with your repo name and author
3. Add your games under `games/[game-id]/game.json`
4. Host your mod ZIPs anywhere (GitHub Releases, direct links, etc.)
5. Add your raw `repo.json` URL to the Mod Store app

## Repository URL format

After forking, your repo index URL will look like:
```
https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/repo.json
```

Add this to `sd:/wiiu/apps/modstore/config.json` on your Wii U SD card:
```json
{
  "repos": [
    "https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/repo.json"
  ]
}
```

## Folder structure

```
repo/
├── repo.json               ← Repo index (required)
└── games/
    └── [game-id]/
        ├── game.json       ← Game info + mod list
        └── assets/
            └── cover.png   ← Game cover image (optional)
```

## Mod types

- `mod`: A single standalone mod
- `modpack`: A bundle of multiple mods installed together

## game.json fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | yes | Display name of the game |
| `cover` | no | Relative path to cover image |
| `title_ids` | yes | Array of Wii U Title IDs (all regions) |
| `mods` | yes | Array of mod objects |

## Mod fields

| Field | Required | Description |
|-------|----------|-------------|
| `id` | yes | Unique identifier (no spaces) |
| `name` | yes | Display name |
| `type` | yes | `mod` or `modpack` |
| `version` | yes | Semantic version string |
| `author` | yes | Author name |
| `description` | yes | Description text |
| `thumbnail` | no | URL to thumbnail image (400x225 recommended) |
| `screenshots` | no | Array of screenshot URLs |
| `download` | yes | Direct URL to ZIP file |
| `modpack_path` | yes | SDCafiine path (`content/` or `aoc/`) |
| `includes` | modpack only | Array of mod IDs included in bundle |

## Notes

- Title IDs can be found at [wiiubrew.org/wiki/Title_database](https://wiiubrew.org/wiki/Title_database)
- Mod ZIPs must match the SDCafiine folder structure (`content/` at root of ZIP)
- The app does **not** verify mod safety! only distribute mods you trust
