---
layout: post
title: game assets with blender
---
With the release of the [cannons pack](https://opengameart.org/content/cannons-tank-pack),
a collection of 3d models used for [vax-albina](https://mess110.github.io/html-games/vax-albina/),
I wanted to share how I manage my assets.

For a game, I include all assets in a single blender file, each one being a different
object. This helps with view/scale consistency and makes managing the assets
easier.

I created a script to select each object in the blender file one by one and export
it as a separate glb file. The script can be changed to support any export format
known to blender.

```
#!/usr/bin/env python3

import bpy
import os
from time import sleep

def clear_selection():
    for obj in bpy.context.scene.objects:
        obj.select = False

def export_all_items():
    filepath = bpy.data.filepath
    outputFolder = os.path.dirname(filepath)

    objects = bpy.data.objects
    for object in objects:
        clear_selection()
        object.select = True
        object.location = (0, 0, 0)
        object.rotation_euler = (0, 0, 0)
        object.scale = (1, 1, 1)
        sleep(0.1)
        exportPath = "%s/%s.glb" % (outputFolder, object.name)
        bpy.ops.export_scene.glb(filepath=exportPath,
                                 export_selected=True,
                                 export_apply=True)
        sleep(0.1)

export_all_items()
bpy.ops.wm.quit_blender()
```

Save that as `export_all_glb.py` and run it with:

```
blender ../path_to.blend --python export_all_glb.py
```

This will export all the models in the directory you called the script. Now
they are ready to be used.

All the models I make are public domain and can be found on
[https://opengameart.org/](https://opengameart.org/)
