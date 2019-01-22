[Back](https://dhog10.github.io/portfolio/)

## Lua
I have scripted Lua for many years, Lua was my second language which I learned after Java. My experience scripting in Lua relates to the game Garry'sMod, creating various addons and gamemodes for the my game servers.

### Expanse
Expanse is my Garrysmod gamemode, set in space it sets to push the limits of the game beyond the Source engine's intended capabilities. I wanted to create a gamemode where the player could fly a space ship around in space, explore and travel across vast distances in space.
This project is very much unfinished, and has been a side project of mine for almost a year.

<video width="480" height="320" controls="controls">
  <source src="images/expanse/flight.mp4" type="video/mp4">
</video>
The source engine by default will only support coordinates from -16000 to 16000 (the space station in the video above is pretty much 16000 units wide), I overcame this obstacle by implementing my own coordinate system, which would use a sector combined with local coordinates to evaluate your global coordinates. Using two vectors to represent your global coordinates allowed me to expand the maximum potential location of objects to extreme limits, even beyond floating point imprecision. To have objects render in the correct location, I calculate the relative global coordinates between your player and the target. Essentially, rather than you moving through the universe, everything in the universe moves around you. (This also works in multiplayer)
<video width="480" height="320" controls="controls">
  <source src="images/expanse/flight.mp4" type="video/mp4">
</video>
The tactical map is inspired from Eve Online's tactical map view, it allows the player a strategic overview of their surroundings, and can be used to launch missiles and countermeasures.
