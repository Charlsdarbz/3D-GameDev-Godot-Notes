![logo_large_color_light](https://github.com/user-attachments/assets/b97d692f-96d0-4782-91b0-831509561674)

These are the notes of this lecture of "Learn 3D Game Development Step by Step with Godot 4 by Creating 5 Complete Projects."

> Grammar and Spacing fixed by Claude


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

As you build larger games, you'll create many different scenes, for example:

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

# Nodes & Resources

> This is mostly annotation of the lecture, but modified a bit to be in my own words.

While nodes are the building blocks of games in Godot, resources provide the data for our nodes to be able to work.

So, for example, when we're looking at our MeshInstance3D, the mesh that we're assigning in the inspector is actually a resource. It contains the data of that mesh, and that data is then used by the MeshInstance3D to display the 3D shape on the screen.

As you'll see, as well as many nodes, we have many types of resources. For example:

- We have a node to play sound, which uses resources that are sound files.
- Collision detection nodes have resources like the collision shape data.
- Label Settings hold the colours and fonts of labels and things like that.
- Textures are very common. When you want to display images, those are resources too.
These are all pieces of data that are then used by nodes (in the last case, to display an image).

## Resource Reuse

The thing about resources is that Godot reuses them where possible.

This can be an issue. For example, when you have two nodes, say two MeshInstance3D nodes, and you duplicate them, Godot will use the same resource ID. This can cause problems, because when scaling an object that shares the same ID as another of the same type, it will scale that other object too. This happens because Godot doesn't create unique copies of them.

Being brand new to all of this, that sounds a little odd. Why would you do that?

But if you think about the situation. Say you've got a game showing sprites in 2D, and those sprites are bullets with a texture. Let's say you're going to have 1,000 bullets on the screen. When you load a texture, it goes into the GPU memory. It would make little sense to load the same texture 1,000 times into GPU memory. You'd quickly run out of memory. So instead, you load it once and then reuse it as you need to draw it on the screen for those 1,000 times. That is reusing of a resource.

By default, any resource that we use in Godot gets reused rather than copied.

Now say you have two objects, both MeshInstance3D. The mesh of that MeshInstance3D is a resource, and the same resource is being used on, for example, `Box2`. So if we modify the resource, like the z-axis scale, the same change will apply to `Box1`, because they are both using the same resource.

Now you're probably thinking: does that mean I'm now restricted to every box mesh being the same size in the entire game? Of course not.

## Where Resources Live

But to understand how to change it, we need to understand how the resource is actually being loaded and where they live.

With `Box2` selected, if we scroll down, you'll find a resource section. If you click the dropdown arrow, you'll find a path. Now, if you hover over the path, you'll see it points to the actual resource data.

A texture would normally be in a file. In this case, we haven't made a file for this resource data, so the data is actually embedded in our scene file.

So you can see that we have `movementsdemo.tscn`, that's our scene file, then a double colon, and then an ID defined for this particular resource. That is `BoxMesh_u2d4l` in this case. That's where our resource data is living.

If we select `Box`, go to the mesh, go all the way down to the resource path, and hover, we can see it's exactly the same resource.

## Reading the Scene File

If you open your scene in file explorer and then drag it into a text editor like Sublime Text or VS Code, anything other than Microsoft Notepad, you can view the raw contents.

> ⚠️ Do NOT use Notepad. It claims to be a text editor, but while it does let you edit text, it also inserts hidden characters and causes issues with files like this. So don't use it for viewing Godot files.

In this case, mine is `movements_demo.tscn`. Once open, you should be able to see the actual contents of the file, and the contents are readable text.

Inside here is the entire structure of the scene you've been building. Although it may look really complicated at first glance, it actually isn't.

At the top, you'll see the definition of your scene. It's given a unique ID, which is a unique reference to this scene that Godot uses internally to find it when needed.

## Sub-Resources

Then we have sub-resources. Sub-resources are resources, data containers used by nodes, where the data is defined in the scene itself.

As mentioned already, textures are often files. That will be something known as an **external resource**. But we also have **sub-resources**, where the data is defined inside the scene like this. There's no point occupying space with more information than we need to.

```tscn
[sub_resource type="Environment" id="Environment_t4iy8"]
background_mode = 2
sky = SubResource("Sky_l88sr")
glow_enabled = true
```

If we look a bit further down, you'll be able to see your `BoxMesh` resource and its ID, and you'll notice there is no data, which is a little odd.

We can see our plane mesh has some data (the size is 10x10), but the box mesh doesn't have anything. So why is that?

At the moment, if we go back into Godot, select the box, and scroll up a bit on the mesh, you'll notice we haven't changed anything from the default values that came with it.

When you save a resource, Godot only saves the values you've changed. It already knows the default values, so it only ever saves values if they've changed from the defaults.

So, for example, if you grab the Z on the size, make it `2`, and press Control-S to embed that change, then go back into your text editor, you'll now see that the box mesh has a Vector3 size there.

That is our resource. That's our piece of data.

If you scroll down a bit and look at the box nodes that are set up, you'll notice they use exactly the same resource. That's why, if we change some data on one of the boxes, it's reflected in both nodes, because both are using the same resource.

```tscn
[sub_resource type="PlaneMesh" id="PlaneMesh_u2d4l"]
size = Vector2(10, 10)

[sub_resource type="BoxMesh" id="BoxMesh_u2d4l"]
```

Same sub-resource:

```tscn
[node name="Box" type="MeshInstance3D" parent="." unique_id=1566873264]
transform = Transform3D(1, 0, 0, 0, 1, 0, 0, 0, 1, 3.6199627, 0.38542938, -4.304199)
mesh = SubResource("BoxMesh_u2d4l")

[node name="Box2" type="MeshInstance3D" parent="." unique_id=1985232165]
transform = Transform3D(1, 0, 0, 0, 1, 0, 0, 0, 1, -4.0725884, 0.43287396, 4.224799)
mesh = SubResource("BoxMesh_u2d4l")
```

> ⚠️ This section is currently incomplete, as I've been at my computer too long writing this and I'm getting a headache.

## Making a Resource Unique

So now that you understand all of that, you're probably wondering: how do you get around this problem of wanting a different-sized box?

What you need to do is use a different resource, and there are various ways of doing that.

Let's select `Box2` and scroll up in the Inspector. Click the dropdown arrow where it says Mesh, and click the **Make Unique** button close to the bottom of the dropdown menu.

Now press Control-S to save and embed this data into the scene. If you don't do that, it'll exist uniquely in memory, but it won't be updated in the scene file yet. So Control-S saves it to the scene file.

If you go back to the scene file, you can see now that `Box2` is using a different resource. So we've now got two box mesh resources, which are different.

Back in Godot, if you change the Z axis on the scale now, you'll see it changes on its own and doesn't change the other box.

## Saving a Resource to File

To complete this, you should actually save this resource to a file.

Click the dropdown arrow where it says Mesh in the Inspector, this time with `Box` (not `Box2`) selected, and click **Save As**.

Go up one level in the Godot file manager by clicking the up arrow where it says Path. Make a new folder called `resources`, go into it, and save your resource. Name it something like `box_mesh_1m` (`1m` = 1 metre).

If we look down the right-hand side at the path, it's no longer embedded in the scene. The data for this resource is now saved in this file: `box_mesh_1m.tres`.

The `.tres` extension tells Godot to save the resource data as text that we can read.

An alternative is to save it as a `.res`. If you do that, it won't be readable text. It'll be compressed into Godot's internal binary format, which is much smaller.

- **Text (`.tres`):** the benefit is that you can read it if you need to.
- **Binary (`.res`):** the benefit is that it's a lot smaller, faster to load, and smaller on disk.
Generally, if you've got really large terrains and things like that, you might want to save the meshes as `.res` files.

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![Mesh](https://github.com/user-attachments/assets/0b4d2ec4-7a37-4135-8996-21498b8d1085)

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![SameID1](https://github.com/user-attachments/assets/9d2e84a6-3fe1-4b08-b215-54fa9b0374f7)

> ⚠️ This screenshot was taken in Godot 4.7.1 and may look different in newer versions.

![SameID2](https://github.com/user-attachments/assets/4cdddd53-1da2-46d3-b57a-a7715cf82002)
