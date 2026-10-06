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

This is where you play. The pads, the touch strip and most buttons belong to the
current **scene** (your sounds and MIDI assignments).

**The display** shows the tempo:

| Display | Meaning |
|---|---|
| `(I) 120 BPM` | internal tempo -- the device's own clock |
| `(E) 090 BPM` | external tempo -- following an incoming MIDI clock |

**The lights:**

- **MENU, TAP, Star, Scene, TEMPO** are lit.
- **Left / Right** are lit while the internal tempo `(I)` is in use -- then they change
  the tempo (see below). With the external tempo `(E)` they glow dimly and do nothing.
- **STOP / PLAY** with the internal tempo `(I)`: STOP is lit while the tempo plays,
  PLAY while it is stopped -- the other one glows dimly. With the external tempo `(E)`
  both are off.
- The **LEDs above the touch strip** show a metronome pendulum: one sweep per beat,
  slowing down at the ends like a real mechanical metronome -- while the tempo runs.
- Every other button glows **very dimly**, so you can still find your way on a dark
  stage.

**Device keys** -- these are never sent to your music:

| Key | What it does |
|---|---|
| **TAP** | Tap the tempo. From the 4th tap on, the tapped tempo becomes the internal tempo, and the device switches to it. A pause of more than 2 seconds starts a new measurement. |
| **TEMPO** | Choose the tempo source: **internal** or **external**. With "external", the device follows an incoming MIDI clock; if the clock stops for more than a second, it falls back to the internal tempo on its own -- and picks the clock up again when it returns. |
| **MENU** | Open the menu. Notes you are still holding are ended first, so nothing hangs. |
| **Star** | Pad brightness -- see below. |
| **Encoder, Left / Right** | With the internal tempo `(I)`: the tempo, 1 BPM per step (30 to 300). No push needed -- the display and the pendulum follow at once. With the external tempo `(E)` they do nothing: the tempo comes from outside. |
| **STOP** | With the internal tempo `(I)`: stops it -- the pendulum goes off (and later no clock is sent out). The tempo stays on the display. |
| **PLAY** | With the internal tempo `(I)`: starts it again from beat 0. With the external tempo `(E)`, PLAY and STOP do nothing -- the clock comes from outside, and its pendulum runs even if you stopped the internal one. |
| **Scene** | Choose the playing scene -- see below. |

**Choosing a scene (Scene):** a quick key, not a menu. Press **Scene**: it blinks,
and the display shows `SCENE 01/10` and the scene's name (or `EMPTY`). Turn the
encoder or press **Left / Right** -- the chosen scene **plays at once**, and the pads
show its colours. An empty slot shows dark pads and the playing scene stays. Pads and
the touch strip keep playing. **Scene**, **MENU** or **Star** takes you back.

**Pad brightness (Star):** a quick key for the stage, not a menu. Press **Star**: the
top row shows `BRIGHTNESS`, the bottom row the level: `LEVEL 1/3` (dim, the start
value), `LEVEL 2/3` or `LEVEL 3/3` (brightest). Turn the encoder or press **Left /
Right** to make all pads at rest dimmer or brighter -- you see it at once. (The pads
know one more step, but it looks almost the same as the dimmest, so it is left out.) A pad you hit always lights at full brightness, so it stands out. At
`LEVEL 3/3` the pads already rest at full brightness, so a pad you hit lights **white**
instead. The pads and the touch strip keep playing meanwhile. **Star** (or MENU) again,
and you are back.

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

**Where am I?** Below the list, the top row starts with one `<` per level -- that's
how many MENU presses take you back to the list -- followed by what you chose one level
up, and, where you choose from a list, your position in it:

| Top row | Where |
|---|---|
| `MENU 02/03` | the menu list |
| `< SCENE 04/10` | SCENE: the scene list |
| `<< USER-1 01/02` | inside scene USER-1: its settings |
| `<<< COLOR` | COLOR: pick a pad |
| `<<<< PAD 10` | pad 10 (the number printed on it): pick a colour |

A long scene name is shortened so the row fits.

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
   `< SCENE 01/10`, the bottom row its name -- or `EMPTY`. The chosen scene **plays at
   once** and the pads show its colours, so what you edit is what you play.
2. **Push the encoder** to open it. An empty slot becomes a new, blank scene: all pads
   dark, playing notes 36 to 51. Scenes 4 to 10 get the names **USER-1** to **USER-7**
   (names can't be typed on the device).
3. Choose **COLOR** (or **CC** -- listed, but coming later) with the encoder and push it.
4. **Pick a pad:** nothing blinks on and off. The pads glow softly, switching between
   their colour and white; pads without a colour stay white. Press the pad you want to
   colour.
5. **Pick a colour:** all 16 pads show the 16 colours. The pad you are colouring is
   brighter and switches between the colour at its place and its current colour -- or
   white, when it has none yet or the two are the same. Press any pad, that one
   included -- your pad takes its colour (dim at rest, bright while you hit it), and you
   are back at step 4 for the next pad.
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
