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

### Project Structure
- *Scenes* folder: This folder contains sub-folders for each separate scene in the project. Each scene contains a *Level* and a *Sequence*
    - Scene *Level*: A named level (.umap) that should contain all the visual content for its scene
    - Scene *Sequence*: A file (.uasset) that contains the animation and sequencing for its scene
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
### Reference Objects