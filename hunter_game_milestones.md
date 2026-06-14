# 🎯 Hunter Game — Milestones & Tasks (55-Day Sprint)

> **What is this document?**
> This is the fast-reference version of the full development plan. It lists every phase, milestone, and task in order — without the long explanations. Use this as your daily checklist. Tick off tasks as you complete them.
>
> For deeper explanations of *why* each task exists and *how* to approach it, refer to the full Dev Plan document.

---

## 📅 Phase Overview

| Phase | Days | What You're Building |
|---|---|---|
| 1 | 1–7 | Project setup, map, version control |
| 2 | 8–18 | Gun, Net, Reload, Timer, Win Conditions |
| 3 | 19–28 | Stamina, Distortion Threshold, Digging |
| 4 | 29–37 | Shadow Vision, 6-Line Radio, Proximity |
| 5 | 38–44 | Table Lobby, Betrayal, Economy |
| 6 | 45–50 | Multiplayer networking, Voice Chat |
| 7 | 51–53 | AI bots (fill disconnected player slots) |
| 8 | 54–55 | Bug fixes, balance, audio, art pass |

---

---

## PHASE 1 — Setup & Foundation *(Days 1–7)*

> Get the project running, build a basic test map, and set up your save/backup system. Nothing fancy — just the workspace ready to build in.

---

### Milestone 1.1 — Dev Environment Ready *(Day 2)*
- [x] Install Unity (LTS version)
- [x] Create a new Unity 2D project: `HunterGame`
- [x] Install Git and create GitHub account
- [x] Initialize Git repo and push first commit
- [x] Install VS Code with the Unity editor package (or use Rider / Visual Studio)
- [x] Create folder structure: `/Scenes`, `/Scripts`, `/Assets/Art`, `/Assets/Audio`

---

### Milestone 1.2 — Basic Map & Camera *(Day 5)*
- [x] Build a basic top-down test arena using Tilemap (walls, corridors, open areas)
- [x] Add Cinemachine Virtual Camera that follows the player
- [ ] Constrain camera to map bounds
- [x] Add placeholder sprites for Hunter (red box) and Prey (blue box)
- [x] Confirm WASD movement works

---

### Milestone 1.3 — Version Control Habits *(Day 7)*
- [x] Commit to GitHub daily with clear commit messages
- [ ] Set up Trello board: `To Do` / `In Progress` / `Done`
- [ ] Add all tasks from this document to Trello

---

---

## PHASE 2 — Core Gameplay Prototype *(Days 8–18)*

> Build the fundamental loop: Hunter hunts, Prey evade, the gun fires, the reload window opens, the net can close it. Three win conditions. By end of this phase you can "play" a rough version of the game.

---

### Milestone 2.1 — Player Roles & Spawning *(Day 10)*
- [ ] Create `Hunter` and `Prey` prefabs
- [ ] Each prefab: sprite + Collider2D + movement script
- [ ] `GameManager` script assigns 1 Hunter and up to 6 Prey
- [ ] Spawn points: Hunter in center, Prey around edges
- [ ] Confirm correct spawning at game start

---

### Milestone 2.2 — Gun & Reload Mechanic *(Day 13)*
- [ ] Hunter fires on left-click in mouse direction
- [ ] Use `Physics2D.Raycast` for line-of-sight check (walls block shots)
- [ ] Hit Prey = Prey eliminated from scene
- [ ] After shot: `reloading = true` for 3 seconds, cannot fire
- [ ] Show reload progress bar above Hunter's head
- [ ] Test: fire → defenseless 3 sec → can fire again

---

### Milestone 2.3 — Net & Prey Attack *(Day 15)*
- [ ] Prey throws net with right-click or `F`
- [ ] Net creates a small collision zone in front of Prey
- [ ] `IF net zone hits Hunter AND reloading = true` → Hunter eliminated → Prey win
- [ ] `IF net zone hits another Prey` → betrayal (Phase 5 will finish this)
- [ ] Net cooldown: 2 seconds between uses
- [ ] Prey cannot net Hunter when Hunter is not reloading — attempt does nothing

---

### Milestone 2.4 — Match Timer & Win Conditions *(Day 18)*
- [ ] Visible countdown timer on screen (5 minutes)
- [ ] `check_win_conditions()` runs every second:
  - All 6 Prey eliminated → Hunter Wins
  - Timer hits zero + 1+ Prey alive → Prey Win
  - Hunter netted during reload → Prey Win
- [ ] Show `"Hunter Wins"` / `"Prey Win"` end screen
- [ ] Restart button reloads the scene
- [ ] Test all three win conditions manually

---

---

## PHASE 3 — Movement Systems *(Days 19–28)*

> Add the Distortion Threshold (running too fast causes you to phase through walls, then players, then vanish) and the underground digging mechanic. These are what make the Hunter Game unique.

---

### Milestone 3.1 — Basic Movement & Stamina Bar *(Day 20)*
- [ ] Add `speed` and `stamina` variables to Hunter and Prey scripts
- [ ] `Shift` + move = sprinting; drains stamina faster
- [ ] Stamina slowly recharges when not sprinting
- [ ] Hunter: small bar, recharges fast
- [ ] Prey: large bar, recharges slowly
- [ ] Display stamina bar above each player (green → yellow → red)

---

### Milestone 3.2 — Distortion Threshold System *(Day 24)*
- [ ] `distortion_level` variable: 0 (Normal), 1 (Phase Objects), 2 (Phase Players), 3 (Vanish)
- [ ] Distortion level rises with sustained sprinting / stamina depletion
- [ ] **Level 0 — Normal:** standard movement, minor screen blur
- [ ] **Level 1 — Phase Objects:** passes through walls; Prey cannot fire Net in this state
- [ ] **Level 2 — Phase Players:** passes through players too; no targeting in or out
- [ ] **Level 3 — Vanish (Prey only):** player is eliminated; show `"[Name] ran too fast and vanished!"`
- [ ] **Hunter cap:** Hunter distortion can never exceed Level 1
- [ ] Show current distortion level as on-screen text label

---

### Milestone 3.3 — Underground Digging *(Day 28)*
- [ ] Press `E` to go underground
- [ ] While underground: hidden from line-of-sight, cannot be targeted by Gun or Net
- [ ] Underground movement speed = 50% of normal
- [ ] Dig stamina bar depletes while underground
- [ ] Auto-resurface when dig stamina hits zero
- [ ] Press `E` again to manually resurface early
- [ ] Add dust/dirt visual effect on entry and exit
- [ ] Test: shots pass through a digging Prey

---

---

## PHASE 4 — Shadow Vision & Radio System *(Days 29–37)*

> Players only see what's in their line of sight (walls block vision). Prey coordinate via a 6-line radio that degrades as they die. More deaths = more static = harder to communicate.

---

### Milestone 4.1 — Shadow Vision *(Day 32)*
- [ ] Add `LightOccluder2D` to all walls in the Tilemap
- [ ] Attach `PointLight2D` to each player (represents their vision cone)
- [ ] Areas outside the player's light appear dark
- [ ] Other players/objects only visible if inside lit area
- [ ] Test: walk behind wall → cannot see players on other side

---

### Milestone 4.2 — 6-Line Radio System *(Day 35)*
- [ ] Create `RadioManager` Singleton MonoBehaviour
- [ ] Track 6 radio lines — one per Prey
- [ ] Prey press `1`–`6` to switch which line they transmit on
- [ ] UI panel shows each line: green (active) / grey (dead)
- [ ] **Line Death:** when Prey is eliminated, their line goes offline
- [ ] **Clarity Degradation UI:**
  - 6 lines: clear
  - 4 lines: static overlay
  - 2 lines: heavy distortion indicators
  - 0 lines: silence
- [ ] **Hunter Interception:** press `R` near dead Prey's position → see their last message
- [ ] **Sabotage:** press `Q` near dead Prey → adds distortion to all remaining lines

---

### Milestone 4.3 — Proximity Chat System *(Day 37)*
- [ ] Write `ProximityDetector` script
- [ ] Every 0.5 seconds: check distance between all players
- [ ] If within radius → flag as "in proximity"
- [ ] Show UI indicator: `"[PlayerName] is nearby"`
- [ ] System ready to connect to real voice chat in Phase 6

---

---

## PHASE 5 — Lobby, Betrayal & Economy *(Days 38–44)*

> The pregame Table Lobby where all 7 players negotiate stakes. The prize pool. The Prey-on-Prey betrayal system. And the post-match currency distribution.

---

### Milestone 5.1 — Table Lobby *(Day 40)*
- [ ] Create `TableLobby Scene` — top-down view of table with 7 seats
- [ ] Show each player's name and "Ready" indicator at their seat
- [ ] Display live prize pool total in center of table
- [ ] Host sets minimum stake (text input or slider)
- [ ] Each player has `+10`, `+50`, `+100` buttons to add personal stake
- [ ] All 7 players confirm → countdown: `"Match Starting in 5..."`
- [ ] Transition to game map when countdown ends

---

### Milestone 5.2 — Betrayal Mechanic *(Day 42)*
- [ ] Net can now also target other Prey (not only the Hunter)
- [ ] `IF net hits a Prey AND that Prey is not the player` → sacrifice that Prey
- [ ] Sacrificed Prey: removed from match; their prize stake transferred to betrayer
- [ ] Show: `"[A] was betrayed by [B]!"`
- [ ] Betrayed Prey's radio line goes offline
- [ ] Test the risk: betrayer must be very close → exposed to Hunter and other Prey

---

### Milestone 5.3 — Economy & Prize Distribution *(Day 44)*
- [ ] `PlayerWallet` script tracks each player's balance
- [ ] Display balance in lobby and in-game HUD
- [ ] At match start: deduct stake from wallet, add to `prize_pool`
- [ ] Distribution:
  - Hunter wins → Hunter gets full `prize_pool`
  - Prey win → surviving Prey split `prize_pool` equally (sacrificed Prey already forfeited their share to their betrayer)
- [ ] Post-match results screen: who won, how much, final balance
- [ ] New accounts start with 1,000 coins

---

---

## PHASE 6 — Multiplayer Integration *(Days 45–50)*

> Connect everything over the internet so 7 real players can play together. Technically the most complex phase — take it one step at a time.

---

### Milestone 6.1 — Basic Networked Connection *(Day 46)*
- [ ] Watch a "Unity multiplayer tutorial" (minimum 1 hour of learning)
- [ ] Implement Host / Join system (host creates server, joiner enters IP)
- [ ] Sync player positions using `NetworkTransform`
- [ ] Test: 2 players move around the same map in real time on different computers
- [ ] Show player name labels above each character

---

### Milestone 6.2 — Full 1v6 Networking *(Day 48)*
- [ ] Scale to 7 players (1 Hunter + 6 Prey)
- [ ] Sync over network:
  - Player positions and rotation
  - Hunter reload state
  - Stamina / distortion level
  - Underground status
  - Prize pool
  - Match timer
- [ ] Handle disconnect gracefully (remove or replace with AI bot)
- [ ] Test with 3+ real players on different machines

---

### Milestone 6.3 — Voice Chat Integration *(Day 50)*
- [ ] Decide approach: Discord GameSDK integration OR document "use Discord alongside game"
- [ ] If integrating: connect `ProximityDetector` to voice volume (distance = volume)
- [ ] Connect `RadioManager` to push-to-talk channels
- [ ] Test proximity chat (nearby players can hear each other)
- [ ] Test radio channels (Prey can switch and broadcast)

---

---

## PHASE 7 — AI System *(Days 51–53)*

> A basic AI bot that fills the slot of any player who disconnects mid-match. Simple enough to build in 3 days, believable enough to keep the match playable.

---

### Milestone 7.1 — Basic Prey Bot *(Day 52)*
- [ ] Create `PreyBot` script
- [ ] Bot behavior states:
  - Hunter reloading + bot close enough → move toward Hunter and net
  - Hunter has gun ready + bot in line-of-sight → run away from Hunter
  - Hunter cannot see bot → wander map randomly
  - Hunter approaching → dig underground
- [ ] Bot uses same stamina/distortion system as human players
- [ ] Bots do NOT betray other Prey (too complex — future update)

---

### Milestone 7.2 — Bot Activation on Disconnect *(Day 53)*
- [ ] Detect player disconnect signal
- [ ] Spawn `PreyBot` at disconnected player's last position
- [ ] Bot inherits that player's radio line and stake
- [ ] Show: `"[PlayerName] disconnected — replaced by AI"`

---

---

## PHASE 8 — Testing & Polish *(Days 54–55)*

> Play the game. Break the game. Fix the worst problems. Add basic sound and simple sprites. Ship a playable closed-testing build.

---

### Milestone 8.1 — Bug Hunt & Balance *(Day 54)*
- [ ] Play 10+ complete matches with real players
- [ ] Fix all crashes and game-breaking bugs first
- [ ] Adjust these values from playtesting feedback:
  - [ ] Hunter reload time
  - [ ] Match timer length
  - [ ] Stamina drain/recharge rates
  - [ ] Distortion threshold timing
  - [ ] Dig stamina duration
- [ ] Fix networking desyncs (players seeing wrong positions)
- [ ] Verify all 3 win conditions trigger correctly 100% of the time

---

### Milestone 8.2 — UI & Audio Pass *(Day 55)*
- [ ] Replace placeholder boxes with simple pixel-art sprites (Hunter and Prey)
- [ ] Add sound effects:
  - [ ] Gunshot
  - [ ] Net throw
  - [ ] Reload (mechanical click)
  - [ ] Underground dig
  - [ ] Betrayal sting
  - [ ] Match win / match lose jingle
- [ ] All UI readable and clearly labelled
- [ ] Add main menu: `Play`, `Host`, `Join`, `Quit`
- [ ] Add credits screen

---

---

## ✅ Total Milestone Count: 16 Milestones across 8 Phases

| # | Milestone | Phase | Day Target |
|---|---|---|---|
| 1.1 | Dev Environment Ready | Setup | Day 2 |
| 1.2 | Basic Map & Camera | Setup | Day 5 |
| 1.3 | Version Control Habits | Setup | Day 7 |
| 2.1 | Player Roles & Spawning | Core Prototype | Day 10 |
| 2.2 | Gun & Reload Mechanic | Core Prototype | Day 13 |
| 2.3 | Net & Prey Attack | Core Prototype | Day 15 |
| 2.4 | Match Timer & Win Conditions | Core Prototype | Day 18 |
| 3.1 | Basic Movement & Stamina | Movement | Day 20 |
| 3.2 | Distortion Threshold | Movement | Day 24 |
| 3.3 | Underground Digging | Movement | Day 28 |
| 4.1 | Shadow Vision | Radio & Vision | Day 32 |
| 4.2 | 6-Line Radio System | Radio & Vision | Day 35 |
| 4.3 | Proximity Chat Placeholder | Radio & Vision | Day 37 |
| 5.1 | Table Lobby | Lobby & Economy | Day 40 |
| 5.2 | Betrayal Mechanic | Lobby & Economy | Day 42 |
| 5.3 | Economy & Prize Distribution | Lobby & Economy | Day 44 |
| 6.1 | Basic Networked Connection | Multiplayer | Day 46 |
| 6.2 | Full 1v6 Networking | Multiplayer | Day 48 |
| 6.3 | Voice Chat Integration | Multiplayer | Day 50 |
| 7.1 | Basic Prey Bot | AI | Day 52 |
| 7.2 | Bot Activation on Disconnect | AI | Day 53 |
| 8.1 | Bug Hunt & Balance | Polish | Day 54 |
| 8.2 | UI & Audio Pass | Polish | Day 55 |

---

*Condensed reference document — for full explanations and tool recommendations, see the full Dev Plan.*
*Timeline: 55 Days | Hunter Game Prototype — Closed Testing Build*
