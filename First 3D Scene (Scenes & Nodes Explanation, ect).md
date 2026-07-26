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

⚠️ this screen shot was taken in Godot 4.7 and may be diffrent in newer versions
   <img width="260" height="93" alt="image" src="https://github.com/user-attachments/assets/83be6cf3-e06e-4f87-ae92-d5b7e317c1e6" />


# Setting up a Camera

