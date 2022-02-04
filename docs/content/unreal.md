# Unreal XR Content Guide
<!-- <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/534588250?h=7edf94bba3&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="XR Studios | External Unreal Content Integration Guide"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script> -->

This is a short overview of the steps to prepare Unreal content for delivery, intended as a quick reference for those who are familiar with the XR Studios workflow. For a much more in-depth guide on XRS Unreal Content for first-time creators, see the rest of the sections below, then come back and read this section.

* Download the Unreal Template File from Perforce following [this guide](docs/content/perforce.md).
    * There is also a <a href="https://drive.google.com/drive/folders/1sZdLxl7ijTaw9Odrlam8zAg5OLbZpIiO?usp=sharing">C4D file</a> with of the stage with proper scale and orientation for reference during modelling.
* If transferring content from a different Unreal project, be sure to follow the folder hierarchy found in the template file. An overview of this file can be found [below](docs/content/unreal.md#project-file-overview).
* Import the "XR cameras" and "Stage Reference" levels found in the "Stage" folder to the current scene. The XR cameras are what Disguise uses to interface with the current scene and are essential. The stage reference is to help with placement of shots and the height of the floor which must be at 0,0,0. Anywhere talent is intended to walk on should be level with the stage floor.
* Add any objects that should occlude talent to a frontplate layer in the scene named "FG" (Select desired actors in World Outliner -> Layers -> Add Selected Actors to New Layer). Ensure the Actor Layer is named `FG`
* Expose any control variables to the d3 timeline for real-time control by following the "Exposed Parameters" section of [this guide](http://help.disguise.one/Content/Configuring/Render-engines/RenderStream-Unreal.htm) 

## Getting the Unreal Template Files
Access the Unreal Project Template using Perforce (P4V). 
A specific depot and access credentials should be provided by the XRS Team. You will work inside this Project file, and submit updates and changes via Perforce.
If you have not used Perforce before, follow the [Content Delivery via Perforce](docs/content/perforce.md) Guide to get started.

## Getting the Cinema4D Asset Files
Use the following 3D assets to ensure the content is built out with accurate cameras and stage dimensions.

<a href="https://drive.google.com/drive/folders/1sZdLxl7ijTaw9Odrlam8zAg5OLbZpIiO?usp=sharing"><button type="button">Download C4D Resources</button></a>


## Project File Overview
All of the content will go inside the project's *Content* folder. The Content folder should be set up as such:
- *Scenes* folder: This folder contains sub-folders for each separate scene in the project. Each scene contains a *Level* and a *Sequence*
    - Scene *Level*: A named level (.umap) that should contain all the visual content for its scene
    - Scene *Sequence*: A file (.uasset) that contains the animation and sequencing for its scene
        - This can be added by opening the level in Unreal Engine, clicking "Cinematics" on the overhead bar, and clicking "Add Level Sequence"
    - Each scene should have its own named folder. For example:
        - Content
            - Scenes
                - Song A
                    - Song A Level (.umap)
                    - Song A Sequence (.uasset)
                - Song B
                    - Song B Level (.umap)
                    - Song B Sequence (.uasset)
- *Stage* folder: This folder contains all the technical assets related to the physical stage like LED Reference Geometry, Cameras, and Demo Content. One should not need to modify anything in here.
    - Demo Scene: This contains a level and a sequence that contain reference objects to the Stage and the Cameras. Additionally, there are examples of different common XR content types.
    - Stage A References: Meshes and 3D Objects exactly matching the XR Studios Stage A to help visualize the content's relationship to the real world.
    - XR Cameras: A scene containing the cameras that will stream the content to the LED Stage. Add this as a sublevel to the content's level to gain access to the cameras.

## Creating Content with the Template

### Organization
* There should be an individual folder for each Scene in the project
* Name the Scene's folder, level, and level sequence with corresponding name
* Keep all content related to each scene inside its respective folder

### Sequences
* Ensure sequences are built at a 60fps time base
* All animation that needs to sync to timecode should be included in the sequencer
* Include 5 seconds (300frames) of pre-roll and post-roll to compensate for any delay

!> Do **not** use the cameras from the XRCameras sublevel in your sequences.

### FBX Sequences
To import an FBX Sequence into your scene, navigate to `File > Import into Level`. The "Import" button in the Content Browser ***will not*** take you to the correct dialog

In the file menu popup, choose a location within the scene's folder for the imported sequence to reside. Once this is done, a dialogue with the FBX Scene Import Options should appear. Click Import.

Add an *FBX Scene* object to the Level Sequence. Add an *FBX Animation Sequence* object to the Animation Track.

### C4D Datasmith
Datasmith is a tool that automatically brings in models from software like Cinema4D. There are some details to how these models are imported:
- *Mographs* translate over effectively. Mograph Effectors are not sent as assets into UE4 but their results translate. Mograph objects (i.e. clones) will appear in the World Outline but will each be their own individual object.
- *Deformers* will not appear as assets in UE4 but their results translate.
- *Materials* will be recreated in UE4. *Textures* generated inside the modelling software will not translate.
- *Animations* will translate but will simply alter the Transform Position of the model frame by frame. Add the animation to the Level Sequence by dragging and dropping it on top of the Level Sequence to create a sub-scene.

> See an example of this in the Demo Scene included with the Template File

### Particle Systems
Niagara systems must be deterministic using a [System Life Cycle](https://www.youtube.com/watch?v=rIkpu358Hak&feature=emb_title) track on the Level Sequence's timeline

> See an example of this in the Demo Scene included with the Template File

### Media Tracks
Media can be added to a scene in the form of a 60fps EXR or PNG Image Sequence via a [Media Track](https://docs.unrealengine.com/4.27/en-US/WorkingWithMedia/IntegratingMedia/MediaFramework/HowTo/ImgMediaSource/) in the Level Sequence.

> See an example of this in the Demo Scene included with the Template File

### Exposable Parameters
Exposable parameters are a useful feature that allow for quick tweaking onsite by our media server operators without having to go into the unreal scene itself. With values exposed, we build in the flexibility to adapt to any unseen looks and can keyframe these values if they need to change throughout a performance. Examples of this are positions of specific objects, lighting color or intensity, timing of animations, etc. 

To do this, go inside your level blueprint and create a variable based upon your needs. When a variable is selected, check instance editable, this will allow access to this variable. The eye icon in the variables left hand side dropdown will appear to inform you that this is now visible inside of the media server. Additionally inside of the specific variable you can control the category selection and the default value which will be the starting point. Make sure you compile the blueprint upon completion of steps.

!> Ensure all Exposed Parameters are being tracked in the Project Document

### Remote Texture Sharing
The RenderStream plugin offers support for the sharing of textures through the use of exposed parameters. This allows a two-way flow of video content between disguise and the Unreal Engine project.
Follow these steps to configure:

1. Add a 3D Object into the scene onto which the texture will be streamed
2. Create a new Render Target and Material:
    1. Create a new Asset under Materials & Textures -> Render Target
    2. Drop the Render Target onto the 3D Object you created in Step 1
    3. Ensure that a new material has been created for the Render Target, and has been set as a material element in the "Materials" component of the 3D Object
3. Expose the Render Texture as an exposed parameter, following the steps in the section above
    - The Blueprint Variable created should be of type `Texture Render Target 2D`
    - The variable's Default Value should be the Render Target created in Step 2

### Optimization and Performance
- Scenes must run at or above 60fps on Disguise RX2 Hardware
- As a general rule, keep your project's Game Time under 8ms, and its Total Frame Time under 16ms. Lower is always better!

Be aware of building and developing optimized content. There are a number of areas in your scene that may be reducing performance. Utilize profiling and debug tools to find good candidates for optimization. Common areas include:
- Lighting:
    - Too many dynamic lights
    - Too many shadow-casting lights
    - Overlapping attenuation on lights
- Materials:
    - High texture memory use
    - High number of unique materials
    - Too many shader instructions
    - Many transparent overlapping materials (overdraw)
- Objects
    - Large number of objects / high triangle count
    - Complex CPU logic (collisions, water, etc)
    - Lots of blueprint logic happening every frame

## Using Existing Content
If you have existing unreal content you can migrate it into the Template Project.
1. Replicate the Folder Hierarchy in your existing Project: Content > Scenes > SceneFolderName > [Scene Level & Scene Content Here]
2. Migrate your Level: Asset Actions > Migrate. Choose the Content Folder of the Template Project as your destination.
3. Check that there were no errors! Continue work inside the Template Project.

## Creating the Fixed Plate Render
The fixed plate render is a video file rendered from a fixed camera position that is displayed on the LED outside of the camera frustrum to provide consistent ambient lighting when the camera frustrum does not cover the full LED surface.

1. Place a camera in your level, and position it to capture most/all of the stage
2. Create a new Sequence in your scene via Cinematics > New Level Sequence
3. Drag the new camera from your World Outline into the Sequencer
4. Save the Sequence
5. Go to Window > Cinematics > Movie Render Queue, click to add a Render, and select your Sequence
6. The media you export depends on your scene:
    1. If your scene has lots of moving parts or interactivity, in the Job's settings, disable ".jpg Sequence" and add a new setting for "Apple ProRes". Set its codec to HQ. Accept settings.
    2. Otherwise, in the Job's settings, disable ".jpg Sequence" and add a new setting for ".png Sequence". In the Output settings, check "Use Custom Playback Range", and set "Custom End Frame" to 1. Accept settings.
7. Press "Render (Remote)". The static plate .mov or .png will be in the folder specified in your Job's Output settings.
8. If you exported a video, using the [NotchLC plugin](https://notchlc.notch.one/), convert your rendered video to a NotchLC optimal codec .mov file.

## Preparing the Scene for Handoff
- Ensure there is a [Player Start Actor](https://docs.unrealengine.com/4.26/en-US/Basics/Actors/PlayerStart/) somewhere not-visible in the scene (like under the floor); this prevents the default Player Sphere from spawning on Play.
- Disable any mannequins
- Make sure Frame Smoothing is disabled: Go to `Edit > Project Settings > Engine > General Settings > Framerate` and ensure that `Smooth Framerate` is unchecked.
- Ensure Blueprint nodes are only firing on "Event Tick" if it is absolutely necessary that they run every frame. Use timers, timelines, custom tick intervals, or custom events in lieu of "Event Tick" wherever possible.
- Avoid expensive functions ("Get All Actors of Class", for loops, complex construction scripts, etc) especially in Blueprints that run more than once.

&nbsp;

&nbsp;

*contact: integration@xrstudios.live*
