---
title: Usage
links:
  - title: Using the Mikro
    description: what the device does, what the keys do, and the menu -- grows with every feature
menu:
    main:
        weight: 5
        params:
            icon: music

comments: false
toc: true
---
# Using the Mikro

How the Mikro behaves with the DIY software: what it shows, what the keys do, and
how to find your way through the menu. This page grows with every new feature.

**Status (2026-10-04):** everything below runs today with the desktop host program;
the bridge box will run the very same behaviour. Behind the scenes it is one state
machine -- this page is its human-readable version.

## At a glance

```text {linenos=false}
   plug in
      │
      ▼
 ┌─────────┐ MENU  ┌──────┐ push  ┌───────────┐
 │ RUNNING │ ────▶ │ MENU │ ────▶ │ METRONOME │
 │         │ ◀──── │ list │ ────▶ │ SCENE ──▶ COLOR, CC
 └─────────┘ MENU  │      │ ────▶ │ TEST (3 s)│
                   └──────┘ ◀──── └───────────┘
                            MENU (one level up)
```

There is no start-up animation: the Mikro already runs its own self-test when it gets
power. The full light-and-display test is in the menu (TEST).

## Running mode

This is where you play. The pads, the encoder, the touch strip and almost all buttons
belong to the current **scene** (your sounds and MIDI assignments).

**The display** shows the tempo:

| Display | Meaning |
|---|---|
| `(I) 120 BPM` | internal tempo -- the device's own clock |
| `(E) 090 BPM` | external tempo -- following an incoming MIDI clock |

**The lights:**

- **MENU, TAP, Left, Right, Scene** are lit.
- **TEMPO** is **steadily lit** while the external tempo is in use and **blinks with
  the beat** while the internal tempo is in use.
- The **LEDs above the touch strip** show a metronome pendulum: one sweep per beat,
  slowing down at the ends like a real mechanical metronome.
- Every other button glows **very dimly**, so you can still find your way on a dark
  stage.

**Device keys** -- these are never sent to your music:

| Key | What it does |
|---|---|
| **TAP** | Tap the tempo. From the 4th tap on, the tapped tempo becomes the internal tempo, and the device switches to it. A pause of more than 2 seconds starts a new measurement. |
| **TEMPO** | Choose the tempo source: **internal** or **external**. With "external", the device follows an incoming MIDI clock; if the clock stops for more than a second, it falls back to the internal tempo on its own -- and picks the clock up again when it returns. |
| **MENU** | Open the menu. Notes you are still holding are ended first, so nothing hangs. |

**About the external tempo:** when a MIDI clock starts, the device measures half a
beat before it switches to `(E)`, so the first number you see is already right. The
display only changes when the tempo really changes, not on every tiny timing wobble
of the incoming clock.

## The menu

| Display | |
|---|---|
| top row, small | `MENU 01/03` -- which entry, out of how many |
| bottom row, large | the entry's name, e.g. `METRONOME` |

- **Left / Right** or **turning the encoder**: previous / next entry. The list wraps
  around at both ends.
- **Pushing the encoder**: open the entry.
- **MENU**: one level up -- from an entry back to the list, from the list back to the
  running mode.
- While the menu is open, nothing reaches your music: pads and buttons are silent.

### METRONOME

Choose the colour of the metronome pendulum.

- The **pads show 16 colours**; the current one **blinks**.
- All buttons go **dark** so the colours stand out -- except MENU (lit) and Star and
  Search (dim): they sit next to the encoder and keep it findable in the dark.
- **Press a pad** to choose its colour -- the pendulum takes it at once, and the new
  colour now blinks. Try as many as you like.
- **Push the encoder** or press **MENU** to go back to the list.

### SCENE

Set up your scenes right on the device -- for now their **pad colours**.

1. **Choose a scene** (1 to 10) with Left / Right or the encoder. The top row shows
   `SCENE 01/10`, the bottom row its name -- or `EMPTY`. The chosen scene **plays at
   once** and the pads show its colours, so what you edit is what you play.
2. **Push the encoder** to open it. An empty slot becomes a new, blank scene: all pads
   dark, playing notes 36 to 51. Scenes 4 to 10 get the names **USER-1** to **USER-7**
   (names can't be typed on the device).
3. Choose **COLOR** (or **CC** -- listed, but coming later) with the encoder and push it.
4. **Pick a pad:** all pads blink softly in their colours (pads without a colour blink
   white). Press the pad you want to colour.
5. **Pick a colour:** that pad keeps blinking brightly, the other 15 pads show the
   colours. Press one -- the pad takes it (dim at rest, bright while you hit it), and
   you are back at step 4 for the next pad. Pressing the blinking pad keeps its colour.
   **ERASE** is lit while the pad has a colour: press it to switch the pad off (no
   colour), and you are back at step 4. On a pad without a colour, ERASE stays dark.

From step 3 on, the buttons go dark except MENU, Star and Search (and ERASE in step 5),
like in METRONOME.
**MENU** goes one level up at every step. For now, changes last until the program is
closed; saving comes with the bridge box.

### TEST

Lights **every LED** and shows a **test picture** on the display for 3 seconds, then
returns to the list by itself (MENU ends it earlier). Use it to check that all lights
and the display work.

## Coming next

More menu entries and the scenes' own settings. This page will follow.
