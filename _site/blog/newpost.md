---
layout: post
tags: posts
title: Building the board for Iron Testament
summary: In order to create a level-designer-friendly board editor for my upcoming turn based strategy game, I set out to learn editor scripting and tools development.
image: board.png
date: 2024-07-27
---
<div class = "textspace">
<p><a href = "/projects/iron-testament" class="highlight underline">Iron Testament</a> is the first major project by <a href = "https://rat-economy.com" class="highlight underline">Rat Economy</a>, a studio I co-founded and where I work as programming lead. It is a turn-based strategy game where you play as the last human on Earth as they lead their band of fanatical robots to take back the planet for the forces of life. Inspired by games like XCOM and Into the Breach it features on a mixture tactical combat and team-management. </p>

<p>The first order of buisness when developing the prototype for Iron Testament was to create a board system. A board is made up of tiles (individual spaces on a grid) that will be made up of ground, objectives that need to be reached, and extract points for leaving a level. The board itself then needs to be able to contain all of the game tiles, find all tiles within a radius, and keep track of where units were on the board. </p>
<img class="rounded-2xl border border-gray-400 border-2 w-1/2 float-left mr-6" src = "/images/blog/tile-mat.gif">

<p> First I implemented a class to define a Tile. This is a simple class that defines the type of tile, the position, and helper functions to find its neighbours.</p>



<p class = ""> As art is still in development we are using different materials to signal different tile types. In order to avoid designers having to individually change each tile's material, I threw together a simple <a href = "https://learn.unity.com/tutorial/editor-scripting" class = "highlight underline">editor script</a>. This contains a simple override for OnInspectorGUI that keeps track of when the tiletype is changed, and if so it updates the tile to the correct material by calling a helper function on the Tile class itself.</p>

<p>
Next I needed to define a Board. This was a more complex class, but essentially is made up of a 2d array of Tiles with extra data to track currently selected tiles and what tile someone is hovering over. I also added helper functions to find all tiles within a radius (useful determining where a unit can move to later) and functions to get a Tile's data from position or vice-versa.</p>

<img class="rounded-2xl border border-gray-400 border-2 w-1/2 float-right ml-6" src = "/images/blog/board-inspector.png">
<p>However, a problem quickly became apparent with how I had set everything up: how was I going to connect the visual side of the level (the tile objects that level designers set up) with the code-representation of the level (the 2d array of Tiles in Board)? 

To do this I created another editor script, this time providing a custom inspector for the Board class. Below the default inspector elements, I added a button labeled "Save Level Data". This calls a function that loops through each possible position that a tile could be in (0,0) to (maxrows, maxcols) and checks if a tile is present, if so it adds it to a saved list of Tiles in BoardTools.cs. While finding the tiles, I also had this function do some setup of their data (saving their positions, ect) so no one would have to enter that manualy. While this function isn't incredibly efficient, because it is running only in the editor it will have no effect on the performance of the game.

When a level is loaded, the game will find the saved list of Tiles on BoardTools.cs and construct a 2d array according to the saved information. This allows us to have have all of the design of a level be done in the editor and with the save button the code-representation of that level to be automatically generated without any additional work.

I also added two buttons to spawn default and objective tiles just to eliminate the need to go searching for the correct prefab as well as a button that automatically generates a board of the maximum size to speed up the design process. The goofy little level I have pictured in the header of this article is created from that default map generator.
</p>

</div>