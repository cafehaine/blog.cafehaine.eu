title: Generating 3D models from 2D bitmaps
summary: The secrets behind our Cozy Winter Jam 2025 submission
tags: gamedev,python,blender,inkscape,godot,gimp
date: 2025-01-31
lang: en
---
# Our submission to the Cozy Winter Jam 2025

Cozy Winter Jam 2025, hosted by Virtual Turtle, lasts 3 days, optional theme
was metamorphosis.

Game made with my significant other https://gemma-pricot.itch.io/

A paper-cut styled [diorama](https://en.wikipedia.org/wiki/Diorama) which
represents an autumn scene that the player has to transition into the winter
through a series of small puzzles.

https://gemma-pricot.itch.io/winter-treasures

Please note that the currently uploaded version at the time of writing this
article contains many bugs and missing features, which will hopefully be fixed
soon after the end of the game jam voting process.

# The problem

- We couldn't just use 2D assets, since we wanted dynamic shadows, and that
  would have probably meant harder to implement click detection
- We didn't know how to 3D design, or really use blender

# The process

- in Gimp, generate a texture file, and a mask file
- in Inkscape, vectorize the mask
- in Blender import svg, convert into mesh, export into OBJ
- through a python script, add UV coordinates to the OBJ file
- import the obj in godot, and apply the texture to it

# Automating the process

- Generate the texture file and mask file using the Pillow library
  - Multiprocessing process pool to speed up the process
- Automate inkscape using the shell mode
  - Problems when trying to start multiple instances in parallel
- Automate blender using the shell mode

# Conclusion

possible improvements:
- Texture trimming
- Automated import in godot
- Speed up texture/mask generation using numpy
