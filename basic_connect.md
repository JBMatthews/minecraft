# Connection
Getting Started with Minecraft Pi

Minecraft is a popular sandbox open-world building game. A free version of Minecraft is available for the Raspberry Pi; it also comes with a programming interface. This means you students can write commands and scripts in Python code to build things in the game automatically and it’s a great way to learn Python!

Open Python 3 from the application menu and move the windows so they’re side-by-side.

You can either type commands directly into the Python window or create a file so you can save your code and run it again another time.

If you want create a file, go to File > New window and File > Save. You’ll probably want to save this in your home folder or a new project folder.

Start by importing the Minecraft library, creating a connection to the game and testing it by posting the message “Hello world” to the screen:

from mcpi.minecraft import Minecraft

mc = Minecraft.create()

mc.postToChat("Hello world")

If you’re entering commands directly into the Python window, just hit Enter after each line. If it’s a file, save with Ctrl + S and run with F5. When your code runs, you should see your message on screen in the game.

Find your location

To find your location, type:

pos = mc.player.getPos()

pos now contains your location; access each part of the set of coordinates with pos.x, pos.y and pos.z.

Alternatively, a nice way to get the coordinates into separate variables is to use Python’s unpacking technique:

x, y, z = mc.player.getPos()

Now x, y, and z contain each part of your position coordinates. x and z are the walking directions (forward/back and left/right) and y is up/down.

 

Note that getPos() returns the location of the player at the time, and if you move position you have to call the function again or use the stored location.

 

Teleport

As well as finding out your current location you can specify a particular location to teleport to.

 

x, y, z = mc.player.getPos()

mc.player.setPos(x, y+100, z)

This will transport your player to 100 spaces in the air. This will mean you’ll teleport to the middle of the sky and fall straight back down to where you started.

 

Try teleporting to somewhere else!

 

Set block

You can place a single block at a given set of coordinates with mc.setBlock():

 

x, y, z = mc.player.getPos()

mc.setBlock(x+1, y, z, 1)

Now a stone block should appear beside where you’re standing. If it’s not immediately in front of you it may be beside or behind you. Return to the Minecraft window and use the mouse to spin around on the spot until you see a grey block directly in front of you.

The arguments passed to set block are x, y, z and id. The (x, y, z) refers to the position in the world (we specified one block away from where the player is standing with x + 1) and the id refers to the type of block we’d like to place. 1 is stone.

 

Other blocks you can try:

 

Air: 0

Grass: 2

Dirt: 3

Now with the block in sight, try changing it to something else:

 

mc.setBlock(x+1, y, z, 2)

