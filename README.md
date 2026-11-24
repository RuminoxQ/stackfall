# STACKFALL

A falling-block puzzle game built for event booths. It's one self-contained `index.html` that runs in any modern browser on PC, laptop, tablet and phone.

## Play

- Open `index.html` in a browser, or
- Turn on **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / root) and open the link it gives you.

## Modes

- **Booth round**: score as much as you can before time runs out (default 2 minutes).
- **1v1 Versus**: clearing lines sends junk rows to your opponent. Whoever tops out loses; if time runs out, the higher score wins.
  - **Same screen**: two boards side by side, with two controllers or one shared keyboard. Works on a tablet held sideways.
  - **Online**: two devices joined by a 4-letter match code. Only works on the hosted claude.ai version while signed in, not from this file or GitHub Pages.
- **Garbage race**: survive while junk rows rise from the bottom faster and faster. Ranked by time survived.
- **Zen**: no game over and calm music, for relaxed play.
- **Marathon**: endless, speeds up every 10 lines.
- **Sprint 40**: clear 40 lines as fast as you can.

## Controls

| Action | Keyboard | Controller | Touch |
|---|---|---|---|
| Move | ← → (A D) | D-pad / left stick | ◀ ▶ or swipe |
| Soft drop | ↓ (S) | D-pad ↓ | ▼ or drag down |
| Hard drop | Space (W) | D-pad ↑ / RT | DROP or flick down |
| Rotate | ↑ / X, Z | A, B | ⟳ ⟲ or tap the board |
| Rotate 180° | E | Y | Two-finger tap |
| Hold | C (Shift) | LB / RB | HOLD or swipe up |
| Pause | Esc / P | Menu | ‖ |

You can change every keyboard and controller binding in **Settings → Controls**.

**1v1:** Player 1 uses A D S, W/Space to drop, E Q to rotate and L-Shift/C to hold. Player 2 uses the arrow keys, Enter to drop, ↑ and / to rotate and R-Shift to hold. Controller 1 plays for Player 1 and controller 2 for Player 2.

## Features

- **Neon arcade look**: glowing blocks, an animated synthwave grid and sunset, a flickering neon logo, confetti and bouncy pop-ups
- **Rival chase**: while you play, see who you're chasing on today's board and how many points you need to pass them
- **ON FIRE meter**: clear lines on 6 pieces in a row and every clear scores double points
- **Badges**: unlock achievements during a game (First STACK!, Stack Master, Back-to-back, On Fire, Spin Doctor, Perfectionist, Line Machine, Six Figures, Survivor, Speed Demon)
- **Results screen**: your rank today, 1–3 stars, badges earned, the board around you and how far you are from #1
- **Hall of Fame**: big-screen podium with a crown for #1, plus a scrolling ticker of booth highlights on the title and big screen

- Callouts for special moves (4-line STACK!, T-Spins, combos, back-to-back, perfect clear)
- Row flashes, screen shake and controller or phone vibration that grow with the size of the clear
- Music that adds layers and speeds up as the level rises
- A 4-step tutorial that shows the right buttons for the player's device
- Accessibility options: colour-blind block symbols, high-contrast lines, left-handed touch layout, reduced shake and flashing, slower starting speed
- QR code on the title screen and big-screen leaderboard so visitors can play on their phones. Set the link in **Settings → Booth**.
- Booth tools: event name, prize line, round length, leaderboard shown when the game is idle, name entry with a basic rude-word filter, full-screen big-screen leaderboard

## Leaderboard storage

Scores go to a shared **Firebase Firestore** database (project `stackfall-b70b8`, free Spark plan), so every device that opens the GitHub Pages link sees one live leaderboard. Each device also keeps a backup copy in its browser, so games still save without internet.

- The game reads new scores every 15 seconds while the title, leaderboard, game over or name screen is showing.
- Security rules allow anyone to read scores and add a valid new score, but nobody can edit or delete scores from the game.
- Scores are kept for **7 days**. The game deletes older ones automatically (about once an hour, from any open copy of the game), and the rules only allow deleting scores more than 7 days old. Change `KEEP_DAYS` in `index.html` and the `604800000` (7 days in ms) in the rules to keep them longer or shorter.
- To remove a newer score (a rude name, say), open the Firebase console → Firestore Database → `scores` and delete the document.

## Credits

QR codes are made with [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) by Kazuhiko Arase (MIT licence), which is included in `index.html`.
