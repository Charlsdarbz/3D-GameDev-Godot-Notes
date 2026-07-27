<img width="2533" height="1024" alt="logo_large_color_light" src="https://github.com/user-attachments/assets/b97d692f-96d0-4782-91b0-831509561674" />
These are the notes of this lecture of the "Learn 3D game development step by step with Godot 4 by creating 5 complete projects."


# About
Building out a 3D Playground, Taking a look at what nodes are, What something called Resource are in Godot, explanation on what a scene is.

# A Tree of Nodes & How Scenes work (I think)

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="288" height="492" alt="image" src="https://github.com/user-attachments/assets/b1e4f77b-62ff-49f3-92bd-c018fe1034f8" />

The screenshot above is what's known as a tree of nodes and this tree of nodes is making up our scene. adding stuff like the Enviroment, Light, Objects, a Camera, ect.
The top node is what's known as the root node of our scene. and all the other nodes are what are known as children in this particular scene. And a scene is simply a collection ofthings that are saved into a file. When Godot runs our game, it loads up whatever scene we told it to run by default and then draws that on the screen. The things that we have inside the scene they're all nodes and each of the nodes have specific job. So the MeshInstance3D for example has the job of showing 3D shapes. The Camera3D has the job of allowing us to actually look into our world. DirectionalLight3D has the job of providing some light and so on. And that is how Godot works. You pick nodes based on what you need. You put them in the scene and Godot then does the rest. Later on, when making games you will start making multiple scenes and building those out according to the things that we need. For example, player scenes, pickup scenes, things like that. And we use those scenes inside other scenes then to build up our games.

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="1343" height="959" alt="image" src="https://github.com/user-attachments/assets/d7c65d58-ea83-407c-aae5-9c41e4bf80b8" />

# Node Naming

When Nodes are at the same level in the scene they must have Unique names and cannot be named the same.

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="285" height="190" alt="image" src="https://github.com/user-attachments/assets/47ca98c0-fe5a-4909-8225-cb488b2c8f5c" />

If you for example put Box2 inside another child node then it can have the same name as a node that isn't on the same level as it

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="281" height="169" alt="image" src="https://github.com/user-attachments/assets/0cf29864-6aa6-416a-bca9-c4e74d14f099" />
