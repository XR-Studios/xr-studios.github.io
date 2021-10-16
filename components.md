# Components
Components are the individual UI elements that make up your application.

They are divided into three types: ``Controls``, ``Monitors``, and ``Organizers``

## Common Methods
What follows is a list of methods that are shared by several classes and that you will probably find useful.

### Panel Components <!-- {docsify-ignore} -->
These methods can be called on any object that interacts with the Panel system - in other words, any component that inherits ofxXRSComponent. In other other words, any component except Large Buttons and Knobs.

 - `ofxXRSComponent* getComponent(ofxXRSType type, string label)` | `getComponent(string label)`
     - Returns a pointer to the child object component matching *type* and/or *label*, or nullptr if no matching children could be found. Note that this method returns a generic ofxXRSComponent.
- `string getLabel()`
     - Returns a string of this component's label.
- `void setLabel(string label)`
     - Set this component's label to *label*.
- `void setLabelColor(ofColor color)`
    - Sets the color of this component's label text to *color*.
- `float getX()`
    - Returns a float of this component's current X coordinate.
- `float getY()`
    - Returns a float of this component's current Y coordinate.
- `void setVisible(bool visible)`
    - Sets whether or not this component is visible equal to *visible*.
- `void setStripeColor(ofColor color)`
    - Sets the color of this component's stripe (See [Customizing Components]() for usage details)
- `void setBackgroundColor(ofColor color)`
    - Sets the color of this component's background (See [Customizing Components]() for usage details)
- `void setBackgroundColorOnMouseOver(ofColor color)`
    - Sets the color of this component's background while the user is mousing over it (See [Customizing Components]() for usage details)
- `void setBackgroundColorOnMouseDown(ofColor color)`
    - Sets the color that this component flashes when it is clicked (See [Customizing Components]() for usage details)
- `void setEnabled(bool enabled)`
    - Sets whether or not this component is enabled equal to *enabled*. Disabled elements will still draw but will not update or respond to any events.


Classes that inherit from *ofxXRSGroup* (currently *ofxXRSFolder* and *ofxXRSDropdown*) have the following common methods:
- `void expand()`
    - Expands the component as if the user had clicked it while it was closed.
- `void collapse()`
    - Collapses the component as if the user had clicked it while it was open.
- `void toggle()`
    - If the component is expanded it collapses it, and vice versa.
- `int getHeight()`
    - Get the height of the element in pixels.
- `bool getIsExpanded()`
    - Returns a bool for whether or not this component is currently expanded.


Classes that inherit from *ofxXRSInteractableObject* (currently *ofxXRSFolder* and *ofxXRSPanel*) have the following common methods, related to managing their child components:
- `ofxXRSLabel* addLabel(string label)`
    - Adds a label to the bottom of this component and returns a pointer to it.
- `ofxXrsButton* addButton(string label)`
    - Adds a button to the bottom of this component and returns a pointer to it.
- `ofxXRSToggle* addToggle(string label, bool state)`
    - Adds a toggle to the bottom of this component and returns a pointer to it. If you want a toggle to default to starting checked, set *state* to true.
- `ofxXRSSlider* addSlider(string label, float min, float max, float value)`
    - Adds a slider to the bottom of this component and returns a pointer to it.
- `ofxXRSTextInput* addTextInput(string label, string value)`
    - Adds a text input to the bottom of this component and returns a pointer to it.
- `ofxXRSColorPicker* addColorPicker(string label, ofColor color)`
    - Adds a color picker to the bottom of this component set to *color* and returns a pointer to it.
- `ofxXRSBreak* addBreak()`
    - Adds a horizontal break to the bottom of this component and returns a pointer to it.
- `ofxXRS2dPad* add2dPad(string label)`
    - Adds a 2D Coordinate Pad to the bottom of this component and returns a pointer to it.
- `ofxXRSMatrix* addMatrix(string label, int numButtons, bool showLabels)`
    - Adds a Button Matrix with *numButtons* buttons to the bottom of this component and returns a pointer to it. If *showLabels* is true, the index of each button will be drawn in the center of it.
- `ofxXRSWaveMonitor* addWaveMonitor(string label, float frequency, float amplitude)`
    - Adds a Wave Monitor with amplitude *amplitude* and frequency *frequency* to the bottom of this component and returns a pointer to it.
- `ofxXRSValuePlotter* addValuePlotter(string label, float min, float max)`
    - Adds a value plotter from range \[*min*-*max*\] to the bottom of this component and returns a pointer to it.
- `void attachItem(ofxXRSComponent* item)`
    - Attaches *item* to the bottom of this component.
- `ofxXRSLabel* getLabel(string label)`
    - Returns a pointer to the child *ofxXRSLabel* with label *label*, or nullptr if a child could not be found.
- `ofxXRSButton* getButton(string label)`
    - Returns a pointer to the child *ofxXRSButton* with label *label*, or nullptr if a child could not be found.
- `ofxXRSToggle* getToggle(string label)`
    - Returns a pointer to the child *ofxXRSToggle* with label *label*, or nullptr if a child could not be found.
- `ofxXRSSlider* getSlider(string label)`
    - Returns a pointer to the child *ofxXRSSlider* with label *label*, or nullptr if a child could not be found.
- `ofxXRS2dPad* get2dPad(string label)`
    - Returns a pointer to the child *ofxXRS2dPad* with label *label*, or nullptr if a child could not be found.
- `ofxXRSTextInput* getTextInput(string label)`
    - Returns a pointer to the child *ofxXRSTextInput* with label *label*, or nullptr if a child could not be found.
- `ofxXRSColorPicker* getColorPicker(string label)`
    - Returns a pointer to the child *ofxXRSColorPicker* with label *label*, or nullptr if a child could not be found.
- `ofxXRSMatrix* getMatrix(string label)`
    - Returns a pointer to the child *ofxXRSMatrix* with label *label*, or nullptr if a child could not be found.
- `ofxXRSWaveMonitor* getWaveMonitor(string label)`
    - Returns a pointer to the child *ofxXRSWaveMonitor* with label *label*, or nullptr if a child could not be found.
- `ofxXRSValuePlotter* getValuePlotter(string label)`
    - Returns a pointer to the child *ofxXRSValuePlotter* with label *label*, or nullptr if a child could not be found.

## Controls
Controls are components that are interactable, and are hooked up to control some aspect of the stage or show.
What follows is a list of controls that are implemented as part of the ofxXRS library:

The following is a list of controls built into the panel system, meaning they can be instantiated and placed individually, but **ofxXRSPanel** and **ofxXRSFolder** natively support managing and adding these components.
- Button
- Slider
- Toggle
- Color Picker
- Text Input
- Dropdown
- Button Matrix
- 2D Coordinate Pad

The following is a list of controls that are not natively supported by Panels. This means these controls are just given an x and y for their position and a width and a height for their size, and must be manually moved and/or resized whenever the window is resized.
- Knob
- Large Button
- Large Image Button

### Button
Fires a trigger, listener, or some other event when clicked.  

Hooked up via an event listener function, a void method that takes an ofxXRSButtonEvent as an argument.  
Flashes a different color when clicked or hovered over.  


It's a button. You get it.
<div align=justify>
<img width="75%" src="./img/components/button.png"/>
</div>

>Class: `ofxXRSButton`

#### Methods
`ofxXRSButton` has no unique methods. You click it and something happens! That's it!

#### Instantiation
To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSButton* button;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel();
    button = panel->addButton("Button Label");
}
```

To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/
std::vector<ofxXRSComponent*> components;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSButton("Button Label");
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto component : components) {
        component->draw();
    }
}
```
#### Usage

### Toggle
A special type of button that keeps its state when pressed - used to toggle the state of something between "enabled" or "disabled", or set a variable to either 1 or 0, etc.
<div align=justify>
<img width="75%" src="./img/components/toggle.png"/>
</div>

>Class: `ofxXRSToggle`

#### Methods
- `void toggle()`
    - Toggles this component from checked to unchecked or vice versa.
- `void setChecked(bool checked)`
    - Sets this component's checked state. Like `ofxXRSToggle::toggle()`, but you have control over the new state instead of just swapping.
- `bool getChecked()`
    - Returns a boolean for whether or not this component is checked or not.

#### Instantiation
> Constructors:  
`ofxXRSToggle(string label, bool startedChecked = false)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSToggle* toggle;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    toggle = panel->addToggle("Toggle Label");
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSToggle("Toggle Label");
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### Text Input
A text box where the user can input a string.
<div align=justify>
<img width="75%" src="./img/components/textInput.png"/>
</div>

>Class: `ofxXRSTextInput`

#### Methods
- `void setText(string text)`
    - Sets the text of this input to *text*, as if it had been entered by the user.
- `string getText()`
    - Returns a string of the current value of this input
- `void setUpperCase(bool isUpper)`
    - Sets whether or not the text in the field is displayed in all-caps to *isUpper*
- `bool getTextUpperCase()`
    - Returns a boolean for whether or not the text in the field is displayed in all-caps
- `void setInputType(ofxXRSInputType type)`
    - Sets the input type of this field (numbers and letters, numbers only, etc) to *type*

#### Instantiation
> Constructors:  
`ofxXRSTextInput(string label, string defaultText = "")`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSTextInput* textInput;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    textInput = panel->addTextInput("Label", "Type Here...");
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSTextInput("Label", "Type Here...");
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### Slider
A control that sets the value of something between a minimum and maximum range.
<div align=justify>
<img width="75%" src="./img/components/slider.png"/>
</div>

>Class: `ofxXRSSlider`

#### Methods
- `void setMin(float min)`
    - Sets the minimum value of this slider to *min*
- `void setMax(float max)`
    - Sets the maximum value of this slider to *max*
- `void setValue(float value, bool dispatchEvent = true)`
    - Sets the value of this slider to *value* (or min, or max, if outside that range). If dispatchEvent is false it will not fire this slider's *ofxXRSSliderEvent*
- `void setScale(float scale)`
    - Like `ofxXRSSlider::setValue()`, except *scale* must be between 0.0f and 1.0f, and it will map that value to the slider's range.
- `float getValue()`
    - Returns a float for the current value of this slider
- `float getScale()`
    - Returns a float for the current value of this slider between 0 and 1


#### Instantiation
> Constructors:  
`ofxXRSSlider(string label, float min, float max, float val)`  
`ofxXRSSlider(string label, float min, float max)`  
`ofxXRSSlider(ofParameter<int> p)`  
`ofxXRSSlider(ofParameter<float> p)`

!> Note: I have neither fully implemented nor tested the current implementation of the ofParameter binding. Use at your own risk.

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSSlider* slider;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    slider = panel->addSlider("Slider Label", 0.0f, 100.0f, 50.0f);
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSSlider("Slider Label", 0.0f, 100.0f, 50.0f);
    comp->setPosition(10, 50);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### Color Picker
A control that drops down to a color wheel when clicked which sets the color of something using **ofColor**
<div align=justify>
<img width="75%" src="./img/components/colorPicker.png"/>
</div>

>Class: `ofxXRSColorPicker`

#### Methods
- `void setColor(ofColor color)` | `setColor(int hex)` | `setColor(int r, int g, int b, int a)`
    - Sets the current color value of this color picker to *color* or *hex*, as if it had been selected by the user.
- `ofColor getColor()`
    - Returns an ofColor for the current color value of this color picker.


#### Instantiation
> Constructors:  
`ofxXRSColorPicker(string label, ofColor color)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSColorPicker* picker;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    picker = panel->addColorPicker("Color Picker Label", ofColor::green);
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/
std::vector<ofxXRSComponent*> components;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSColorPicker("Color Picker Label", ofColor::green);
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### Dropdown
A control that drops down to a list of selections from which the user selects a single option
<div align=justify>
<img width="75%" src="./img/components/dropdown.png"/>
</div>

>Class: `ofxXRSDropdown`

#### Methods
- `void select(int index)`
    - Selects the *index*-th option from the Dropdown as if it had been selected by the user.
- `int size()`
    - Returns an int for how many options are in the dropdown
- `string getSelected()`
    - Returns a string for the currently selected option. Returns this dropdown's label if nothing has been selected (I think; have not tried)

#### Instantiation
> Constructors:  
`ofxXRSDropdown(string label, std::vector<string> options)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSDropdown* dropdown;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);

    std::vector<string> options = {
        "Option1", "Option2", "Option3"
    };
    dropdown = panel->addDropdown("Dropdown Label", options);
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    std::vector<string> options = {
        "Option1", "Option2", "Option3"
    }
    ofxXRSComponent* comp = new ofxXRSDropdown("Dropdown Label", options);
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```


### Button Matrix
A control that allows the user to toggle one or several buttons in a grid; most often used for cue lists.
<div align=justify>
<img width="75%" src="./img/components/buttonMatrix.png"/>
</div>

>Class: `ofxXRSMatrix`

#### Methods
- `void setRadioMode(bool radioMode)`
    - Sets whether or not this matrix is in radio mode (only one button can be active at a time) to *radioMode*
- `void setSelected(std::vector<int> listOfIndices)`
    - Sets all the button numbers in *listOfIndices* to active. Note that even if this matrix is set to radio mode, if there is more than one element in *listOfIndices*, they will all be set to active.
- `std::vector<int> getSelected()`
    - Returns a vector with a list of the indices of buttons that are currently active on this matrix.
- `ofxXRSMatrixButton* getButtonAtIndex(int index)`
    - Returns a pointer to the *ofxXRSMatrixButton* at *index*, or nullptr if there is no button at that index.

#### Instantiation
> Constructors:  
`ofxXRSMatrix(string label, int numButtons, bool showLabels = false)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSMatrix* matrix;

/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_RIGHT);
    matrix = panel->addMatrix("Matrix Label", 50);
}
```
To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRSMatrix("Matrix Label", 50, true);
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### 2D Coordinate Pad
A control that allows the user to see and set the 2D Position (X, Y) of whatever aspect of the stage or show is hooked up to it.
<div align=justify>
<img width="75%" src="./img/components/2dpad.png"/>
</div>

>Class: `ofxXRS2dPad`

#### Methods
- `void setPoint(ofPoint pt)`
    - Moves the cursor to the location at *pt*. Does nothing if *pt* is outside of the bounds of this pad's graph.
- `ofPoint getPoint()`
    - Returns an *ofPoint* for the cursor's current location within the graph.
- `void setBounds(ofRectangle bounds, bool scaleOnResize)`
    - Sets this pad's graph to cover the coordinates spanning *bounds*. If *scaleOnResize* is true, the graph's coordinate system will resize with the pad.
- `ofRectangle getBounds()`
    - Returns an *ofRectangle* for the graph of this pad
- `void reset()`
    - Moves the cursor to the exact center of the pad's graph

#### Instantiation
> Constructors:  
`ofxXRS2dPad(string label)`  
`ofxXRS2dPad(string label, ofRectangle bounds)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRS2dPad* pad;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    pad = panel->add2dPad("2D Pad Label");
}
```
To Instantiate Free-Floating:  
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;

/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* comp = new ofxXRS2dPad("2D Pad Label");
    comp->setPosition(10, 10);
    components.emplace_back(comp);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```
### Knob
Like a slider but visualized as a circle rather than a rectangle.


> Class: `TODO; Not yet implemented`

#### Methods
Under construction.
#### Instantiation
Under construction.

### Large Button
Works exactly like a button but is free-standing and can be given custom dimensions. Can be either rectangular or circular, set via an **ofxXRSSimpleButton::BUTTON_SHAPE** passed during instantiation or to the *setShape()* function.
<div align=justify>
<img width="33%" src="./img/components/largeButton.png"/>
</div>

>Class: `ofxXRSSimpleButton`

#### Methods
- `void setType(ofxXRSSimpleButton::TYPE_BUTTONS type)`
    - Sets the type of this large button to *type*
- `void setShape(ofxXRSSimpleButton::BUTTON_SHAPES shape)`
    - Sets the shape of this large button to *shape*
- `void setColor(ofColor color)`
    - Sets the color of this large button to *color*
- `void setToggleColor(ofColor color)`
    - Sets the color of this large button to *color* when it is clicked if its type is TYPE_BUTTON, or while it is enabled if its type is TYPE_TOGGLE
- `void setPos(ofPoint point)` | `void setPos(float x, float y)`
    - Sets the position of the top-left corner of this large button to either *point* or (*x*, *y*)
- `void setName(string name, float xOffset, float yOffset)`
    - Sets the name of this large button, which will be drawn at (*xOffset*, *yOffset*) distance from the top-left of this large button

#### Instantiation
> Constructors:  
`ofxXRSSimpleButton::setup(float x, float y, float width, float height, bool useListener)`  
`ofxXRSSimpleButton::setup(float x, float y, float width, float height, bool useListener, bool manualRender, TYPE_BUTTONS type, BUTTON_SHAPES shape, ofColor color)`

To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

ofxXRSSimpleButton button;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    button.setup(10, 10, 100, 100, true, false, TYPE_BUTTON, BUTTON_RECT, ofColor::green);
    button.setName("Large Button");

    // Since we passed "false" to the constructor's "manualRender" parameter,
    // we do not need to call draw() on button in ofApp::draw().
}
```

### Large Image Button
Works exactly like a Large Button but the sprite will be an image given during instantiation rather than a circle or rectangle. 

!> Note that the button will appear *exactly* as its source image; there will be no border, cropping, resizing, or blending.
<div align=justify>
<img width="33%" src="./img/components/largeImageButton.png"/>
</div>

>Class: `ofxXRSSimpleButton`

#### Methods
- Since they are the same class, *ofxXRSSimpleButton*, Large Image Buttons have access to the same methods as [Large Buttons](components.md#large-button); however, methods that affect the drawing of the button, like `setShape()` and `setColor()`, will have no effect.
- `void setAsAnimationButton(int time)`
    - Sets this button to animate using an *ofFBO* with *time* milliseconds between frames (Needs testing)

#### Instantiation
> Constructors:  
`ofxXRSSimpleButton::setup(float x, float y, string pathToImg, bool isAnimated, bool useListener, bool manualRender, TYPE_BUTTONS type)`

To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

ofxXRSSimpleButton img;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    img.setup(10, 10, "img/button.png", false, true, false, TYPE_BUTTON);
    img.setName("Large Image Button");

    // Since we passed "false" to the constructor's "manualRender" parameter,
    // we do not need to call draw() on img in ofApp::draw().
}
```

<p>&nbsp;</p>

## Monitors
Monitors are components that listen to and report the status of some aspect of the stage or show.

The following is a list of monitors built into the panel system, meaning they can be instantiated and placed individually, but **ofxXRSPanel** and **ofxXRSFolder** natively support managing and adding these components.
- Label
- Wave Monitor
- Value Plotter

### Label
Simply displays a string of text. The alignment of the text can be set via an **ofxXRSAlignment** passed to the *setLabelAlignment()* function
<div align=justify>
<img width="75%" src="./img/components/label.png"/>
</div>

>Class: `ofxXRSLabel`

#### Methods
*ofxXRSLabel* has no special methods. It's a label. Use all the label methods from [Common Methods](/components#common-methods).

#### Instantiation
> Constructors:  
`ofxXRSLabel(string label)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSLabel* label;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    label = panel->addLabel("Label");
}
```
### Wave Monitor
Smoothly oscillates between a negative and positive **amplitude** at a speed of **frequency** waves per second.  
Not sure why anyone would use this.
<div align=justify>
<img width="75%" src="./img/components/waveMonitor.png"/>
</div>

>Class: `ofxXRSWaveMonitor`

#### Methods
- `void setAmplitude(float amp)`
    - Sets the amplitude of the wave to *amp*. Amplitude is a multiplier that affects the vertical height of the wave and should be a value between 0 and 1.
- `void setFrequency(float freq)`
    - Sets the frequency of the wave to *freq*, within this monitor's frequency limit.
- `void setFrequencyLimit(float limit)`
    - Sets the frequency limit of the wave.

#### Instantiation
> Constructors:  
`ofxXRSWaveMonitor(string label, float frequency, float amplitude)`

To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSWaveMonitor* monitor;


/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    monitor = panel->addWaveMonitor("Wave Monitor Label", 5.0f, 0.5f);
}
```

To Instantiate Free-Floating: 
```cpp
/**
 * ofApp.h
 **/
std::vector<ofxXRSComponent*> components;



/**
 * ofApp.cpp
 **/
void ofApp::setup() {
    ofxXRSComponent* component = new ofxXRSWaveMonitor("Wave Monitor Label", 5.0f, 0.5f);
    components.emplace_back(component);
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

### Value Plotter
Charts a given **value** between a set **min** and **max** over time. Useful for performance and confidence monitors. Have whatever value is being tracked passed to `setValue()` in the update function.
<div align=justify>
<img width="75%" src="./img/components/valuePlotter.png"/>
</div>

>Class: `ofxXRSValuePlotter`

#### Methods
- `void setValue(float value)`
    - Sets the current value of this plotter to *value*
- `void setMin(float min)`
    - Sets the minimum value of this value plotter to *min*
- `void setMax(float max)`
    - Sets the maximum value of this value plotter to *max*
- `void setRange(float min, float max)`
    - It's `setMin()` and `setMax()` together at last!
- `void setSpeed(float speed)`
    - Sets how fast the chart scrolls across the graph to *speed*
- `void setDrawMode(ofxXRSDrawMode drawMode)`
    - Sets the draw mode of this value plotter to *drawMode*. Currently supported draw modes are: OUTLINE, FILLED, LINES, and POINTS
- `float getMin()`
    - Returns a float of the minimum value of this plotter.
- `float getMax()`
    - Returns a float of the maximum value of this plotter.
- `float getRange()`
    - Returns a float of maximum minus the minimum value of this plotter.

#### Instantiation
> Constructors:  
`ofxXRSValuePlotter(string label, float min, float max)`  


To Instantiate in a Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSValuePlotter* plotter;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    plotter = panel->addValuePlotter("Value Plotter Label", 0.0f, 50.0f);
    plotter->setValue(25.0f);
}
```

To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

ofxXRSValuePlotter* plotter;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    plotter = new ofxXRSValuePlotter("Value Plotter Label", 0.0f, 50.0f);
    plotter->setPosition(10.0f, 10.0f);
    plotter->setValue(25.0f);
}

void ofApp::draw() {
    plotter->draw();
}
```

<p>&nbsp;</p>

## Organizers
Organizers serve no functional purpose - they are used, as the name implies, to organize your application's monitors and controls. 

!> Headers, footers, and folders work ***exclusively*** with Panels. Do not try to put a folder in a folder.

### Panel
Groups together multiple components into an on-screen panel. Constructor takes two floats for the panel's X,Y coordinates or an **ofxXRSPanelAnchor**
<div align=justify>
<img width="75%" src="./img/braitsch.png"/>
</div>

> Class: `ofxXRSPanel`

#### Methods
- `void setOpacity(float opacity)`
    - Sets the opacity of this panel and the components within to *opacity*, between 0 and 1.
- `void setLabelAlignment(ofxXRSAlignment alignment)`
    - Sets how label text is justified to *alignment*
- `void setAutoDraw(bool autoDraw)`
    - Sets whether or not this panel automatically draws itself and its components (if false, you will have to call `draw()` on this panel in your app's *draw()* method)
- `ofxXRSHeader* addHeader(string label, bool draggable)`
    - Adds a header to this panel and returns a pointer to it. A panel can only have one header. Any subsequent `addHeader()` calls will override the previous header.
- `ofxXRSFolder* addFolder(string label, ofColor color)`
    - Adds a folder to the bottom of this panel and returns a pointer to it.
- `ofxXRSDropDown* addDropdown(string label, std::vector<string> options)`
    - Adds a dropdown populated with *options* to the bottom of this panel and returns a pointer to it.
- `ofxXRSFooter* addFooter()`
    - Adds a footer to the bottom of this panel and returns a pointer to it. A panel can only have one footer. It cannot have a label (yet). A footer will always be on the bottom of the panel regardless of in what order it was added.
- `ofxXRSHeader* getHeader()`
    - Returns a pointer to this panel's header, or nullptr if it has none.
- `ofxXRSFooter* getFooter()`
    - Returns a pointer to this panel's footer, or nullptr if it has none.
- `ofxXRSFolder* getFolder(string label)`
    - Returns a pointer to the child *ofxXRSFolder* with label *label*, or nullptr if a child could not be found.
- `ofxXRSDropdown* getDropdown(string label)`
    - Returns a pointer to the child *ofxXRSDropdown* with label *label*, or nullptr if a child could not be found.

#### Instantiation
> Constructors:  
`ofxXRSPanel(float x, float y)`  
`ofxXRSPanel(ofxXRSPanelAnchor anchor)`


!> Using X,Y coordinates calculated via the application window's width and height is recommended over using an **ofxXRSPanelAnchor** - they do not play nice with resizing windows.
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
}
```

### Header
A special label for a panel that automatically places itself at the top of the panel and allows the panel to be repositioned
<div align=justify>
<img width="75%" src="./img/components/header.png"/>
</div>

>Class: `ofxXRSHeader`

#### Methods
*ofxXRSHeader* has no special methods.

#### Instantiation
> Constructors:  
`ofxXRSHeader(string label = "")`


To add a header to your panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSHeader* header;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    header = panel->addHeader("Header Label");
}
```

### Footer
A special label for a panel that automatically places itself at the bottom of the panel and allows the panel to be resized
<div align=justify>
<img width="75%" src="./img/components/footer.png"/>
</div>

>Class: `ofxXRSFooter`

#### Methods
*ofxXRSFooter* has no special methods.

#### Instantiation
> Constructors:  
`ofxXRSFooter()`


To add a footer to your panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSFooter* footer;


/**
 * ofApp.cpp
 **/
ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    footer = panel->addFooter();
}

```

### Folder
Groups together multiple components within a panel into a labeled, collapsable folder view.
<div align=justify>
<img width="75%" src="./img/components/folder.png"/>
</div>

>Class: `ofxXRSFolder`

#### Methods
The folder has no special methods that have not already been detailed in [Common Methods](components.md#common-methods)

#### Instantiation
> Constructors:  
`ofxXRSFolder(string label, ofColor color = ofColor::white)`

To Instantiate in Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;
ofxXRSFolder* folder;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel(ofxXRSPanelAnchor::TOP_LEFT);
    folder = panel->addFolder("Folder");
    folder->addButton("Child Button");
    folder->addToggle("Child Toggle");
}

```

To Instantiate Free-Floating:
```cpp
/**
 * ofApp.h
 **/

std::vector<ofxXRSComponent*> components;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    ofxXRSComponent* folder = new ofxXRSFolder("Folder");
    folder->setPosition(10, 10);
    folder->addButton("Child Button");
    folder->addToggle("Child Toggle");
}

void ofApp::draw() {
    for(auto& component : components) {
        component->draw();
    }
}
```

!>Note: Might need to add folder's children to *components* and *draw()* them as well. You might even only be able to add folders to panels. Idk I ain't tried this yet.


### Scroll View
Similar to a folder, except instead of expanding to show its children via a dropdown, it is a fixed size and the user can scroll through the options when mousing over the component.

>Class: `ofxXRSScrollView`

