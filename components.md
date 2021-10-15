# Components
Components are the individual UI elements that make up your application.

They are divided into three types: ``Controls``, ``Monitors``, and ``Organizers``

### Common Methods
What follows is a list of methods that can be called on any object and that you will probably find useful.

#### Panel Components
These methods can be called on any object that interacts with the Panel system - in other words, any component that inherits ofxXRSComponent. In other other words, any component except Large Buttons and Knobs.

 - `ofxXRSComponent* getComponent(ofxXRSType type, string label)` | `getComponent(string label)`
     - Returns a pointer to the child object component matching *type* and/or *label*, or nullptr if no matching children could be found. Note that this method returns a generic ofxXRSComponent - use a more specific getter like `getButton(string label)` to get back an *ofxXRSButton\** or `getToggle(string label)` to get back an *ofxXRSToggle\**, etc. if you need to access component-specific methods.
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
    


#### Free-floating Components

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
>Class: `ofxXRSButton`
<div align=justify>
<img width="75%" src="./img/components/button.png"/>
</div>

#### Methods
`ofxXRSButton` has no unique methods. You click it and something happens! That's it!

#### Instantiation
To Instantiate in Panel:
```cpp
/**
 * ofApp.h
 **/

ofxXRSPanel* panel;


/**
 * ofApp.cpp
 **/

void ofApp::setup() {
    panel = new ofxXRSPanel();
    panel->addButton("Button Label");
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
    ofxXRSComponent* component;
    component = new ofxXRSButton("Button Label");
    component->setPosition(x, y);
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
>Class: `ofxXRSToggle`
<div align=justify>
<img width="75%" src="./img/components/toggle.png"/>
</div>

#### Methods
- `void toggle()`
    - Toggles this component from checked to unchecked or vice versa.
- `void setChecked(bool checked)`
    - Sets this component's checked state. Like `ofxXRSToggle::toggle()`, but you have control over the new state instead of just swapping.
- `bool getChecked()`
    - Returns a boolean for whether or not this component is checked or not.

#### Instantiation

### Text Input
A text box where the user can input a string.
>Class: `ofxXRSTextInput`
<div align=justify>
<img width="75%" src="./img/components/textInput.png"/>
</div>

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

### Slider
A control that sets the value of something between a minimum and maximum range.
>Class: `ofxXRSSlider`
<div align=justify>
<img width="75%" src="./img/components/slider.png"/>
</div>

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

### Color Picker
A control that drops down to a color wheel when clicked which sets the color of something using **ofColor**
>Class: `ofxXRSColorPicker`
<div align=justify>
<img width="75%" src="./img/components/colorPicker.png"/>
</div>

#### Methods
- `void setColor(ofColor color)` | `setColor(int hex)` | `setColor(int r, int g, int b, int a)`
    - Sets the current color value of this color picker to *color* or *hex*, as if it had been selected by the user.
- `ofColor getColor()`
    - Returns an ofColor for the current color value of this color picker.


#### Instantiation

### Dropdown
A control that drops down to a list of selections from which the user selects a single option
>Class: `ofxXRSDropdown`
<div align=justify>
<img width="75%" src="./img/components/dropdown.png"/>
</div>

#### Methods
- `void select(int index)`
    - Selects the *index*-th option from the Dropdown as if it had been selected by the user.
- `int size()`
    - Returns an int for how many options are in the dropdown

#### Instantiation


### Button Matrix
>Class: `ofxXRSMatrix`
<div align=justify>
<img width="75%" src="./img/components/buttonMatrix.png"/>
</div>

A control that allows the user to toggle one or several buttons in a grid; most often used for cue lists.
### 2D Coordinate Pad
>Class: `ofxXRS2dPad`
<div align=justify>
<img width="75%" src="./img/components/2dpad.png"/>
</div>

A control that allows the user to see and set the 2D Position (X, Y) of whatever aspect of the stage or show is hooked up to it.
### Knob
> Class: `TODO`

Like a slider but visualized as a circle rather than a rectangle.
### Large Button
>Class: `ofxXRSSimpleButton`
<div align=justify>
<img width="33%" src="./img/components/largeButton.png"/>
</div>

Works exactly like a button but is free-standing and can be given custom dimensions. Can be either rectangular or circular, set via an **ofxXRSSimpleButton::BUTTON_SHAPE** passed during instantiation or to the *setShape()* function.
### Large Image Button
>Class: `ofxXRSSimpleButton`
<div align=justify>
<img width="33%" src="./img/components/largeImageButton.png"/>
</div>

Works exactly like a Large Button but the sprite will be an image given during instantiation rather than a circle or rectangle. 

!> Note that the button will appear *exactly* as its source image; there will be no border, cropping, resizing, or blending.

<p>&nbsp;</p>

## Monitors
Monitors are components that listen to and report the status of some aspect of the stage or show.

The following is a list of monitors built into the panel system, meaning they can be instantiated and placed individually, but **ofxXRSPanel** and **ofxXRSFolder** natively support managing and adding these components.
- Label
- Wave Monitor
- Value Plotter

### Label
>Class: `ofxXRSLabel`
<div align=justify>
<img width="75%" src="./img/components/label.png"/>
</div>

Simply displays a string of text. The alignment of the text can be set via an **ofxXRSAlignment** passed to the *setLabelAlignment()* function
### Wave Monitor
>Class: `ofxXRSWaveMonitor`
<div align=justify>
<img width="75%" src="./img/components/waveMonitor.png"/>
</div>

Smoothly oscillates between a negative and positive **amplitude** at a speed of **frequency** waves per second.  
Not sure why anyone would use this.
### Value Plotter
>Class: `ofxXRSValuePlotter`
<div align=justify>
<img width="75%" src="./img/components/valuePlotter.png"/>
</div>

Charts a given **value** between a set **min** and **max** over time. Useful for performance and confidence monitors.

<p>&nbsp;</p>

## Organizers
Organizers serve no functional purpose - they are used, as the name implies, to organize your application's monitors and controls. 

!> Headers, footers, and folders work ***exclusively*** with Panels. Do not try to put a Large Button in a Folder.

### Panel
> Class: `ofxXRSPanel`
<div align=justify>
<img width="75%" src="./img/braitsch.png"/>
</div>

Groups together multiple components into an on-screen panel. Constructor takes two floats for the panel's X,Y coordinates or an **ofxXRSPanelAnchor**

!> Using X,Y coordinates calculated via the application window's width and height is recommended over using an **ofxXRSPanelAnchor** - they do not play nice with resizing windows.


### Header
>Class: `ofxXRSHeader`
<div align=justify>
<img width="75%" src="./img/components/header.png"/>
</div>

A special label for a panel that automatically places itself at the top of the panel and allows the panel to be repositioned


### Footer
>Class: `ofxXRSFooter`
<div align=justify>
<img width="75%" src="./img/components/footer.png"/>
</div>

A special label for a panel that automatically places itself at the bottom of the panel and allows the panel to be resized


### Folder
>Class: `ofxXRSFolder`
<div align=justify>
<img width="75%" src="./img/components/folder.png"/>
</div>

Groups together multiple components within a panel into a labeled, collapsable folder view.

### Scroll View
>Class: `ofxXRSScrollView`

Similar to a folder, except instead of expanding to show its children via a dropdown, it is a fixed size and the user can scroll through the options when mousing over the component.