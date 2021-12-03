# Unreal Content Checklist

This list is an overview of steps to getting an unreal content file ready for delivery and links out to other pages in this guide for more information

* Download the unreal template file from Perforce ([perforce help here](docs/content/perforce.md)). This will be where to work from and submit file changes to.
    - There is also a <a href="https://drive.google.com/drive/folders/1sZdLxl7ijTaw9Odrlam8zAg5OLbZpIiO?usp=sharing">C4D file</a> with of the stage with proper scale and orientation for reference during modelling.
* If transferring content from another, external unreal file, be sure to follow the folder hierarchy found in the template file. An overview of this file can be [found here](docs/content/unreal.md).
* Import the "XR cameras" and "Stage Reference" levels found in the "Stage" folder to the current scene. The XR cameras are what Disguise uses to interface with the current scene and are essential. The XR cameras level also includes the frontplate layer. The stage reference is to help with placement of shots and the height of the floor which must be at 0,0,0. Anywhere talent is intended to walk on should be level with the stage floor.
* Add any objects you want to occlude talent to the frontplate layer in your scene
* Add any values you want to expose to the d3 timeline for real time control by [following this guide](http://help.disguise.one/Content/Configuring/Render-engines/RenderStream-Unreal.htm) 

Please check out the [XR Unreal Content Guide](docs/content/unreal.md) for a more in-depth guide.