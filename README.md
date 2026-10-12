# Laser Settings Estimator

Starting-point power, speed and pass settings for the Makerspace Laser Lab (Room 1408E). Pick the laser, the material and the job. Get a number to try first.

**Live app:** https://im4creative.github.io/MS-LL-Settings-Estimator/

![Settings tab](docs/screenshots/settings.png)

## What it does

Pick a **laser type** (CO₂ or diode), a **beam**, a **material** and a **job** (cut or engrave). The estimator returns:

- **Power** as a percentage, with the watts at the work
- **Speed** in mm/min or mm/s
- **Passes**
- Kerf and offset (cuts) or line density and depth (engraves)
- Time per metre or per 100 cm²
- Air assist level
- Numbered steps, plus tips and warnings for the chosen material

**Copy settings** puts the result on the clipboard, ready to paste on an offcut note.

## Tabs

| Tab | Use it to |
| --- | --- |
| **Settings** | Choose laser, beam, material, job, thickness and cut quality. Results update live. |
| **Test grid** | Build a 5 × 5 power-by-speed grid around your settings. Download it as SVG for LightBurn. |
| **Materials** | See which materials each laser can cut or mark, what is banned, and the house rules. |

![Test grid tab](docs/screenshots/test-grid.png)

## How it decides

- **Slow-cut threshold: 250 mm/min.** If a cut would have to run slower than this, the estimator adds passes instead of slowing down. Slow cuts char and flare. A note shows when this happens.
- If even the maximum passes can't stay above the threshold, it says so and lets the speed drop.
- Energy per millimetre comes from material, thickness and laser absorption. Quality sets the safety margin: Quick, Standard or Best edge.
- Engraving targets a depth (Light, Standard, Deep) at the material's usual line density.
- CO₂ tubes under 10% power fire unevenly. The estimator warns you to raise speed instead.
- A diode beam can't cut clear acrylic, Delrin and some others. The result says to switch to CO₂.

### Machine limits

Under **Machine limits** you can set actual watts, top speed and the slowest cut speed. Use this when a tube has aged or the lens is dusty. **Reset** returns the nominal values. Your changes are saved in your browser only.

### Lasers in the app

| Type | Beams |
| --- | --- |
| CO₂ 10.6 µm | 40 W, 60 W, 100 W tubes (generic, replace with the lab's real machine) |
| Diode 455 nm | Falcon2 Pro 40 W normal, Falcon2 Pro 20 W precise, 1.6 W module |

## Materials

25 materials across wood, plastic, natural, textile, paper, foam, metal and brittle. Metals and brittle materials (glass, slate, tile) are mark-only. The Cut through option greys out for them.

![Materials tab](docs/screenshots/materials.png)

## Safety

The Materials tab lists what never goes in the laser: PVC and vinyl, polycarbonate, ABS, PTFE, fiberglass and FR-4, carbon fibre, HDPE, chrome-tanned leather, galvanised steel, and anything unlabelled.

**These are starting points.** The sheet in front of you has the final say. Always test on an offcut.

## Run it

Open `index.html` in a browser. It is one self-contained file, so there is nothing to install or build.

## Design

Built with the Yazaki Makerspace design system: Laser Lab red, National Park display type, stencil icons, and the Binny and Makesafe mascots, on a wood-burned look.

## Known gaps

- CO₂ machine specs are placeholders.
- All numbers are estimates and have not been calibrated against lab test cuts.
- Safety copy is general shop knowledge. Have lab staff review it.
