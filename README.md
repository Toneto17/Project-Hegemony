# Project Hegemony

A single-file browser strategy game blending the resource economy of Catan with the territorial combat of Risk — played on hex grids with dice-driven mechanics, tech upgrades, and AI opponents.

**Play it:** [https://toneto17.github.io/Project-Hegemony/](https://toneto17.github.io/Project-Hegemony/)

---

## Gameplay

### Objective
Reach **14 Dominance Points (DP)** before your opponents. DP comes from:
- Holding settlements and walled cities
- Controlling metropolis hexes
- Researching technologies

### Turn Phases
1. **Harvest** — Roll 2 dice; every hex you own with a matching number produces its resource
2. **Upkeep** — Pay 1 📦 Logistics per 3 armies (armies disband if you can't pay)
3. **Actions** — Move armies, attack, recruit, build, research
4. **End Turn** — Advance to next player

### Resources
| Icon | Resource | Produced by |
|------|----------|-------------|
| 📦 | Logistics | Plains |
| ⚙️ | Industry | Mountains |
| 💡 | Knowledge | Forests |

### Actions (Phase 3)
- **Move / Attack** — Move armies to adjacent hexes. Attacking costs 1 move token; reinforcing your own territory is always free
- **Recruit** — Spend 📦 Logistics to add armies to your capital or any settlement
- **Build** — Spend resources to upgrade settlements or build walls
- **Research** — Spend 💡 Knowledge to unlock technologies

### Combat
Both sides roll dice simultaneously. Attacker rolls up to 3 dice (4 with Grand Army upgrade); defender rolls up to 2 (3 if walled). Highest dice are compared pair by pair — ties go to the defender. Both sides can spend 📦1 to reroll a die; defender can spend ⚙️2 to cancel a loss.

---

## Maps

| Map | Size | Description |
|-----|------|-------------|
| Classic | Medium (37 hexes) | Standard hex ring |
| Continents | Medium (37 hexes) | Two landmasses separated by a strait |
| Islands | Medium (37 hexes) | Archipelago with bridge connections |
| Ring | Medium (37 hexes) | Hollow centre — control the outer ring |
| Europa | Large (61 hexes) | Europe-inspired geography with bridges |
| World | Large (61 hexes) | World map with continents and bridges |
| Skirmish | Small (19 hexes) | Fast 2-player duel |
| Labyrinth | Large (61 hexes) | Narrow winding corridors |

---

## Technologies

| Tech | Cost | Effect |
|------|------|--------|
| Logistics Network | 📦3 | +1 army per settlement on harvest |
| Iron Forges | ⚙️3 | Recruit costs 1 less Logistics |
| Grand Army | 💡3 | Roll up to 4 attack dice, 2 attacks per turn |
| Fortification | ⚙️4 | All your settlements count as walled |
| Economic Dominance | 📦4 💡2 | +2 DP (instant win condition accelerator) |

---

## Game Modes

### Quick Play
No login required. Choose players (2–4), mode, map, and launch.

### VS AI
Play against AI opponents with three difficulty levels: Easy, Normal, Hard.

### Campaign
10 linked story missions of increasing difficulty, each on a specific map. Requires a commander profile. Completing missions awards XP and unlocks further missions.

### Hot Seat
Multiple human players on the same screen, passing the device each turn.

### Multiplayer (Online)
Real-time play across different devices using WebRTC (PeerJS). One player creates a room and shares the 5-character code; others join from any browser on any device or network.

---

## Commander Profiles

Profiles are **stored locally in your browser** — no server, no email, no account required. Password is optional (useful on shared devices). Your profile holds:
- XP and commander level
- Match history and stats
- Campaign progress

---

## Running Locally

The game is a single HTML file with no build step.

```bash
# Option 1 — Python (built-in)
python -m http.server 8080
# Open http://localhost:8080/project-hegemony\ \(30\).html

# Option 2 — Node.js
npx serve .
```

Or just open the file directly in a browser (some features like clipboard copy work better over HTTP).

---

## Architecture

| Concern | Approach |
|---------|----------|
| Rendering | HTML5 Canvas 2D with HiDPI support |
| Hex grid | Axial coordinates (q, r, s), BFS pathfinding |
| Map generation | Seeded RNG, per-map layout functions |
| AI | Heuristic scoring with difficulty multipliers |
| Auth | localStorage accounts, PBKDF2-SHA256 password hashing, sessionStorage sessions (per-tab) |
| Multiplayer | PeerJS WebRTC data channels via public signaling server |
| Sound | Web Audio API (SFX only) |

Everything lives in a single `project-hegemony (30).html` file (~6 000 lines).

---

## License

MIT — do whatever you want with it.
