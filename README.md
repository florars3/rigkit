# RigKit

Build a desktop PC step by step in 3D, then power it on and see if it posts.

RigKit is a free, in-browser trainer for first-time PC builders. Pick compatible parts, follow ten guided build steps on a 3D workbench, then press the power button. Mistakes behave the way they do on a real bench:

- forgot the 8-pin CPU cable → the **CPU** debug LED stays lit
- no PCIe power to the graphics card → **VGA** LED, no picture
- cooler film left on or no paste → temperatures climb to a thermal shutdown
- extra standoff under the board → the PSU trips its short-circuit protection
- PSU too small → it shuts off during the stress test
- memory in A1 + A2 → it boots, but in single channel

When it fails, it tells you which step to go back to.

## Features

- 10-step guided build: parts, CPU, M.2 SSD, memory, cooler, motherboard, PSU, graphics card, cables, power on
- Compatibility checker for CPU socket, memory type, and PSU wattage (with 30% headroom suggestion)
- Simulated POST with CPU / DRAM / VGA / BOOT debug LEDs, BIOS screen, temperatures and fan speed
- Stress test
- Undo, reset and save (saved in your browser)
- Keyboard: `Enter` to do a step, `U` to undo; drag to orbit, scroll to zoom
- Works on phones

## Run it

It's one static file with no build step.

```bash
# any static server works
npx serve .
```

Then open http://localhost:3000. Three.js r128 loads from cdnjs.

## Deploy

Import the repo into Vercel as a static site (framework preset: **Other**, no build command, output directory `.`). Every push to `main` deploys.

## Notes

Power figures are manufacturer peak ratings for the CPU and graphics card, plus 60 W for everything else. They're a guide, not a PSU calculator.

Inspired by [RoverKit](https://roverkit.vercel.app/).
