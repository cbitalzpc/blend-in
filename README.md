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
5. Take turns giving a one-word clue, vote, then the host taps **Reveal the Chameleon**.

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
