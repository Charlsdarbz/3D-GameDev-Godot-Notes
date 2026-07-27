<img width="2533" height="1024" alt="logo_large_color_light" src="https://github.com/user-attachments/assets/b97d692f-96d0-4782-91b0-831509561674" />
These are the notes of this lecture of the "Learn 3D game development step by step with Godot 4 by creating 5 complete projects."

# 3D View Controls
Orbiting - Holding down middle mouse button
Panning - Shift + Holding down middle mouse button
Zooming - Ctrl + minus for zooming out and Ctrl + plus for zooming in can also use scroll wheel (really simple)

# Tips from lecture
When working with large maps, ect orbiting or zooming in around a certain object because it's hard for Godot to know what we want to orbit or zoom-in/out on so it can some times be difficult. to fix this select the Object you want to orbit and stuff around ect make sure you mouse is over the 3D view and Click ``Crtl + F`` and then when panning, ect it will focus on that point / objects location 

# Diffrent Views
To change your View you can click the ``: Perspective View`` in the top left corner of the 3D view 
Perspective is where we're looking at 3D with Perspective which means there's depth perception meaning so the further the away things are the smaller they get. if you click on the  ``: Perspective View`` Button like shown in the image below and scroll up if you select orthogonal an Orthogonal 3D is where you see things in 3D but without any depth perception. an example that uses orthogonal 3D view is the First 3D Game Example on the Godot docs. it will not be used for any games in the course that I'm taking notes on.

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="1339" height="951" alt="image" src="https://github.com/user-attachments/assets/274eff7f-a2f4-46ae-92b2-3230ca585425" />

Another intresting view is Wireframe the Wireframe view shows the meshes themselves without the faces of the objects drawn this makes it easier to see how many verticies a shape / object has. verticies are the points that are connected by edges the triangles that you will see while in the wirteframe perspective on where the faces would be those are what make up the faces.

- V = Verticies
- E = Edges
- F = Faces

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="1330" height="966" alt="image" src="https://github.com/user-attachments/assets/79cf97a9-145b-4413-bf91-ca563e09adbe" />

Another good View is Overdraw it enables a kind of like x-ray vision with your shapes with single colors and this is pretty good when you're lining things up and you've lost a collision shape

⚠️ This screenshot was taken in Godot 4.7.1 and may be different in newer versions.
<img width="1335" height="958" alt="image" src="https://github.com/user-attachments/assets/faa76ca3-672a-47f8-ae90-a03154ad7b0e" />


Some other views we we'll be using a lot are viewing from the top, the bottom, the side and so on. if you click the ``: Perspective View`` in the top left corner of the 3D view again you'll see there's top view, bottom view, left, right, front and rear to get these to work you need to make sure you mouse is in the 3D view

<img width="1384" height="957" alt="image" src="https://github.com/user-attachments/assets/4742fe71-0c53-43f6-9101-8edc3f824078" />

# Default keybinds for changing to your top, bottom, left, right, views ect.

<img width="418" height="164" alt="image" src="https://github.com/user-attachments/assets/224d29fb-f19b-4b76-b176-c795d557145e" />




