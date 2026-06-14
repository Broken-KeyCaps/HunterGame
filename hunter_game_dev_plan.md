# 🎮 Hunter Game — Full Development Plan (55 Days)

> **What is this document?**
> This is a step-by-step development plan for the Hunter Game — a 1v6 asymmetrical multiplayer game. It breaks down everything that needs to be built into phases, milestones, and daily tasks. Think of it as a recipe book: each phase is a chapter, each milestone is a dish, and each task is a step in the recipe.

---

## 📋 Quick Overview

| Field | Details |
|---|---|
| Game Type | 2D Top-Down Asymmetrical Multiplayer |
| Players | 1 Hunter vs 6 Prey |
| Total Dev Time | 55 Days |
| Target Platform | PC (Primary) |
| Engine | **Unity** (free Personal tier, industry-standard, strong 2D support) |
| Language | **C#** (Unity's primary scripting language) |

---

## 🛠️ Recommended Tools (Beginner-Friendly)

> **What is a "tool"?**
> Tools are software programs that help you build different parts of the game. Just like a carpenter uses different tools for different jobs, game developers use different programs for different tasks.

### Game Engine
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Unity** | Free, open-source, excellent 2D support, easy to learn, built-in networking | [unity.com/download](https://unity.com/download) |

### Code Editor
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **VS Code** | Free, lightweight, works with Unity via the Visual Studio Code editor package | [code.visualstudio.com](https://code.visualstudio.com) |
| **Unity Editor** | Built-in, comes with Unity | Included with Unity |

### Art & Graphics
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Aseprite** | Industry-standard pixel art tool, great for 2D game sprites | [aseprite.org](https://www.aseprite.org) |
| **Krita** | Free alternative to Photoshop for drawing sprites and tiles | [krita.org](https://krita.org) |
| **Piskel** | Free, browser-based pixel art tool — perfect for beginners | [piskelapp.com](https://www.piskelapp.com) |

### Audio
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Audacity** | Free audio editor for recording and editing sound effects | [audacityteam.org](https://www.audacityteam.org) |
| **BFXR / sfxr** | Free tool that auto-generates retro sound effects | [bfxr.net](https://www.bfxr.net) |
| **OpenGameArt.org** | Free audio and art assets under open licenses | [opengameart.org](https://opengameart.org) |

### Networking (Multiplayer)
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Unity Netcode for GameObjects** | Unity's official networking solution for multiplayer | Included with Unity |
| **Nakama (optional)** | Open-source game server for matchmaking and lobbies | [heroiclabs.com/nakama](https://heroiclabs.com/nakama) |

### Version Control (Saving Your Work)
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Git** | Tracks every change you make — like a time machine for your code | [git-scm.com](https://git-scm.com) |
| **GitHub** | Free cloud storage for your Git project, easy to collaborate | [github.com](https://github.com) |
| **GitHub Desktop** | A visual app so you don't need to type Git commands | [desktop.github.com](https://desktop.github.com) |

### Project Management
| Tool | Why Use It | Where to Get It |
|---|---|---|
| **Trello** | Free visual board for tracking tasks (drag cards between "To Do", "Doing", "Done") | [trello.com](https://trello.com) |
| **Notion** | Free all-in-one notes + task tracker | [notion.so](https://notion.so) |

---

## 📅 55-Day Master Timeline

```
Days 1–7   → Phase 1: Setup & Foundation
Days 8–18  → Phase 2: Core Gameplay Prototype
Days 19–28 → Phase 3: Movement Systems
Days 29–37 → Phase 4: Communication & Radio
Days 38–44 → Phase 5: Lobby & Economy
Days 45–50 → Phase 6: Multiplayer Integration
Days 51–53 → Phase 7: AI System
Days 54–55 → Phase 8: Closed Testing & Polish
```

---

---

## PHASE 1 — Setup & Foundation
### ⏱️ Days 1–7 | 7 Days

> **What is this phase?**
> Before you build a house, you clear the land and lay the foundation. This phase is about setting up your development environment, creating your project structure, and prototyping the very basics of the game map and player movement. Nothing fancy yet — just making sure everything works.

---

### 🏁 Milestone 1.1 — Dev Environment Ready
**Target: End of Day 2**

> **What does "dev environment" mean?**
> It means all the software you need to make the game is installed, configured, and working together. Like setting up your kitchen before you cook.

#### Tasks:
- [ ] Download and install **Unity**
- [ ] Create a new Unity 2D project called `HunterGame`
- [ ] Install **Git** and create a GitHub account
- [ ] Initialize a Git repository in your project folder
- [ ] Make your first commit (save your empty project to GitHub)
- [ ] Install **VS Code** with the Unity support via Rider or Visual Studio (optional but helpful)
- [ ] Create a simple folder structure inside the Unity project:
  ```
  /Scenes       ← game Scenes and levels
  /scripts      ← all C# code files
  /Assets       ← art, audio, fonts
  /Assets/Art
  /Assets/Audio
  ```

**Tools Used:** Unity, Git, GitHub, VS Code

---

### 🏁 Milestone 1.2 — Basic Map & Camera
**Target: End of Day 5**

> **What is a tilemap?**
> A tilemap is like a grid of small picture tiles that together make up your game world — like a mosaic or Lego floor.

> **What is a camera?**
> In a game, the "camera" is the virtual eye that follows your player. It controls what part of the world you see on screen.

#### Tasks:
- [ ] Create a basic 2D top-down map using Unity's **Tilemap** system
- [ ] Design a simple test arena (walls, open areas, corridors) — doesn't need to look good yet
- [ ] Add a **Cinemachine Virtual Camera** node that follows the player
- [ ] Set the camera so it stays within the bounds of the map
- [ ] Add placeholder rectangles for the Hunter and Prey (colored squares are fine)
- [ ] Confirm: player rectangle moves with WASD/arrow keys

**Tools Used:** Unity (Tilemap, Cinemachine Virtual Camera), Aseprite or Piskel (for simple tile art)

---

### 🏁 Milestone 1.3 — Version Control Habits
**Target: End of Day 7**

> **Why is this a milestone?**
> Version control (Git) is your safety net. If you break something, you can go back. Getting into the habit of committing (saving) your work daily is one of the most important skills in development.

#### Tasks:
- [ ] Commit your project to GitHub every single day from now on
- [ ] Write clear commit messages (e.g., `"Added basic player movement"`, `"Fixed camera bounds"`)
- [ ] Set up a **Trello board** with three columns: `To Do`, `In Progress`, `Done`
- [ ] Add all tasks from this document to Trello

**Tools Used:** Git, GitHub, GitHub Desktop, Trello

---

---

## PHASE 2 — Core Gameplay Prototype
### ⏱️ Days 8–18 | 11 Days

> **What is this phase?**
> This is where the game starts to feel like a game. You'll build the two core roles (Hunter and Prey), the Gun and Net mechanics, the timer, the reload vulnerability window, and the basic win/lose conditions. By the end, you should be able to "play" a very rough version of the game — just you and placeholder graphics.

---

### 🏁 Milestone 2.1 — Player Roles & Spawning
**Target: End of Day 10**

> **What is spawning?**
> Spawning means placing a player character into the game world at the start of a match. Like dropping a piece onto a board game.

#### Tasks:
- [ ] Create two separate **Player prefabs** in Unity: `Hunter` and `Prey`
- [ ] Each Scene has: a sprite (colored box for now), a collision shape, and a movement script
- [ ] Write a `GameManager` script that:
  - Assigns one player as the Hunter (red)
  - Assigns up to six players as Prey (blue)
- [ ] Place spawn points on the map (Hunter spawns in center, Prey spawn around the edges)
- [ ] Confirm: Hunter and Prey spawn at the correct positions at game start

**Tools Used:** Unity (GameObjects, Components, C#)

---

### 🏁 Milestone 2.2 — The Gun & Reload Mechanic
**Target: End of Day 13**

> **What is line-of-sight?**
> Line-of-sight means the Hunter can only shoot a Prey if there's a clear, unobstructed path between them — no walls in the way. Like shining a flashlight: if a wall blocks the beam, the Prey is safe.

> **What is a reload window?**
> After the Hunter fires, they must wait a few seconds before they can fire again. During that window, they cannot defend themselves. This is the MOST important mechanic in the game.

#### Tasks:
- [ ] Add a **Gun** to the Hunter:
  - Left-click fires a projectile (or instant raycast) in the direction the mouse points
  - The projectile travels in a straight line
  - If it hits a Prey: Prey is eliminated (removed from the Scene)
- [ ] Implement **Line-of-Sight check**:
  - Use Unity's `Physics2D.Raycast` method
  - The shot only registers if no wall is between Hunter and Prey
- [ ] Implement **Reload Phase**:
  - After shooting, Hunter enters a `reloading = true` state for 3 seconds (adjustable)
  - During reload: Hunter cannot fire
  - Visual indicator: show a reload progress bar above Hunter's head
- [ ] Add a simple **reload animation** (flashing red outline or countdown timer on screen)
- [ ] Test: Fire gun → Hunter is defenseless for 3 seconds → can fire again

**Tools Used:** Unity (Physics2D.Raycast, Coroutine / InvokeRepeating, Animator / Animation component), Piskel/Aseprite (for visual indicator art)

---

### 🏁 Milestone 2.3 — The Net & Prey Attack
**Target: End of Day 15**

> **What is close-range/melee?**
> The Net can only be used when a Prey is physically very close to the target — like a punch in range. Unlike the Gun, you can't use it from across the map.

#### Tasks:
- [ ] Add a **Net** to each Prey:
  - Right-click or press `F` to throw the Net
  - Create a small collision area in front of the Prey (the "net zone")
  - If the net zone overlaps with the Hunter AND `reloading = true`: Hunter is eliminated → Prey win
  - If the net zone overlaps with another Prey (betrayal — covered in Phase 5): that Prey is eliminated
- [ ] Add a **Net cooldown** (e.g., 2 seconds between uses)
- [ ] Show a visual when the net is thrown (simple white rectangle flying forward)
- [ ] Test: Prey cannot net Hunter when Hunter is not reloading → attempt does nothing

**Tools Used:** Unity (Collider2D + trigger zone, Timer for cooldown)

---

### 🏁 Milestone 2.4 — Match Timer & Win Conditions
**Target: End of Day 18**

> **What is the win condition?**
> The specific thing that must happen for someone to win. A win condition check runs every frame (60 times per second) and ends the match the moment it's met.

#### Tasks:
- [ ] Add a **visible countdown timer** on screen (e.g., 5 minutes, displayed top-center)
- [ ] Write a `check_win_conditions()` function that runs every second:
  ```
  IF all Prey are eliminated → Hunter Wins
  IF timer hits zero AND at least 1 Prey alive → Prey Win
  IF Hunter is netted during reload → Prey Win
  ```
- [ ] Show a simple **"Hunter Wins" / "Prey Win"** screen when the match ends
- [ ] Add a **Restart button** that reloads the Scene back to the beginning
- [ ] Test all three win conditions manually

**Tools Used:** Unity (Coroutine / InvokeRepeating, TextMeshPro component for UI, SceneTree.reload_current_scene())

---

---

## PHASE 3 — Movement Systems
### ⏱️ Days 19–28 | 10 Days

> **What is this phase?**
> Movement in the Hunter Game is NOT normal. Running too fast causes you to phase through walls, then phase through other players, and if you go even faster — you vanish permanently. This phase builds that entire system, plus the underground digging mechanic. These are the two most creative and technically complex movement features in the game.

---

### 🏁 Milestone 3.1 — Basic Movement & Stamina Bar
**Target: End of Day 20**

> **What is a stamina bar?**
> A stamina bar shows how much "running energy" you have left. The faster you run, the faster it drains. When it's empty, something bad happens (in this game: you start phasing).

#### Tasks:
- [ ] Add a **speed variable** to both Hunter and Prey scripts
- [ ] Add a **stamina/energy bar** UI element visible above each player
- [ ] Holding `Shift` while moving drains stamina faster (sprinting)
- [ ] When not sprinting, stamina slowly recharges
- [ ] Hunter stats: smaller stamina bar, BUT recharges much faster
- [ ] Prey stats: larger stamina bar, BUT recharges very slowly
- [ ] Display the stamina bar visually as a colored bar (green → yellow → red as it depletes)

**Tools Used:** Unity (UI Slider / Image fill, Rigidbody2D)

---

### 🏁 Milestone 3.2 — Distortion Threshold System
**Target: End of Day 24**

> **What is the Distortion Threshold?**
> It's a 4-stage system triggered by running too fast for too long. Think of it like a speedometer with 4 danger zones:
> - **Normal**: Everything is fine.
> - **Phase Objects**: You run through walls. Prey can't shoot.
> - **Phase Players**: You run through other players too. Nobody can target you, but you can't target anyone either.
> - **Vanish**: You disappear entirely and are eliminated from the match. (Hunter can NEVER reach this — only Prey can.)

#### Tasks:
- [ ] Create a `distortion_level` variable (0 = Normal, 1 = Phase Objects, 2 = Phase Players, 3 = Vanish)
- [ ] Tie `distortion_level` to how long the player has been sprinting / stamina level
- [ ] **Level 0 — Normal:**
  - Standard movement and collision
  - Minor screen blur (use Unity's Post-Processing Volume with Lens Distortion (URP))
- [ ] **Level 1 — Phase Objects:**
  - Disable collision with walls and environment objects
  - Apply a wavy visual distortion shader to the player sprite
  - Prey in this state CANNOT fire their Net
- [ ] **Level 2 — Phase Players:**
  - Additionally disable collision with other player characters
  - Player cannot shoot OR net anyone
  - No one can target this player either (raycasts pass through them)
- [ ] **Level 3 — Vanish (Prey only):**
  - Player sprite becomes invisible
  - Player is removed from the match (treated as eliminated)
  - Show a message: `"[Prey name] ran too fast and vanished!"`
- [ ] **Hunter cap:** Hunter's `distortion_level` can never exceed Level 1 (Phase Objects)
- [ ] Show the current distortion level on screen as a simple text label for now

**Tools Used:** Unity (Shader Graph material for visual effects, Physics2D collision layers, Collider2D with isTrigger)

---

### 🏁 Milestone 3.3 — Underground Digging
**Target: End of Day 28**

> **What is digging?**
> Any player can press a button to "go underground" — they become invisible and cannot be targeted. However, they move slower underground, and they can only stay down for a limited time before they automatically resurface.

#### Tasks:
- [ ] Add a **dig stamina bar** (separate from run stamina) — visible only when underground or when pressing dig button
- [ ] Press `E` to go underground:
  - Player sprite changes to a small mole/dirt-clump placeholder sprite (or disappears)
  - Player is removed from all line-of-sight calculations
  - Player CANNOT be hit by the Gun or Net while underground
  - Player movement speed is reduced to 50% of normal speed
- [ ] The **dig stamina bar** depletes while underground
- [ ] When dig stamina hits zero: player automatically resurfaces
- [ ] Press `E` again (while underground) to manually resurface
- [ ] Add a **small dust/dirt visual effect** when entering and exiting the ground
- [ ] Test: Hunter shoots at digging Prey → shot passes through / misses

**Tools Used:** Unity (Coroutine, Physics2D collision layers toggling, simple particle effects via ParticleSystem)

---

---

## PHASE 4 — Shadow Vision & Communication System
### ⏱️ Days 29–37 | 9 Days

> **What is this phase?**
> Two important systems get built here. First, the "Shadow Mode" vision system — players can only see what's directly in their line of sight. Second, the Prey Radio Network — a 6-channel radio that degrades as Prey die.

---

### 🏁 Milestone 4.1 — Shadow Vision (Line-of-Sight Occlusion)
**Target: End of Day 32**

> **What is occlusion?**
> Occlusion means "blocking the view." If a wall is between you and something, you can't see that thing. This creates tension and stealth gameplay — you never know what's around the corner.

#### Tasks:
- [ ] Research Unity's **Light2D** and **CompositeCollider2D** system
- [ ] Add `ShadowCaster2D` nodes to all walls in the Tilemap
- [ ] Add a **Light2D** attached to each player (this represents their "vision")
- [ ] Configure the light so areas outside the player's cone appear dark
- [ ] Each player only renders other players/objects that are within their lit area
- [ ] Test: Walk behind a wall → cannot see players on the other side

> **Beginner Tip:** Unity has great YouTube tutorials on 2D URP lighting. Search "Unity 2D URP shadow vision tutorial" for step-by-step guides.

**Tools Used:** Unity (Light2D, ShadowCaster2D, CompositeCollider2D, Global Light 2D)

---

### 🏁 Milestone 4.2 — Radio System (6-Line Network)
**Target: End of Day 35**

> **What is the Radio System?**
> Each of the 6 Prey has a dedicated "radio channel." They can switch between channels to communicate. When a Prey dies, their channel goes offline. The more channels that go offline, the worse the audio quality gets for surviving Prey — creating tension.

#### Tasks:
- [ ] Create a `RadioManager` Singleton MonoBehaviour script
- [ ] Track 6 "radio lines" — each assigned to one Prey player
- [ ] Prey can press `1` through `6` to switch which radio line they're transmitting on
- [ ] UI: Show which lines are **active** (green) and which are **dead** (grey/red) in a small panel
- [ ] **Line Death:** When a Prey is eliminated:
  - Their line is marked as offline
  - Other Prey can no longer use that line to communicate
- [ ] **Clarity Degradation (visual simulation):**
  - With 6 active lines: UI shows clear text/voice label
  - With 4 active lines: add static text overlays on radio UI
  - With 2 active lines: heavy distortion indicators, text corrupted on screen
  - With 0 active lines: complete silence UI
- [ ] **Hunter Interception:** If a line is offline AND NOT sabotaged, the Hunter can walk near that player's corpse icon on the map and press `R` to "listen in" — show them that line's last transmitted message
- [ ] **Sabotage:** Any player can press `Q` near a dead Prey's position to sabotage their radio line — adds extra static effects to all remaining lines
- [ ] Note: Actual voice chat integration comes in Phase 6. For now, implement the UI and state logic.

**Tools Used:** Unity (Singleton MonoBehaviour, Unity UI (Canvas, Text, Image), Text/TextMeshPro components)

---

### 🏁 Milestone 4.3 — Proximity Chat UI Placeholder
**Target: End of Day 37**

> **What is proximity chat?**
> When players are physically close to each other in the game world, they can hear each other speak. The further apart they are, the quieter the voice becomes. Real voice integration comes later — this milestone just builds the system that KNOWS who is near whom.

#### Tasks:
- [ ] Write a `ProximityDetector` script
- [ ] Every 0.5 seconds, check distance between all players
- [ ] If two players are within a set radius (e.g., 200 pixels), flag them as "in proximity"
- [ ] Show a simple UI indicator: `"[PlayerName] is nearby"` when proximity is triggered
- [ ] This will be connected to actual voice chat in Phase 6

**Tools Used:** Unity (Vector2.Distance(), Collider2D with isTrigger)

---

---

## PHASE 5 — Lobby, Betrayal & Economy
### ⏱️ Days 38–44 | 7 Days

> **What is this phase?**
> Before the match starts, all 7 players sit at a virtual table and talk. They set the stakes (how much in-game currency they're betting), form temporary alliances, and trash-talk each other. This phase builds that lobby, the currency system, the betrayal (Prey-on-Prey netting), and prize pool distribution.

---

### 🏁 Milestone 5.1 — The Table Lobby
**Target: End of Day 40**

> **What is the Table Lobby?**
> A pre-game social space where all 7 players appear seated around a table. No combat yet — just talking, negotiating, and setting the prize pool.

#### Tasks:
- [ ] Create a new Scene: `TableLobby Scene`
- [ ] Design a simple top-down view of a table with 7 seats (one per player)
- [ ] Display each player's name and a "Ready" indicator above their seat
- [ ] Show the **current prize pool total** in the center of the table (updates live)
- [ ] **Host Minimum Stake:** The host player sets a minimum opt-in amount (text input or slider)
- [ ] **Voluntary Inflation:** Each player has a `+10`, `+50`, `+100` button to add more to their personal stake beyond the minimum
- [ ] **Match Start:** When all 7 players have confirmed their stake, show a "All Ready — Match Starting in 5..." countdown
- [ ] Transition from lobby to the main game map when countdown ends

**Tools Used:** Unity (Scene management, Unity UI (Canvas, Text, Image), InputField, Button)

---

### 🏁 Milestone 5.2 — Betrayal Mechanic (Prey-on-Prey)
**Target: End of Day 42**

> **What is betrayal?**
> Any Prey can use their Net on ANOTHER Prey (not just the Hunter). If successful, the victim Prey is eliminated and the betrayer claims their share of the prize pool. High risk — you have to get very close — but potentially very rewarding.

#### Tasks:
- [ ] Update the **Net mechanic** from Phase 2 so it can target other Prey (not just the Hunter)
- [ ] Add a confirmation check: `IF net_zone overlaps a Prey AND that Prey is NOT the current player → sacrifice that Prey`
- [ ] When a Prey is sacrificed:
  - Remove them from the match
  - Transfer their prize pool stake to the player who netted them
  - Show a dramatic screen message: `"[PlayerA] was betrayed by [PlayerB]!"`
- [ ] Betrayed Prey: their radio line goes offline (same as being killed by the Hunter)
- [ ] Test the risk: Prey must be very close to betray — this puts them in danger too

**Tools Used:** Unity (Collider2D OnTriggerEnter2D, Unity Events / C# delegates)

---

### 🏁 Milestone 5.3 — Economy & Prize Pool Distribution
**Target: End of Day 44**

> **What is in-game currency?**
> Players use in-game currency (name TBD) to place their stake/wager before each match. At the end of the match, the winner (or surviving Prey) splits the pool. Sacrificed Prey forfeit their share to whoever betrayed them.

#### Tasks:
- [ ] Create a `PlayerWallet` script — tracks each player's currency balance
- [ ] Display current balance in lobby and in-game HUD
- [ ] At match start: deduct each player's agreed stake from their wallet, add to `prize_pool`
- [ ] **Distribution Logic:**
  ```
  Hunter Victory → Hunter receives entire prize_pool
  Prey Victory   → Surviving Prey split prize_pool equally
                   (Sacrificed Prey forfeited their share to their betrayer)
  ```
- [ ] Show a **post-match results screen** with:
  - Who won
  - How much each player won/lost
  - Final currency balance
- [ ] **Starting Currency:** New accounts start with a fixed amount (e.g., 1000 coins)
- [ ] Note: Real-money purchase system is a future feature — for now just implement the in-game currency logic

**Tools Used:** Unity (Dictionary for wallet data, UI/Text/TextMeshPro components)

---

---

## PHASE 6 — Multiplayer Integration
### ⏱️ Days 45–50 | 6 Days

> **What is this phase?**
> Up until now, the game has been playable only on one computer (local testing). This phase connects everything to the internet so 7 different players can all play together in real time. This is technically the hardest phase — take it slow.

> **Beginner Note on Networking:** Multiplayer game development is complex. The key concept is that each player runs the game on their own computer, and the computers constantly send each other small messages: `"Player A moved to position X,Y"`, `"Player B fired their gun"`, etc. Unity has a built-in system for this.

---

### 🏁 Milestone 6.1 — Basic 1v1 Networked Connection
**Target: End of Day 46**

#### Tasks:
- [ ] Learn Unity's **Unity Netcode (NGO) API** (watch at least one tutorial: "Unity multiplayer tutorial")
- [ ] Implement a simple Host/Join system:
  - One player clicks "Host Game" — they become the server
  - Another player clicks "Join Game" and enters the host's IP address
- [ ] Sync player positions over the network using `NetworkTransform` component
- [ ] Test: Two players can move around the same map in real time on different computers
- [ ] Add player name display above each character

**Tools Used:** Unity (Unity Netcode (NGO) API, UnityTransport, NetworkTransform)

---

### 🏁 Milestone 6.2 — Full 1v6 Networking
**Target: End of Day 48**

#### Tasks:
- [ ] Scale up from 2 players to 7 players (1 Hunter + 6 Prey)
- [ ] Sync all game state over the network:
  - Player positions and rotation
  - Hunter reload state (so all Prey can see when Hunter is vulnerable)
  - Stamina/distortion levels
  - Underground status
  - Prize pool amounts
  - Match timer
- [ ] Handle player disconnection gracefully (remove them from match, possibly trigger AI bot — Phase 7)
- [ ] Test with at least 3 real players on different machines

**Tools Used:** Unity (RPC calls, NetworkTransform)

---

### 🏁 Milestone 6.3 — Voice Chat Integration
**Target: End of Day 50**

> **What is voice chat integration?**
> This connects actual microphone audio between players. Unity doesn't have built-in voice chat, so you'll use an external service.

#### Tasks:
- [ ] Research options: **Discord GameSDK** (free) or **Vivox** (game industry standard)
- [ ] For a beginner-friendly approach: Use **Discord's GameSDK voice overlay** or simply document that players use Discord in parallel for now (this is acceptable for a prototype)
- [ ] If integrating directly:
  - Connect the `ProximityDetector` from Phase 4 to the voice chat volume: further away = quieter
  - Connect the `RadioManager` from Phase 4 to in-game push-to-talk channels
- [ ] Test: Proximity chat works (players near each other can hear each other)
- [ ] Test: Radio channels work (Prey can switch which channel they broadcast on)

**Tools Used:** Discord GameSDK, or document as "use Discord" for prototype scope

---

---

## PHASE 7 — AI System
### ⏱️ Days 51–53 | 3 Days

> **What is this phase?**
> When a player disconnects mid-match, an AI bot should fill their slot so the game stays balanced. The AI watches how real players behave and tries to mimic them. For a 55-day prototype, we implement a basic version of this.

> **Beginner Note:** Full AI systems take months to build properly. In this phase, you're building a "good enough" AI for the prototype — one that behaves in a basic but believable way.

---

### 🏁 Milestone 7.1 — Basic Bot Movement (Prey AI)
**Target: End of Day 52**

#### Tasks:
- [ ] Create a `PreyBot` script that controls a Prey automatically
- [ ] Bot behavior logic:
  ```
  IF Hunter is reloading AND bot is close enough → move toward Hunter and net them
  IF Hunter has gun ready AND bot can see Hunter → run away from Hunter
  IF Hunter cannot see bot → wander randomly around the map
  IF underground digging makes sense (Hunter is close) → dig underground
  ```
- [ ] Bot uses the same movement system (stamina, distortion) as human players
- [ ] Bots do NOT betray other Prey (too complex for prototype — leave as a future update)

**Tools Used:** Unity (NavMeshAgent2D for pathfinding, StateMachine pattern)

---

### 🏁 Milestone 7.2 — Bot Activation on Disconnect
**Target: End of Day 53**

#### Tasks:
- [ ] Detect when a human player disconnects mid-match
- [ ] Spawn a `PreyBot` at that player's last position to replace them
- [ ] Bot inherits the disconnected player's remaining radio lines and stake
- [ ] Show a message: `"[PlayerName] disconnected — replaced by AI"`

**Tools Used:** Unity (peer disconnected signal, Scene instantiation)

---

---

## PHASE 8 — Testing & Polish
### ⏱️ Days 54–55 | 2 Days

> **What is this phase?**
> Testing means playing the game as many times as possible to find things that are broken, unfair, or confusing. Polish means fixing the most obvious rough edges. With only 2 days, focus on stability, not perfection.

---

### 🏁 Milestone 8.1 — Bug Hunt & Balance Pass
**Target: End of Day 54**

#### Tasks:
- [ ] Play at least 10 complete matches with real players (friends, teammates)
- [ ] Fix any crashes or game-breaking bugs first
- [ ] Adjust these balance values based on playtesting:
  - Hunter reload time
  - Match timer length
  - Stamina drain/recharge rates
  - Distortion threshold timing
  - Dig stamina duration
- [ ] Fix any networking desync issues (players seeing different positions)
- [ ] Make sure all three win conditions trigger correctly 100% of the time

---

### 🏁 Milestone 8.2 — UI & Audio Pass
**Target: End of Day 55**

#### Tasks:
- [ ] Replace placeholder colored squares with simple sprite art for Hunter and Prey
- [ ] Add at least basic sound effects:
  - Gunshot sound
  - Net throw sound
  - Reload sound (mechanical clicking)
  - Underground dig sound (digging/thud)
  - Betrayal sound (dramatic sting)
  - Match win/lose jingle
- [ ] Make sure all UI is readable and clearly labeled
- [ ] Add a simple **main menu** Scene with: `Play`, `Host`, `Join`, `Quit` buttons
- [ ] Create a basic **credits screen**

**Tools Used:** Audacity, BFXR, Unity (AudioSource, Animator / Animation component)

---

---

## 📊 Summary Table

| Phase | Days | Duration | Key Deliverable |
|---|---|---|---|
| 1. Setup & Foundation | 1–7 | 7 days | Project running, basic map, version control |
| 2. Core Gameplay Prototype | 8–18 | 11 days | Gun, Net, Reload, Timer, Win/Lose |
| 3. Movement Systems | 19–28 | 10 days | Distortion Threshold, Digging |
| 4. Shadow Vision & Radio | 29–37 | 9 days | Occlusion vision, 6-line radio |
| 5. Lobby, Betrayal & Economy | 38–44 | 7 days | Table lobby, Prize pool, Betrayal |
| 6. Multiplayer Integration | 45–50 | 6 days | 1v6 online play, voice chat |
| 7. AI System | 51–53 | 3 days | Bot fills disconnected player slots |
| 8. Testing & Polish | 54–55 | 2 days | Bug fixes, balance, basic audio/art |

---

## 🚨 Risk Watch

| Risk | Likelihood | Mitigation |
|---|---|---|
| Multiplayer networking takes longer than expected | High | Start Phase 6 tutorials early (even during Phase 4 downtime) |
| Shadow vision system is technically complex | Medium | Use a Unity tutorial; don't build from scratch |
| Voice chat integration fails | Medium | Fall back to "use Discord" for prototype |
| AI is too hard to build | Low | A very basic state machine is enough for prototype |
| Scope creep (adding new features) | High | Stick strictly to this document. Post-launch features are listed in the GDD. |

---

*Document Version: 1.0 — Based on Hunter Game GDD*
*Timeline: 55 Days | Target: Closed Testing Build*
