# Getting Started
## About
RenderStream for TouchDesigner, called *TouchRender* for short, is a plugin for [Disguise's](http://disguise.one) RenderStream protocol, which allows controlling third-party render engines from the disguise software. This plugin allows Derivative's [TouchDesigner](http://derivative.ca) to be used as one of said third-party render engines alongside the natively-supported Unreal Engine and Notch Builder.

TouchRender exists as a set up of Custom Operators for TouchDesigner that, when launched as a RenderStream Asset from Disguise, allow for streaming of TouchDesigner content directly to Disguise as if it were any normal content layer.

<p>&nbsp;</p>

# Setup
## Download and Install
1. Setup and install [Disguise](https://download.disguise.one/) (Latest Ver. Tested with TouchRender: r19.2 81378)
2. Setup and install [TouchDesigner](https://derivative.ca/download) (Latest Ver. Tested with TouchRender: 2021.15240)
3. Download the **Release** folder of the [TouchRender GitHub Repo](https://github.com/XR-Studios/XRS-TouchDesigner-RenderStream)
5. Place all the .dll files from the downloaded **Release/OPs** folder into your **Documents/Derivative/Plugins** folder. If the Plugins folder does not exist inside the Derivative folder, simply create it.

## Preparing TouchDesigner
!> Your content should render in such a way that whatever you want to be streaming ends up in a single TOP. These steps must be performed on each machine that will be rendering Touch content, and the folder and shortcut names must be identical on each machine.
1. Create your TouchDesigner project file (or place your prepared file) somewhere on the machine
2. Navigate to Disguise's **RenderStream Projects** folder
3. Create a new folder for your TouchDesigner project
4. In the new folder for your TouchDesigner project, create a new shortcut to the TouchDesigner executable
    - Right Click > New File > Shortcut; TouchDesigner installs by default to C:\Program Files\Derivative\TouchDesigner\bin
5. Right click the created shortcut and edit its **Properties**
6. In the **Target** section, after the path to the TouchDesigner executable, add a space and the path to your TouchDesigner project file in quotes, like in this example:


```Target
"C:\Program Files\Derivative\TouchDesigner\bin\TouchDesigner.exe" "C:\Users\Admin\Desktop\Github Projects\XRS-TouchDesigner-RenderStream\TouchRender.toe"
```

7. Add a Flip TOP to your final content's TOP and *Flip Y*
8. Add a Crop TOP to that Flip TOP and leave it "empty" (i.e. leave the "Crop" settings from 0 to 1, Left to Right and Bottom to Top)
9. Create a Replicator COMP and set its *Master Operator* parameter equal to the empty Crop TOP you just created
10. Set the Replicator COMP's *Replication Method* parameter to "By Number", and set the *Number of Replicants* equal to whatever you plan to name your **RenderStream In CHOP**'s *nStreams* channel -- for example:  `op('MyRSinCHOP')['nStreams']`
11. Replace the Replicator COMP's *Callbacks DAT* parameter with whatever you plan to name your **RenderStream Callbacks DAT** -- by default, `Renderstreamcallbacks1`
12. Create a **RenderStream Callbacks DAT** (New Operator > Custom > RStream Callback) and fill in its parameters with what you plan to name your RenderStream Operators, and whatever your Replicator COMP's *Operator Prefix* parameter is
13. Create a **RenderStream Out TOP** and rename it to match the name you filled in in your **RenderStream Callbacks DAT**'s *Name of RenderStream Out TOP* parameter
14. Create a **RenderStream Params DAT** and fill in its parameters page with the details of your content. Note that you **must** reload the DAT if any of the numbers need to be changed and you must fill out the entire table again, so figure out all your exposed params beforehand! If you are unfamiliar with channels, they simply serve to organize and separate data. For example, FrontPlate and BackPlate is simply streaming to two channels and then putting the content sent to the FrontPlate channel in front of the content sent to the BackPlate channel
15. Pulse your **RenderStream Params DAT**'s *Reload* button
16. Lock the **RenderStream Params DAT** in order to make it editable
    - Note that if you unlock the DAT it will lose any user-entered content and will you be forced to lock it and fill it out again.
17. Fill in **EVERY** empty cell in the generated **RenderStream Params DAT** table. Note that the *min*, *max*, and *step* columns are ignored for non-numerical parameters but not my problem if you leave any cells blank and your params don't expose.
    - The schema for Exposable Parameters is thus:
        - scene: The scene that this is a parameter for
        - name: The name of this parameter as it will appear in Disguise
        - group: What group of parameters this parameter belongs to
            - For organizing your scene's exposable parameters - for example, three parameters named X, Y, and Z could all be in a group called "Position" and will then appear under that label in Disguise
        - value: The default value of this parameter
        - min: The minimum value of this parameter
        - max: The maximum value of this parameter
        - step: How much this parameter will change by when scrolled with mouse wheel or arrow key
        - key: A unique one-word key for this parameter; think of it like the variable name for this parameter in code
    - Note that an Exposable Parameter's *scene* value must match one of the *Scene Name* values from the *Scenes* section of the table
    - TODO: Put an example picture here
18. Set your **RenderStream In CHOP**'s *RenderStream Params Dat* parameter equal to the name of your filled-out **RenderStream Params DAT**
19. TODO Map camera

!> DO NOT Start RenderStream from just TouchDesigner. RenderStream's subroutines can only be accessed when TouchDesigner is launched as a Workload from Disguise.

## Preparing Disguise
1. Create a new d3 project, or open the project to which you wish to add TouchRender
2. If one is not already prepared, create an *MR Set* in your Stage with a camera and at least one LED screen
3. Add a RenderStream Layer to your d3 timeline
4. Create or assign a *Cluster pool* with your desired Render Machines
5. Select your TouchDesigner project file's shortcut as the RenderStream Layer's *Asset*
6. Create or assign a *Cluster assigner* with your RenderStream Asset
7. Create or assign a *Multichannel map* with your asset, and add a Spatial Map to that Multichannel map, setting up said Spatial Map if one is not already prepared

Start your RenderStream Workload. If everything is set up properly, your Touch project will launch on your Render Machines! Assuming your Custom Operators are set up already as detailed in the [Preparing TouchDesigner](#preparing-touchdesigner), you are all set to pulse the *Start RenderStream* button on your **RenderStream In CHOP**.  
Once that loads, your *nStreams* will be set, and your replicator will clone cropped versions of your content.  
Finally, pulse the *Start Sending to RenderStream* button on your **RenderStream Out TOP** and you will hopefully see your content in Disguise!

<p>&nbsp;</p>

# Gotchas