![logo_large_color_light](https://github.com/user-attachments/assets/b97d692f-96d0-4782-91b0-831509561674)

These are the notes of this lecture of the "Learn 3D Game Development Step by Step with Godot 4 by Creating 5 Complete Projects."

# About

Building out a 3D playground, taking a look at what nodes are, what resources are in Godot, and an explanation of what a scene is.

# A Tree of Nodes & How Scenes Work (I Think)

> ⚠️ These screenshots were taken in Godot 4.7.1 and may look different in newer versions.

![Tree of nodes](https://github.com/user-attachments/assets/b1e4f77b-62ff-49f3-92bd-c018fe1034f8)

The screenshot above shows what's known as a **tree of nodes**, and this tree of nodes makes up our scene. It contains things like the environment, lights, objects, a camera, etc.

The top node is known as the **root node** of the scene, and all the other nodes are its **children**.

A **scene** is simply a collection of things that are saved into a file. When Godot runs our game, it loads whichever scene we've set as the default and draws it on the screen.

Everything inside a scene is a **node**, and every node has a specific job:

- **MeshInstance3D** displays 3D models.
- **Camera3D** lets us view the world.
- **DirectionalLight3D** provides lighting.
- Other nodes each have their own specialised purpose.

This is the core idea behind Godot. You choose the nodes you need, place them into a scene, and Godot handles the rest.

As you build larger games, you'll create many different scenes—for example:

- Player scenes
- Pickup scenes
- Enemy scenes
- UI scenes

These scenes can then be reused inside other scenes to build your game.

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![Scene example](https://github.com/user-attachments/assets/d7c65d58-ea83-407c-aae5-9c41e4bf80b8)

# Node Naming

Nodes that share the same parent (i.e. are on the same level in the scene tree) **must have unique names**. Two sibling nodes cannot have the same name.

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![Unique sibling names](https://github.com/user-attachments/assets/47ca98c0-fe5a-4909-8225-cb488b2c8f5c)

However, if you place `Box2` inside another child node, it **can** have the same name as another node elsewhere in the tree, because they no longer share the same parent.

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![Duplicate names in different branches](https://github.com/user-attachments/assets/0cf29864-6aa6-416a-bca9-c4e74d14f099)


# Nodes & Resources (This is Mostly anontation of the Lecture but modified abit to be in my own words)
So while the nodes are the building blocks of games in Godot, resource provide the data for our nodes to be able to work. So for example when we're looking at our mesh instance 3D, the mesh that we're assigning in the inspector, it's actually a resource. It contains the data of that mesh. And the data of that mesh is then used by the MeshInstance3D to display the 3D shape on the screen. As you'll see, as well as many nodes, we have many types of resources. For example, we have a node to play sound well that uses resources which are Sound files a few other examples are Collision dectection Nodes and those also will have resources like the collision shape data. another one is Label Settings for the colors and fonts of labels and things like that. theres also one that is very common and that is textures when you want to display images. Those are resources, they're pieces of data that are then used by nodes, in that case to display an image. And the thing about resources is Godot reuses resources where possible this can be an issue when you have to Nodes for example MeshInstance3D and you duplicate them Godot will use the same resource ID this can cause issues because you'll see when scaling a object with the same ID as another of the same type it will scale that other object also. This is because Godot doesn't create Unique Copys of them. Being brand new to all of this, that sounds a little bit odd. Why would you do that? But if you think of the situation, say where you've got, a game where you're showing sprites in 2D and those sprites are bullets, let's say, have a texture. Let's say you're going to have 1,000 bullets on the screen. Well when you load a texture that goes into the GPU memory, that would make little sense to load the same texture 1,000 times into the GPU memory. You'd quickly run out of memory. So instead what you do is load it once then reuse it as you need to draw it on the screen for that 1,000 times. That is reusing of a resource. By default, any resource that we use in Godot gets reused rather than copied. now say you have 2 objects both MeshInstance3D for example the mesh of that MeshInstance3D is a resource and the same resource is being used on for example Box2. So if we modify the resource like the z-axis scale the same changes will apply to Box1 because they are both using the same resource. Now you probally thinking. Does that mean I'mnow restricted to every box mesh being the same size in the entire game?. Ofcourse not. But to understand how to change it, we need to understand actually how the resource is being loaded and where they live. so with Box2 selected, if we scroll down you'll find a resource section. And if you click the drop down arrow you'll find a path, Now if you hover of the path you'll see the path is to the actual resource data. Now, a texture would normally be in a file. In this case we haven't made a file for this resource data. So the data is actually embedded in our scene file. So you can see that we have movementsdemo.tscn, that's our scene file, then a double colon and there's an ID there which is defined for this particular resource. that is BoxMesh_u2d4l in this case. That's where our resource data is living. If we select Box and go to the mesh and go all the way down to resources and the path and hover, we can see it's exactly the same resource. If you open your scene in file explorer and then drag it into a text editor like Sublime Text, VS Code, Anything other than Microsoft Notepad because Notepad claims to be a Text Edtior but it isn't yes it allows you to edit text but it also inserts hidden charectors and causes issues with files like this so DO NOT USE IT for viewing files in Godot what you'll want to do is drag your scene into a text editor or open it in one in this case mine is movements_demo.tscn And now you should be able to see the actual contents of the file and the contents are readable text for us. Inside here is the entire structure of the scene that you've been building. Although it may look at first glance really complicated it actually isn't at the top you will see the definition of your scene and it's given a unique ID, which is a unique reference to this scene that Godot will use internally to be able to find it when we need to use it. And then we have sub-resources. So sub-resources are resources They're data containters used by nodes. A sub-resource is a resource where the data is defined in the scene itself. As mentioned already textures, for example, are often files. That will be something known as an external resource. as you will see we have sub-resources where the data is defined inside here like this. There's no point in occupying space with more imformation that we don't need to.

```tscn
[sub_resource type="Environment" id="Environment_t4iy8"]
background_mode = 2
sky = SubResource("Sky_l88sr")
glow_enabled = true
```

and if we look abit further down you will be able to see your BoxMesh resource for example and its ID and you'll notice there is not data which is a little bit odd. We can see our plane mesh that has some data the size is 10x10, in the Box mesh we don't have anything. So why is that?. Well at the moment, our resource, if we go back into Godot and select the box and scroll up a bit on the mesh, you'll notice we haven't changed anything from the default values that came with this. When you save a resource, Godot will only save the values you've changed. It already knows by default what the default values are. It only ever saves values if they've changed from the default values. So for example, if you get a hold of the Z on the size, make that 2 and you Control-S to save to embed that change. And you go back into your text editor, You will now see that for the box mesh, you've actually got the Vector3 size there. So that is our resource. That's our piece of data. If you scroll down abit and look at the box nodes that are setup you'll notice they are setup to use exactly the same resource. And that's why if we go and change some data on one of the boxes, it's reflected in both of those nodes because both of them are using the same resource.


```tscn


[sub_resource type="PlaneMesh" id="PlaneMesh_u2d4l"]
size = Vector2(10, 10)

[sub_resource type="BoxMesh" id="BoxMesh_u2d4l"]

```

Same sub-resource
```tscn

[node name="Box" type="MeshInstance3D" parent="." unique_id=1566873264]
transform = Transform3D(1, 0, 0, 0, 1, 0, 0, 0, 1, 3.6199627, 0.38542938, -4.304199)
mesh = SubResource("BoxMesh_u2d4l")

[node name="Box2" type="MeshInstance3D" parent="." unique_id=1985232165]
transform = Transform3D(1, 0, 0, 0, 1, 0, 0, 0, 1, -4.0725884, 0.43287396, 4.224799)
mesh = SubResource("BoxMesh_u2d4l")

```
> ⚠️ This section is currently Incomplete as I've been at my Computre too long writting this and I'm getting a headache

So now that you understand all of that hopefully you are probally wondering, So how do you get around this problem of wanting a diffrent size box?
But what you need to do is use a diffrent resource and there are various ways of doing that. Lets select Box2 and scroll up in the Inspector click the drop down around on where it says Mesh and Click the make Unique button close to the bottom of the drop down menu. Now click Control-S to save to embed this data into the Scene. If you don't do that, it'll exist unique in the memory, but it won't be updated in the scene file yet. So Conrtol-S to save is updated in the scene file. And if you go back to the scene file, You can see now that Box2 is using a diffrent resource. So we've now got two Box Mesh resource which are diffrent. So back in Godot if you change the Z axis on the scale now you'll see that it's changed on its own and not changing the other box. And to complete this, what you should do is actually save this resource to file. by clicking the drop down arrow where it says Mesh again in the Inspector with Box not Box2 Selected and go and click Save As. and go up one level in the Godot file manager by click the arrow poiting up where is says Path make a new folder called ``resources`` and go into there and save your Resource. and name it whatever just something like ``box_mesh_1m`` 1m = 1 Meter And if we go down the right-hand side and look at the path it's no longer embedded in the scene. The data for this resource is now saved in this file, wthich is the box_mesh_1m.tres



> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![Mesh](https://github.com/user-attachments/assets/0b4d2ec4-7a37-4135-8996-21498b8d1085)

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![SameID1](https://github.com/user-attachments/assets/9d2e84a6-3fe1-4b08-b215-54fa9b0374f7)

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![SameID2](https://github.com/user-attachments/assets/4cdddd53-1da2-46d3-b57a-a7715cf82002)

