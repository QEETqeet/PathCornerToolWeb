# Qeet's Path Corner Interpolation Tool (Web)

> Note: changes are planned to make the tool more intuitive in the future.

A single-file browser tool for generating interpolated `path_corner` entities for Neverball and Quake 3 maps.

---

## What it does

Instead of placing every path corner by hand in your map editor, you define a handful of key nodes and let the tool fill in all the intermediate points using easing curves. The result is a ready-to-paste block of entities for your `.map` file.

---

## Features

- Add key nodes with position (X Y Z) and angles (X Y Z)
- Adjustable position step size: 1, 8, 32, 64, 128, 256
- Each segment between nodes has its own independent settings
  - Easing XY, Easing Z, and Easing Angles are all separate
- Multi-select nodes to apply the same segment settings to several at once
- 23 easing types: Linear, Sine, Quad, Cubic, Expo, Back, Elastic, Bounce, and Hold
  - Each (except Linear and Hold) available as In, Out, or In and Out
- Hold easing: the object stays at the origin point for a set time, then jumps instantly to the destination using a zero-speed ghost path corner
- Loop mode with its own dedicated segment settings (last node back to first)
- Exports `path_corner` entities with `speed`, `smooth`, `origin`, and `angles`
- Copy to clipboard or save as a `.txt` file

---

## How to use

**Adding nodes**

Fill in a name, position and angles, then click Add node. Repeat for each key point in your path.

**Editing nodes**

Click a node in the list to select it. Its values load into the Edit section. Change what you need and click Apply changes.

**Segments**

Select one or more nodes in the list (Ctrl+click or Shift+click for multiple). The Outgoing segment section lets you set the easing and number of intermediate points for the path between each selected node and the one after it. Click Apply to segment(s) to confirm.

**Loop segment**

If Loop is checked on export, the section at the bottom of the Outgoing segment area controls how the path travels from the last node back to the first. It has its own easing and point count.

**Hold easing**

When you set any axis easing to Hold, the segment generates two path corners at the origin position: one with the normal speed (acting as a wait time) and one with speed 0 (triggering an instant jump to the destination). This is useful for snap-cut animations.

**Exporting**

Set a prefix (the base name for all entities), a speed value, and whether to loop. Click Generate entities, then Copy or Save .txt to use in your map.

---

## Easing reference

| Type | Description |
|---|---|
| Linear | Constant speed |
| Sine | Gentle smooth curve |
| Quad | Slightly stronger curve |
| Cubic | Stronger curve |
| Expo | Very sharp acceleration or deceleration |
| Back | Slight overshoot past the endpoint |
| Elastic | Spring-like oscillation at the endpoint |
| Bounce | Simulates a physical bounce |
| Hold | No movement, then instant jump at the end |

Each type (except Linear and Hold) comes in three variants: In, Out, and In and Out.
