# Themes
# Guide
Themes are a much easier way to give your UI a consistent and good-looking aesthetic without manually having to grab each component and set its width, height, padding, stripe color, font size, margin size, and graph size.

1. Instantiate an `ofxXRSTheme`
2. Customize the theme as you desire
3. Call `init()` on your theme
4. Call `setTheme()` on your desired `ofxXRSComponent`

!> Note that `ofxXRSComponent::setTheme(ofxXRSTheme* theme)` is recursive, meaning it will also apply the theme to any and all children. This means you can just call `setTheme()` on your panels to apply it to your entire UI.

# Pre-installed Themes
The following themes come pre-installed with the ofxXRSLibrary, and can be accessed by instantiating their respective classes as opposted to the generic `ofxXRSTheme` class.

- Smoke: `ofxXRSThemeSmoke`
- Wireframe: `ofxXRSThemeWireframe`
- Midnight: `ofxXRSThemeMidnight`
- Aqua: `ofxXRSThemeAqua`
- Charcoal: `ofxXRSThemeCharcoal`
- Autumn: `ofxXRSThemeAutumn`
- Candy: `ofxXRSThemeCandy`

[Pictures Here]

# Customization
An `ofxXRSTheme` has several properties to manipulate in order to affect the style of your UI:

!> `init()` must be called on your theme whenever it is modified before applying it again to a component via `setTheme()`

 - **font:** The font metadata for components using this theme
    - *float* size: The size of the font
 - **stripe:** The settings for the color stripe on the edge of components using this theme
    - *ofColor* label: The color of the stripe for `ofxXRSLabel`
    - *ofColor* button: The color of the stripe for `ofxXRSButton`
    - *ofColor* toggle: The color of the stripe for `ofxXRSToggle`
    - *ofColor* slider: The color of the stripe for `ofxXRSSlider`
    - *ofColor* pad2d: The color of the stripe for `ofxXRSPad2d`
    - *ofColor* matrix: The color of the stripe for `ofxXRSMatrix`
    - *ofColor* graph: The color of the stripe for `ofxXRSWaveMonitor` and `ofxXRSValuePlotter`
    - *ofColor* dropdown: The color of the stripe for `ofxXRSDropdown`
    - *ofColor* textInput: The color of the stripe for `ofxXRSTextInput`
    - *ofColor* colorPicker: The color of the stripe for `ofxXRSColorPicker`
 - **layout:** The physical dimensions for components using this theme
    - **NOTE: Using `ofxXRSTheme::resize(float multiplier)` is recommended over manipulating these values**
    - *float* width: The width of components using this theme
    - *float* height: The height of components using this theme
    - *float* padding: The amount of padding between components on a Panel
    - *float* vMargin: The vertical spacing between components on a Panel
    - *float* iconSize: The size of any icons used by components like radio buttons, dropdown arrows, etc
    - *float* labelWidth: The width of the space for labels next to any components using this theme
    - *float* labelMargin: The size of the space between a component's label and value
    - *float* breakHeight: The height of any `ofxXRSBreak`
    - **colorPicker:** Unique layout dimensions for `ofxXRSColorPicker`
        - *int* rainbowWidth: The width of the rainbow image that drops down when users select a color picker
    - **pad2d:** Unique layout dimensions for `ofxXRSPad2d`
        - *int* height: The height of the component
        - *int* ballSize: The size of the ball at this pad's current x,y value
        - *int* lineWeight: The width of the axis lines
    - **graph:** Unique layout dimensions for `ofxXRSWaveMonitor` and `ofxXRSValuePlotter`
        - *int* height: The height of the component
        - *int* pointSize: The size of the points if the draw mode is set to `ofxXRSGraph::POINTS`
        - *int* lineWeight: The width of the lines if the draw mode is set to anything else
    - **matrix:** Unique layout dimensions for `ofxXRSMatrix`
        - *int* height: The height of the component
        - *int* buttonSize: The size of the individual buttons within the matrix
        - *int* buttonPadding: The size of the padding between buttons on the matrix
 - **border:** The properties for the thin border drawn around each component
    - *ofColor* color: The color of the borders
    - *bool* visible: Whether or not the borders are drawn
    - *int* width: The width of the borders
 - **color:** The colors for components using this theme
    - *ofColor* guiBackground: The color of the `ofxXRSPanel`
    - *ofColor* label: The color of any labels (both `ofxXRSLabel` and component labels)
    - *ofColor* background: The background color of any component using this theme
    - *ofColor* inputAreaBackground: The background color of any input areas (e.g. a Text Input's textbox)
    - *ofColor* backgroundOnMouseOver: The background color of any component when the mouse is over it
    - **slider:** Unique colors for `ofxXRSSlider`
        - *ofColor* fill: The fill color
        - *ofColor* text: The color of the text that displays the slider's current value
    - **textInput:** Unique colors for `ofxXRSTextInput`
        - *ofColor* text: The color for the current value of the text inputs
    - **colorPicker:** Unique colors for `ofxXRSColorPicker`
        - *ofColor* border: The color for the border of the color pickers
    - **pad2d:** Unique colors for `ofxXRSPad2d`
        - *ofColor* line: The color of the perpendicular lines that meet at the ball
        - *ofColor* ball: The color of the ball at the current x,y value
    - **graph:** Unique colors for `ofxXRSWaveMonitor` and `ofxXRSValuePlotter`
        - *ofColor* lines: The color for any outline lines
        - *ofColor* fills: The color for the fill underneath the line if the graph's draw mode is set to `ofxXRSGraph::FILLED`
    - **matrix:** Unique colors for `ofxXRSMatrix`
        - *ofColor* label: The color for the text that draws the numbers on the buttons
        - *ofColor* button: The color for the buttons themselves
        - Note: label and button are one child down behind *theme.matrix.normal, hover, and selected.*  
        Each label and button parameter sets its color for each of those states, where `theme.matrix.hover` is the colors when a button is being hovered over, and `theme.matrix.selected` is the colors when a button is active.

# Make your own Theme
Making your own theme is as simple as creating a class that inherits `ofxXRSTheme` and instantiating the values according to the design of your theme.

In the constructor for your theme, simply instantiate the theme's variables for the look you desire. For example, here's the code for the "Wireframe" theme that is included with the library.

```cpp
class ofxXRSThemeWireframe : public ofxXRSTheme{

    public:
    
        ofxXRSThemeWireframe()
        {
            stripe.visible = false;
            color.label = hex(0x6E6E6E);
            color.icons = hex(0x6E6E6E);
            color.background = hex(0xFCFAFD);
            color.guiBackground = hex(0xD8D8DB);
            color.inputAreaBackground = hex(0xE9E9E9);
            color.slider.fill = hex(0x6E6E6E);
            color.slider.text = hex(0x6E6E6E);
            color.textInput.text = hex(0x6E6E6E);
            color.textInput.highlight = hex(0xFCFAFD);
            color.colorPicker.border = hex(0xDFDDDF);
            color.textInput.backgroundOnActive = hex(0xD1D1D1);
            color.backgroundOnMouseOver = hex(0xECECEC);
            color.backgroundOnMouseDown = hex(0xDFDDDF);
            color.matrix.normal.button = hex(0xDFDDDF);
            color.matrix.hover.button = hex(0x9C9DA1);
            color.matrix.selected.button = hex(0x6E6E6E);
            color.pad2d.line = hex(0x6E6E6E);
            color.pad2d.ball = hex(0x6E6E6E);
            color.graph.fills = hex(0x6E6E6E);
            init();
        }
};
```

# Unique Components
Once you have a theme applied to your UI, you may want to have specific components that go against the theme by, for example, having a different background or stripe color.

The code to do this is simple:
```cpp
ofxXRSButton* specialButton = panel->getButton("Button With Unique Stripe");
specialButton->setStripeColor(ofColor::purple);
```

However, it can be quite a process of getting these settings to stick consistently, as the auto-drawing nature of the library sometimes involves re-applying themes to their components (e.g. when the window is resized) - meaning the default setting will override the custom setting.

The best way to ensure your UI customizations stick is to put it in the `update()` method - however, this will tank the frame rate as every custom UI component needs to be accessed and modified every frame. We can mitigate this by adding a member variable to track whenever our customization needs re-applying:

```cpp
/**
 * ofApp.h
 */

ofxXRSTheme* theme;
ofxXRSPanel* panel;
bool m_customized;


/**
 * ofApp.cpp
 */

void ofApp::setup() {
    theme = new ofxXRSTheme(false);
    theme->resize(2.0f);
    theme->stripe.label = ofColor::red;
    theme->init();

    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    panel->addButton("Normal Button 1");
    panel->addButton("Normal Button 2");
    panel->addButton("Green Stripe Button");
    panel->setTheme(theme);

    m_customized = false;
}

void ofApp::update() {
    if(!m_customized) {
        // Apply customizations
        panel->getButton("Green Button")->setStripeColor(ofColor::green);
        m_customized = true;
    }
}

void ofApp::windowResized(int w, int h) {
    m_customized = false;
}
```