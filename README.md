# CosmicEnchantsBE

**CosmicPvP-style Cosmic Enchants** for **Minecraft Bedrock Edition** (including **Realms**).

> Realms cannot run Java/Spigot plugins. This project is a **behavior pack + resource pack** (`.mcaddon`) using the Bedrock **Script API**.

**Current version:** `1.4.13`  
**Release file:** [`releases/CosmicEnchantsBE_v1.4.13.mcaddon`](releases/CosmicEnchantsBE_v1.4.13.mcaddon)

---

## Features

| Feature | Status |
|--------|--------|
| 150+ Cosmic-named enchants (Simple → Mastery) | ✅ |
| Combat / mining / armor passives | ✅ |
| Cosmic books + GUI apply (no drag-drop) | ✅ |
| White Scroll (protect gear) | ✅ all tools & armor |
| Black Scroll (extract → book, 90%) | ✅ gear never breaks |
| Mystery Dust (+1% success, cap +50%) | ✅ |
| XP level shop | ✅ |
| Max **9** Cosmic enchants per item | ✅ full pieces hidden from apply |
| Admin maxkit | ✅ |

---

## Install

### Quick (players)
1. Download **`CosmicEnchantsBE_v1.4.13.mcaddon`** from [Releases](../../releases) or the `releases/` folder.
2. Double-click to import, **or** open with Minecraft.
3. World settings → enable **Behavior Pack** + **Resource Pack**.
4. Enable **Beta APIs** / experiments if prompted.
5. Join → you should see `v1.4.13 Ready`.

### Realms
1. Apply both packs to the world (or upload via Realms pack UI).
2. Fully leave and rejoin after updates.

### Admin free shop / kits
```mcfunction
/tag @s add ce_admin
```

---

## Commands

All of these hit the same handler:

- Slash: `/ce:shop`
- Script: `/scriptevent ce:shop`
- Function: `/function ce/shop`
- Chat: `!ce shop` · `.ce shop` · `ce shop`

### Player

| Command | Action |
|---------|--------|
| `/ce:menu` | Main menu |
| `/ce:help` | Help |
| `/ce:shop` | XP shop GUI |
| `/ce:shop <tier>` | Buy 1 random book (`simple` … `mastery`) |
| `/ce:shop_simple` … `/ce:shop_mastery` | Tier shortcuts |
| `/ce:prices` | Shop prices |
| `/ce:list [tier]` | List enchants |
| `/ce:enchants` | Enchant count |
| `/ce:info` / `/ce:inspect` | Inspect held item |
| `/ce:apply` | Apply flow |
| `/ce:combine` / `/ce:use` | GUI for held scroll/dust/book |
| `/ce:white` / `/ce:black` / `/ce:dust` | Utility apply menus |

### Admin (Game Directors / `ce_admin`)

| Command | Action |
|---------|--------|
| `/ce:give <enchant> [level]` | Give Cosmic book |
| `/ce:enchant <enchant> [level]` | Force-apply to held gear |
| `/ce:maxkit` | Full netherite kit + max enchants |
| `/ce:godkit` / `/ce:netheritekit` / `/ce:fullkit` | maxkit aliases |

### Player flow (no commands needed after shop)

1. Buy in **`/ce:shop`** (XP levels, or free with Creative / `ce_admin`).
2. Hold **paper** (White), **ink sac** (Black), **glowstone dust** (Dust), or **Cosmic book**.
3. **Right-click** (or sneak ~1s) → pick target from the list.

| Item | Vanilla | Use |
|------|---------|-----|
| White Scroll | Paper | Protect gear from destroy-on-fail |
| Black Scroll | Ink sac | Extract random enchant → book (90%) |
| Mystery Dust | Glowstone dust | +1% book success (max +50%) |
| Cosmic Book | Enchanted book | Apply to compatible gear |

**Rules of note**
- Max **9** Cosmic enchants per piece (full pieces not listed for new enchants).
- Black Scroll never breaks gear; extract books have **100% destroy** on apply fail.
- White Scroll works on all armor/tools (including netherite).

---

## Build (developers)

```powershell
cd path\to\CosmicEnchantsBE

# Package release .mcaddon → dist/ + releases/
powershell -ExecutionPolicy Bypass -File tools\package.ps1
```

Outputs:
- `dist/CosmicEnchantsBE.mcaddon` (latest)
- `dist/CosmicEnchantsBE_vX.Y.Z.mcaddon`
- `releases/CosmicEnchantsBE_vX.Y.Z.mcaddon` ← upload to GitHub Releases

Offline tests (optional, requires Node):

```powershell
node tools\test_player_flows.mjs
node tools\test_full_suite.mjs
```

---

## Project layout

```
CosmicEnchantsBE/
  packs/BP/                 # Behavior pack (scripts, functions)
  packs/RP/                 # Resource pack (icon, texts)
  tools/package.ps1         # Build .mcaddon
  tools/test_*.mjs          # Offline rule tests
  releases/                 # Versioned release artifacts
  dist/                     # Build output
  CHANGELOG.md
  LICENSE
```

---

## Compatibility

- Minecraft Bedrock **1.21+** (Script API `@minecraft/server` / `server-ui`)
- Windows Bedrock, Realms, BDS with packs enabled
- **Not** for Java Edition

---

## License & disclaimer

MIT — see [LICENSE](LICENSE).

Fan-made interoperability port for personal/server use. CosmicPvP / plugin brand names belong to their owners. **Not affiliated** with Mojang, Microsoft, CosmicPvP, or AdvancedPlugins.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md).
