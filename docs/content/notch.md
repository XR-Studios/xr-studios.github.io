# Notch XR Content Guide

## Getting the Notch Template Files
<a href="https://drive.google.com/drive/folders/1sZd24zD7V8B-RfDXahQqpK1uj-GlFX2u?usp=sharing"><button type="button">Download Notch Template</button></a>

## Getting the Cinema4D Asset Files
<a href="https://drive.google.com/drive/folders/1sZdLxl7ijTaw9Odrlam8zAg5OLbZpIiO?usp=sharing"><button type="button">Download C4D Resources</button></a>

## Creating Content with the Template
<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/460347309?h=4026549de3&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="XR Studios | Notch Content Integration Guide"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

### Performance
Notch can profile performance on other machines to get an accurate estimate of our machines running XR. To do this go to The View Menu and select performance. Notch will provide Local GPU & CPU ms. Under Target System select disguise rx2. When the scene is played, Notch will provide an estimated GPU ms time.


### Gotchas
- Ensure Anti-Aliasing is enabled in the project settings and that one or several FXAA or Temporal AA nodes are attached to the root node.
- Screen space ambient occlusion can cause noise. Turn down blend amount and turn up blur size to tweak this.
- Light Shadows can dramatically effect performance. Find a balance of Shadow Map Size and Shadow Softness. 

## Creating the Fixed Plate Render
The fixed plate render is a video file rendered from a fixed camera position that is displayed on the LED outside of the camera frustrum to provide consistent ambient lighting when the camera frustrum does not cover the full LED surface.

1. Add a new camera to your Nodegraph, name it "Backplate" or "FixedCam" or something similar.
2. Move the camera so it can see most/all of your scene, and set its FOV to 90. Make sure "Use Field of View Y" and "Use Field of View Y as X" are both checked.
3. In the View tab, make sure "Render Queue" is visible.
4. In your Timeline view, drag the Layer of your scene into the Render Queue
5. Double click your Layer in the Render Queue to change its render settings
6. If your scene doesn't have a lot of interactivity or moving parts, ensure it has the following settings:
    - Export Type: Image Frame Sequence
    - Codec: PNG; Quality 100 percent
    - Render Alpha Channel is checked
    - Enable Preroll with a 2-5 frame duration
    - Render only one frame by setting your Start Time to `00:00:00` and your End Time to `00:00:01`
7. If your scene *does* have a lot of interactivity or moving parts, ensure it has the following settings:
    - Export Type: Quicktime GPU
    - Codec: NotchLC, Quality 79 percent
    - Render Alpha Channel is checked
    - Enable Preroll with a 2-5 frame duration
8. Include the .mov or .png with your submission

## Notch Block and Asset Delivery
- Delivery Link: https://xr-studios.digitalpigeon.com/rcv/send
    - Please include file names in the message section
    - A block (.dfxdll), the project file (.dfx), and a scene preview need to be delivered
- Naming: The exported block does not have a timestamp. Place it into a folder with the same name AND a timestamp.
    - Project naming: SongID_Description_vYYYYMMDDHHMM.dfx
    - Block Naming: SongID_Description.dfxdll
    - Place the exported block in a folder named: SongID_Description_vYYYYMMDDHHMM
    - Layers should follow the same naming convention
- Provide any additional assets used in the block that are not embedded
    - Naming: SongID_Description_vYYYYMMDDHHMM
        - Year, Month, Day, Hour(24h), Minute
- You will be invited to a Notch Exposed Parameter Document/Google Sheet. Please name and expose your notch parameters for disguise and keep track of use case and other information there.
- Please provide a web compressed preview with audio with each delivery showcasing the inteded look and usage of the scene.

&nbsp;

&nbsp;

*contact: integration@xrstudios.live*