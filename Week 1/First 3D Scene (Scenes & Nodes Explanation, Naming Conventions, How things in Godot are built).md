<img width="2533" height="1024" alt="logo_large_color_light" src="https://github.com/user-attachments/assets/b97d692f-96d0-4782-91b0-831509561674" />
These are the notes of this lecture of the "Learn 3D game development step by step with Godot 4 by creating 5 complete projects."


----------------------------------------
-# grammar and formating fixed by claude
----------------------------------------

## The lecture
https://www.udemy.com/course/complete-3d-godot-4-game-development-course/learn/lecture/55988743#overview
 
## The course
https://www.udemy.com/course/complete-3d-godot-4-game-development-course/?couponCode=25BBPMXINACTIVE
 
# How Godot Games Are Built
Godot games are built out of scenes. Think of a scene like a container we put things in, and the things we put in there are what we see on the screen.
 
# Scenes and Nodes Explanation
Scenes are containers of things, and nodes are the things they are containing. Nodes can be thought of as building blocks for our applications. Godot has hundreds of different nodes, and each node has a certain kind of functionality. It has a sort of job to do that might be playing sound or displaying a texture. In the case of the Mesh3D node, this one displays 3D shapes.
 
# Mesh Instance 3D
The Mesh Instance 3D has a load of properties, though, and one of the key properties is a Mesh property. A Mesh is some data that's used by the Mesh Instance 3D to tell it what shapes it needs to draw on the screen.
 
To give a MeshInstance3D a shape, click the dropdown arrow in the Inspector (the thing that holds all the properties of the MeshInstance3D node) and left click the PlaneMesh option in the dropdown menu. The PlaneMesh is some data to show basically a 2D flat plane.
 
# Buttons to Enter a Scene
In the Godot UI there are 3 buttons that have to do with running scenes:
  1. Run Project (Shortcut: F5)
  2. Run Current Scene (Shortcut: F6)
  3. Run Specific Scene (Shortcut: Ctrl+Shift+F5)
Run Project - runs the Main Scene of the project.
Run Current Scene - plays the currently edited scene that is open in the view.
Run Specific Scene - plays a specific selected scene. This can be useful if you want to just spawn in at a certain level (if you have multiple levels).
 
These buttons can be located in the top-right of the Godot UI and will look like these in Godot.
 
 ⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="260" height="93" alt="image" src="https://github.com/user-attachments/assets/83be6cf3-e06e-4f87-ae92-d5b7e317c1e6" />
 
 
# Setting Up a Camera, Environment & Light
 
The functionality of the camera is to allow us to view our world. The camera is also a node, called Camera3D, so we are going to add it to our scene as a node.
 
Then on the right you can see a preview of what our scene looks like through the camera, and if you have added any MeshInstance3D nodes you will be able to see them there. If you can't, then there will be a button called `: Perspective`, and if you click that with your Camera3D selected and then click Align Transform with View, this will make it so wherever you are currently looking in your scene, it will move the camera to your exact coordinates.
 
Then you want to run your scene. Once you have done that, you will notice that your platform is a grayish color and the environment is also a different color (I forgot which color it will be or what it will look like). But to fix this, first close out of the debug screen thing and you will see 2 icons at the top of your screen in the toolbar. They will look like a sun (or in other words, a filled circle with lines coming out of it) and a globe (or in other words, an orb with lines crossing over each other).
 
These will be blue for you if enabled (they will be enabled by default).
 
⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="1330" height="964" alt="image" src="https://github.com/user-attachments/assets/74b8c084-3e25-41c9-a0d1-904d0c08e23c" />
 
These are your light and environment. The light one acts as a sun, and the environment one is what adds the blending, the sky, and a feel of environment. The sun makes it so the objects actually have color and aren't just grey. But these are just for preview currently, so now we need to actually add these as nodes so they can actually be seen when we run our application.
 
Now, luckily, there's a shortcut to doing that.
 
First, left click on your main node, aka the parent node (I think/guessing).
Then click the 3 dots to the right of the environment button thing.
 
⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="140" height="76" alt="image" src="https://github.com/user-attachments/assets/b8431f82-1059-4b6d-8e2f-aef7c3126572" />
 
Once in the menu, we will have a couple of options here, one being called Add Sun to Scene and the other being called Add Environment to Scene. So let's click on Add Sun to Scene. You can see we get what's known as a DirectionalLight3D node in the Scene Hierarchy (I spelt this wrong but you get what I mean, probably).
 
This is for directional light. So after adding that, click the same 3 dots and then click Add Environment to Scene, and again we get another node whose job is to provide the environment for the scene. By default, the environment has a sort of muddy floor and a sort of light grey sky with a bit of blending in the background.
 
Now if we run the application, we should see our floor now with our environment.
 
# Naming Conventions
<img width="724" height="506" alt="image" src="https://github.com/user-attachments/assets/6765b3cc-3dc2-4983-97a1-15c9e9e18c0e" />
 
# Challenge Provided by the Udemy Course
Add a new mesh...
Can you add a MeshInstance3D with a BoxMesh?
 
I completed this challenge pretty much instantly. All you have to do is add another MeshInstance3D, and instead of setting the Mesh to PlaneMesh, I set it to BoxMesh and moved it up a little bit! And instead of keeping both of them named MeshInstance3D and MeshInstance3D2, I changed the PlaneMesh one to be called PlaneMeshInstance3D and the BoxMesh one to be called BoxMeshInstance3D.
