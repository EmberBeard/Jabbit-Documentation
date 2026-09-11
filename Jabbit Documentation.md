# Jabbit Documentation

## Introduction

Thanks for purchasing the Jabbit. Here's the full technical documentation for your avatar and associated files. If you wish to stay up to date with the latest version of this documentation it can be found and read here: https://github.com/EmberBeard/Jabbit-Documentation/tree/main

## Table of contents

1. [Introduction](##Introduction)

2. [Blender files](##Blenderfiles)

3. [Substance Painter files](##SubstancePainterfiles)

4. [Unity](##Unity)

## Blender files

You should have 4 blender files.

- Jabbit.blend
- Jabbit-Quest.blend
- RaveWare.blend
- RaveWare-Quest.blend

Before openning and using any of these files, if you happen to be a content creator and wish to either make clothes of this avatar or alter the facial blend shapes, I recommend you install Ember's Toolbox into blender3D, which is available here: https://github.com/EmberBeard/EmbersBlenderToolbox - a copy of this should have been provided with the purchase though, incase this page were to ever be taken down.

If you're just a regular user, then the files should be pretty straight forward and self explainatory. They each contain just the mesh labelled on the file and acompanying skeleton. The extra generator categories in the scene outliner and rig shapes you can ignore. Hence forth, this documentation will explain the intricacies of these files some of the finer details of these files.

All blendshapes for the Jabbit have been generated using rigs instead of sculpted. In the animation timeline there should be a series of markers that denote what shapes they correlate to. If you were to unhide the generator cateogries, you'll see a set of animation rigs. 



### Exporting from blender!

This sadly isn't covered enough so I'll reiterate it here. When you're ready to export your avatar from blender for Unity, these are the settings you should use. Select what you want then go up to the top left in blender. Click File > Export > FBX. These are the settings you should make sure are configured correctly:



Apply Scalings is the extremely important one. The FBX scaling system sadly is not followed universally across the 3D industry and blender defaults to what is a happy middle ground for most software but isn't strictly correct according to spec. "FBX All" is what it should be for your avatar to be correctly scaled in unity. If you leave it as default, check the size of the skeleton when you're next in unity and it should be 100 on all axis. This is wrong, it should be at a scale of 1 on all axis!



## Substance Painter files

### Exporting from Substance Painter and materials in Unity

To get the nice shading effect you see on the default Jabbit - you can't use the "realistic" render mode on Poiyomi. Instead we recommend the "Wrapped" shading method with a provided smootheness map. There's a key advantage to this which is that - when the avatar has a bit of relfectivity that's toned and managed well, instead of looking like a mirror they just naturally catch and integrate well with the lighting of the environment around them - because they are reflective - just very subtly. Here's a walk through for how to do this yourself not just with the Jabbit but with any other avatar you like in theory. However, this process starts all the way back in Substance painter before we get to Unity. Here's what you need to do after you've textured your Jabbit or other avatar:

1. Go to https://www.poiyomi.com/general/substance-painter - there should be a downloader for a substance painter export template. Go and download that.

2. Drag it from your downloads folder into your Substance Painter Assets window

3. Export your textures using the "Unity Poiyomi" tempalte you have installed. This will give you a "MetalicSmoothnessMap".

4. In Unity now, once you've dragged your textures in there, make your material for your avatar and set it to be a "poiyomi toon" shader.

5. Under "Color & Normals" set your Albedo texture

6. Under "Shading -> Shading" change the lighting type to "Wrapped", then;
   
   1. set the Wrap value to 1.
   
   2. set the Normalization value to 0.3.

7. Enable the "Shading -> Reflections & Specular" section. Inside here you'll want to find the "Packed Maps" section. Open the dropdown and you should see a whole list of settings. What we want to do now is set our "MetalicSmoothnessMap" to be the texture used in the following 3 slots:
   
   1. R Metalic Map
   
   2. G Smoothness Map
   
   3. B Reflection Mask

8. After setting these 3 texture slots, make sure to change the fallback dropdown on the right of them from "MAX" to R, G and B respectively. This way it will sample the Metalic value from the R channel, Smoothness from G and Reflection from B.

9. Then just hit the "Confirm Merge" button. Poiyomi will take all that data and generate a new texture next to your material calle dthe Material Name_MochieMetallicMaps. More on this later.

10. The last step is to go below this "Packed Maps" section and to the "Reflection Visiblity" slider - turn that up all the way to 1.

You should now have a material that integrates your avatar very nicely into whatever lighting condition you find yourself in with a subtle reflection trick. A word of caution though: Do NOT delete the generated texture, it is used by the material.

## Unity

### Pre-requisits

Before openning the project in Unity, you will require the following packages - for the ones you will need to downloaded it is recommended you click the "Add to VCC" button to integrate them into the VRChat Creator Companion tool. This way updates can be easily re-integrated:

| Module                                                                                                                                                             | Version number (minimum) | Download links                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------ | ------------------------------------------------------ |
| **Av3 Emulator**<br/><br/>(this allows you to test in editor)                                                                                                      | 3.413                    | NA (Curated in the Companion app)                      |
| **Poiyomi Toon Shader**<br/><br/>(this allows for better shading in game)                                                                                          | 10.0.16                  | https://www.poiyomi.com/download                       |
| **VRCFury**<br/><br/>(this is a core set of additional logic that<br/>allows things to easily plug together in editor)                                             | 1.1426                   | https://vrcfury.com/download                           |
| **Audio link**<br/><br/>You will get this anyway for free in game but<br/>this package allows you to preview and effectively<br/>tweak your work in editor         | 3.12                     | NA (Curated in the Companion app)                      |
| **VRCFT - Jerry's Templates**<br/><br/>(This is the default face tracking control<br/>system used and supported - but Pawligon<br/>should also work if you prefer) | 7.0.5                    | https://adjerry91.github.io/VRCFaceTracking-Templates/ |
