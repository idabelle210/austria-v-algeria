# Austria v Algeria

A small top-down 5-a-side soccer game for the phone. One file (`index.html`), no build step.

- **Play the computer**: pick Austria or Algeria, 3-minute match.
- **Play a friend**: tap *Play a friend*, then *Text the link*. When your friend opens it, the game starts. Your phone runs the match; theirs sends its controls over a direct peer-to-peer connection (WebRTC via PeerJS's free public signaling server).

## Lineups
- Austria: Schlager (GK), Alaba, Cannavaro ’07, Arnautović, Ronaldinho ’07
- Algeria: L. Zidane (GK), Bensebaïni, Kaká ’07, Mahrez, Henry ’07
- At half time Sebastien comes on for whoever's losing. EA Sports: Sebastien's in the game.

Edit `ROSTER`, `LEGEND` and `QUIPS` near the top of the script to change names.

## Controls
- Left thumb anywhere on the left half: move (floating stick).
- **Shoot**: hold to power up, release to shoot. Aim with the stick; shots toward goal get a little aim help.
- **Pass**: passes to the teammate closest to where you're pointing.
- Without the ball: Shoot = **Sprint** (tackles harder), Pass = **Switch** player.
- Desktop: WASD / arrows, Space = shoot, K = pass.

## Hosting (needed for the friend link)
The friend link has to point at a public URL. GitHub Pages is the easiest:

```
git remote add origin https://github.com/<you>/austria-v-algeria.git
git push -u origin main
```

Then on GitHub: Settings → Pages → Source: *Deploy from a branch* → `main` / root. The game will be at `https://<you>.github.io/austria-v-algeria/`. Open it in Safari, Share → *Add to Home Screen* for a full-screen icon.

To play the computer, you can also just open `index.html` locally.

## Notes
- Both players need to be online. If a game won't connect on cellular, try Wi-Fi — some carrier networks block direct peer-to-peer connections. (Fix if it becomes a problem: add a TURN server to the `new Peer(...)` config.)
- Keep the host's screen open. Locking the phone or switching apps drops the match.
- Testing two players on one computer without internet: open `index.html?local=1` in two tabs on a local server (`python3 -m http.server`), tap *Play a friend* in one, open the shown link in the other.
