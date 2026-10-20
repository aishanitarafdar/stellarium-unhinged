# Stellarium Unhinged

A parody of the [Stellarium](https://stellarium.org) planetarium app, built for **Steal//Remake**, a 24-hour remix hackathon.

Stellarium calmly labels the constellations. In *Stellarium Unhinged*, the constellations come alive: they dance, flip, sleep, and beat each other up.

## How to run it

The app is three files with no build step and no backend.

- **Quickest:** double-click `index.html`.
- **To test on a phone:** run a local server in the project folder, then open `http://<your-computer's-IP>:8000` on a phone on the same Wi-Fi.

  ```powershell
  python -m http.server 8000
  ```

- **To share a link:** upload the folder to GitHub Pages or Netlify (both free). Phones only allow shake-to-rave and the share button on `https://` pages, so a hosted link works best for the demo.

## What you can do

| Control | What happens |
|---|---|
| **Tap a constellation** | Opens a fake info card with absurd stats, a random ridiculous fact, and one real astronomy fact |
| **Sound** | Turns on dramatic music and battle sound effects |
| **Figures** | Shows or hides the mythological artwork behind the stars |
| **Rave** | Rainbow lasers, flashing stars, double-speed dancing and faster music. Shaking your phone also starts an 8-second rave |
| **Real mode** | Six seconds of calm, accurate, Stellarium-style sky, then back to chaos |
| **Share** | Takes a screenshot of the sky and shares it, or saves it as `stellarium-unhinged.png` |
| **Battle** | All four fights happen at once in the sky |

## The cast

| Constellation | Dance moves |
|---|---|
| **Orion** | Breakdances: toprock, windmill, headspin |
| **Ursa Major** | Drifts lazily, yawns, tips over and snores |
| **Cassiopeia** | Can't decide if she's a W or an M, so she keeps flipping |
| **Scorpius** | Chases Orion, snaps his claws, makes a tactical retreat |
| **Perseus** | The robot, voguing with Medusa's head, the moonwalk |
| **Cetus** | The worm, a dolphin leap, chomping to the beat |
| **Hercules** | Somersaults, jumping jacks, flexing, the sprinkler |
| **Draco** | Slithering, the twist, a fire dance |

## Battle mode

Four matchups fight at once, each pair where it stands in the sky:

- Orion vs Scorpius
- Perseus vs Cetus
- Hercules vs Draco
- Cassiopeia vs Ursa Major (who is not happy about being woken up)

Each fight has lunges, dodges, hit flashes, POW!/WHIFF! bursts, health bars and screen shake. A sports announcer comments on the action in a caption at the bottom of the screen. Every attack is decided by chance (28% dodge, 12% critical hit), so **the winner is always random**. Losers fall out of the sky like shooting stars, and when all four fights are over, a page of dramatic fake obituaries lists everyone who lost.

## What I changed from Stellarium

| Stellarium | Stellarium Unhinged |
|---|---|
| Constellations sit still | Every constellation has its own personality and dance routine |
| Calm object-info panel | Fake info cards with absurd "facts" (plus one real one) |
| Constellation artwork is a static layer | The artwork bends, spins and flips with the stars as they move |
| No conflict whatsoever | A four-way sky battle with health bars, an announcer and obituaries |
| Silent | Dramatic orchestral music and battle sound effects |
| Serious | Rave mode |
| Always realistic | Realistic for exactly six seconds, in Real mode |

It is a new web app written from scratch. **No Stellarium code is used.** Only the idea and the look of a planetarium sky are borrowed.

## How it works 

- **Everything is drawn on one HTML `<canvas>`**, redrawn about 60 times a second.
- **Each constellation is data:** a list of star positions and a list of lines connecting them.
- **Each personality is a small function** that takes the resting stars and the current time and returns new star positions (a "pose"). For example, Cassiopeia multiplies her stars' heights by −1 to turn W into M, and Orion's windmill rotates every star around his belt.
- **The artwork follows the stars.** Every frame, the app finds the transform (move, rotate, scale, stretch, flip) that best carries the resting stars onto their current positions, and applies it to the engraving.
- **Battles** are a series of 1.4-second attacks. Each one randomly picks the attacker, whether the defender dodges, and whether it's a critical hit.
- **Sound needs no audio files.** The orchestral music (strings, choir, brass, timpani) and the sound effects are generated live with the Web Audio API.
- **Tapping** finds the nearest star drawn in the last frame, so it works on moving constellations.
- **It works on phones and laptops.** The layout switches between rows (portrait) and a 2×2 grid (landscape), and the canvas is scaled for high-resolution screens.

## Files

| File | What's in it |
|---|---|
| `index.html` | Page structure: the canvas, buttons, info card and obituary page |
| `style.css` | Layout and styling of the buttons and cards |
| `app.js` | Everything else: stars, dances, battles, sound, and the artwork (stored inside the file as images) |

There are no frameworks, no paid APIs, and no backend.

## Credits

- **[Stellarium](https://stellarium.org)**: the free, open-source planetarium (GPL) that this project parodies. All respect to the Stellarium team.
- **Constellation artwork**: engravings by Sidney Hall from *Urania's Mirror* (London, 1824), which are in the public domain. Scans are from Wikimedia Commons. The figures were cut out of the original cards and recolored silver for this project.
- **Star names and real facts**: standard astronomical data (Algol's 2.87-day dimming, Mira's ~332-day cycle, M13 in Hercules, Thuban as the ancient pole star).
- **Mythology**: Greek myths of Orion, Scorpius, Cassiopeia, Perseus, Cetus, Hercules and Draco, retold with considerably less dignity.

Built with help from Claude.
