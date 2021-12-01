# Unreal XR Content Guide
TODO embed video walkthrough

## Getting the Unreal Template Files
Access the Unreal Project Template using Perforce (P4V). 
A specific depot and access credentials should be provided to you by the XRS Team. You will work inside this Project file, and submit updates and changes via Perforce.
If you have not used Perforce before, follow the [Content Delivery via Perforce](docs/content/perforce.md) Guide to get started.

## Getting the Cinema4D Asset Files
Use the following 3D assets to ensure your content is built out with accurate cameras and stage dimensions.

TODO link c4d files

## Project File Overview
All of your content will go inside the project's *Content* folder. The Content folder should be set up as such:
- *Scenes* folder: This folder contains sub-folders for each separate scene in the project. Each scene contains a *Level* and a *Sequence*
    - Scene *Level*: A named level (.umap) that should contain all the visual content for its scene
    - Scene *Sequence*: A file (.uasset) that contains the animation and sequencing for its scene
        - This can be added by opening your level in Unreal Engine, clicking "Cinematics" on the overhead bar, and clicking "Add Level Sequence"
    - Each scene should have its own named folder. For example:
        - Content
            - Scenes
                - Song A
                    - Song A Level (.umap)
                    - Song A Sequence (.uasset)
                - Song B
                    - Song B Level (.umap)
                    - Song B Sequence (.uasset)
- *Stage* folder: This folder contains all the technical assets related to the physical stage like LED Reference Geometry, Cameras, and Demo Content. You shouldn't need to modify anything in here.
    - Demo Scene: This contains a level and a sequence that contain reference objects to the Stage and the Cameras. Additionally, there are examples of different common XR content types.
    - Stage A References: Meshes and 3D Objects exactly matching the XR Studios Stage A to help visualize the content's relationship to the real world.
    - XR Cameras: A scene containing the cameras that will stream your content to the LED Stage. Add this as a sublevel to your content's level to gain access to the cameras.

## Creating Content with the Template

### Organization
* There should be an individual folder for each Scene in your project
* Name your Scene's folder, level, and level sequence with corresponding name
* Keep all content related to each scene inside its respective folder

### Sequences
* Ensure sequences are built at a 60fps time base
* All animation that needs to sync to timecode should be included in the sequencer
* Include 5 seconds (300frames) of pre-roll and post-roll to compensate for any delay

### FBX Sequences