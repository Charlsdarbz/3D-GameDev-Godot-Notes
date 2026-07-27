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
