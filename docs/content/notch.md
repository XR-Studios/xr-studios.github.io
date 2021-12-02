# Notch XR Content Guide
TODO embed walkthrough video here

## Getting the Notch Template Files

## Getting the Cinema4D Asset Files

## Creating Content with the Template
TODO


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
    - Render only one frame by setting your Start Time to 00:00:00 and your End Time to 00:00:01
7. If your scene *does* have a lot of interactivity or moving parts, ensure it has the following settings:
    - Export Type: Quicktime GPU
    - Codec: NotchLC, Quality 79 percent
    - Render Alpha Channel is checked
    - Enable Preroll with a 2-5 frame duration
8. Include the .mov or .png with your submission

## Notch Block and Asset Delivery
TODO

&nbsp;

&nbsp;

*contact: integration@xrstudios.live*