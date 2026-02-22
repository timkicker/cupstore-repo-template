# CupStore Repo Template

This is the official template for hosting mods on [CupStore](https://github.com/timkicker/cupstore) - a mod manager for the Wii U.

## Quick Start

1. Fork this repository
2. Edit `repo.json` (name, author)
3. Add your game folders under `games/`
4. Add your mod ZIPs as GitHub Release assets
5. Share your `repo.json` URL with users

## Structure

```
repo.json                        ← repo index
games/
  mario-kart-8/
    game.json                    ← game + mod definitions
  your-game/
    game.json
```

## repo.json

```json
{
  "formatVersion": 1,
  "name": "My Mod Repo",
  "description": "...",
  "author": "your-name",
  "version": "1",
  "games": [
    { "path": "games/mario-kart-8/game.json" }
  ]
}
```

## game.json

```json
{
  "name": "Mario Kart 8",
  "icon": "https://...",
  "titleIds": [
    "000500001010EB00",
    "000500001010EC00",
    "000500001010ED00"
  ],
  "mods": [ ... ]
}
```

## Mod Fields

| Field | Required | Description |
|-------|----------|-------------|
| `id` | ✅ | Unique ID, only `a-z 0-9 - _` |
| `name` | ✅ | Display name |
| `author` | ✅ | Author name |
| `version` | ✅ | Version string e.g. `1.0.0` |
| `description` | ✅ | Short description |
| `download` | ✅ | Direct URL to `.zip` file |
| `type` | ✅ | `"mod"` or `"modpack"` |
| `thumbnail` | ☑️ | Preview image URL (400x225) |
| `screenshots` | ☑️ | List of screenshot URLs (800x450) |
| `includes` | ☑️ | For modpacks: list of mod IDs |
| `releaseDate` | ☑️ | e.g. `"2024-03-15"` |
| `license` | ☑️ | e.g. `"CC BY-NC"` |
| `tags` | ☑️ | e.g. `["skin", "music", "course"]` |
| `fileSize` | ☑️ | ZIP size in bytes |
| `requirements` | ☑️ | List of required mods/patches |
| `changelog` | ☑️ | Free text changelog |

## Validation

```bash
python3 validate.py              # check structure
python3 validate.py --check-urls # also verify download URLs
```

Validation runs automatically on every PR via GitHub Actions.

## Mod ZIP Structure

Your ZIP must extract to a folder matching the SDCafiine layout:

```
your-mod.zip
└── content/
    └── ...game files...
```

CupStore installs to: `SD:/wiiu/sdcafiine/<titleId>/<modId>/`
