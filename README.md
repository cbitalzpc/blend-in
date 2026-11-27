# Blend In 🦎

A phone-based hidden-word party game. One device is the host (the main screen); everyone else scans a QR code to join.

## How to play
1. Open the site on the main screen, tap **I'm the host**, and log in (default password: `chameleon`).
2. Everyone scans the QR code and types their name.
3. The host picks a topic (or 🎲 random) and taps **New round**.
4. The 4×4 board shows on the main screen and every phone. Each player **holds** the button on their phone:
   - regular players see the secret word,
   - one random player sees **"You are the Chameleon"**.
   The button looks the same for everyone until it's held.
5. **Hints:** the host's *Turns & hints* panel sets the order (▲▼ or 🔀 Shuffle) and whose turn it is (tap a name, or **Next turn ▶**). The host types each person's hint; hints show on every phone (Enter jumps to the next player).
6. **Discussion:** the host taps **💬 Start discussion**. A countdown shows on every screen (set the length with − / + in the hints panel; **Pause**, **+30s**, or **Skip to voting** while it runs). When it hits 0, voting starts automatically.
7. **Voting:** everyone votes on their phone. Votes stay secret; the host sees only who has voted. The host taps **Reveal votes** and the player with the most votes is checked:
   - not the Chameleon → a big ✕ flashes on every screen, they're listed under *Voted out*, and discussion starts again, then another vote,
   - a tie → ⚖️ flashes and it goes back to discussion,
   - the Chameleon → 🦎 flashes on every screen with "Caught!" and the secret word.
   You can also pick who was voted out by hand, or **Reveal anyway** to end the round.

Players who refresh or rejoin with the same name keep their role for the current round. People who join mid-round get in on the next one.

## How it works
It's a static site (works on GitHub Pages). Devices talk directly via WebRTC using [PeerJS](https://peerjs.com/)'s free public broker — no server to run. The host's device holds the game state; the Chameleon's phone is never sent the secret word.

## Change the host password
Open the site, open the browser console (F12), and run:

```js
await hashPw("your new password")
```

Paste the result into `HOST_PASSWORD_HASH` near the top of the script in `index.html`. (This is a light gate to keep players off the host screen — it runs in the browser, so it isn't real security.)

## Topics
All 40 topic cards are in `cards.js` — edit or add topics there (each needs exactly 16 words).
