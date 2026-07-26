Godot Games are built out of scenes think of it like a container we put things in and the things we put in there are what we see on the screen

# Scenes and Nodes Explanation
how scenes are containers of things Nodes are the things they are containing nodes can be thought of as building blocks for our applications. And Godot has hundereds of diffrent nodes and each node has a certain kind of functionality. It has a sort of job to do that might be playing sound, displaying a texture. In the case of the Mesh3D Node this one displays 3D shapes.

# Mesh Instace 3D
The Mesh Instance 3D has a load of properties, though, and one of the key properties is a Mesh Property. So a Mesh is some data that's used by the Mesh Instance 3D to tell it what shapes it needs to draw on the screen.
to give a MeshInstance3D a shape click the Drop down arrow in the Inspector (The thing that holds all the propeties of the MeshInstance3D Node) and Left Click the PlaneMesh Option in the Drop down menu the PlaneMesh thing is Some data to show basically a 2D flat plane.

# Buttons to enter a scene or something.
In the Godot UI there are 3 Buttons that have to do with running scenes:
  1. Run Project (Shortcut: F5)
  2. Run Current Scene (Shortcut: F6)
  3. Run Specific Scene (Shortcut: Ctrl+Shift+F5)

Run Project - runs the Main Scene of the Project
Run Current Scene - Plays the currently Edited Scene that is open in the view
Run Specific Scene - Plays a Specific selected Scene, this can be useful for if you want to just spawn in at a certain level (If you have multiple levels)

These buttons can be located in the top-right of the Godot UI and will look like these in Godot

 ⚠️ this screen shot was taken in Godot 4.7.1 and may be diffrent in newer versions
<img width="260" height="93" alt="image" src="https://github.com/user-attachments/assets/83be6cf3-e06e-4f87-ae92-d5b7e317c1e6" />


# Setting up a Camera, Enviroment & Light

The functionallity of the camera is to allow us to view our world 
the camera is also a node called Camera3D so we are going to add to our scene as a node.
then on the right you can see a preview of what our scene looks like through the camera and if you have added any MeshInstance3D Nodes you will beable to see them their if you can't then there will be a button called ``: Perspective`` and if you click that with your Camera3D selected and then click Align Transform with View this will make it so where you are currently looking in your scene it will move the camera to your exact Coordinates
then you want to run your scene, once you have done that you will notice that your platform is grayish color and the enviroment is also a diffrent color (i forgot which color it will be or what it will look like) but to fix this first close out of the debug screen thing and you will see 2 icons at the top of your screen in the toolbar they will look like a sun (or in others words a filled circle with lines comming out of it) and a Globe (or in other words a orb with lines crossing over each other)

these will be blue for you if enabled (will be enabled by default)

⚠️ this screen shot was taken in Godot 4.7.1 and may be diffrent in newer versions
<img width="1330" height="964" alt="image" src="https://github.com/user-attachments/assets/74b8c084-3e25-41c9-a0d1-904d0c08e23c" />

these are your light and enviroment the light one acts as a sun and the enviroment one is what adds like the the blending the the sky and like adds a feel of enviroment and the sun makes it so the objects actually have color and aren't just grey. but now since these are just for preview currently but now we needs to actually add theses as nodes so they can actually be seen when we run our application
Now, luckily, there's a shortcut to doing that.

First left click on your main node aka the parent node (I think/guessing)
then click the 3 dots to the right of the enviroment button thing 

⚠️ this screen shot was taken in Godot 4.7.1 and may be diffrent in newer versions
<img width="140" height="76" alt="image" src="https://github.com/user-attachments/assets/b8431f82-1059-4b6d-8e2f-aef7c3126572" />

once in the menu we will have a couple of options here one being called Add Sun to Scene and the other being called Add Enviroment to Scene So let's click on the add the sun to the scene. And you can see we get what's known as a DirectionalLight3D node in the Scene Hierencey (i spelt this wrong but you get what i mean probally)
this is for Directional Light. so after adding that click the same 3 dots and then Click Add Enviroment to Scene and then again we get another Node whose job is to provide the Enviroment for the Scene and by default, the enviroment has a sort of muddy floor and a sort of light grey sky with a bit of blending in the background.
now if we run the application we now should see  our floor now with our enviroment,

# Naming Conventions
<img width="724" height="506" alt="image" src="https://github.com/user-attachments/assets/6765b3cc-3dc2-4983-97a1-15c9e9e18c0e" />


