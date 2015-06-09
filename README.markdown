# WebSynthUI
HTML5 UI components for synthesizer controls.  

## Installation

WebSynthUI requires [interact.js](http://interactjs.io).  
Include `src/vendor/interact/interact.js`, `src/js/web-synth-ui.js` and `src/css/web-synth-ui.css` in your HTML document:  

	<script type="text/javascript" src="<path-to-web-synth-ui>/src/vendor/interact/interact.js"></script>
	<script type="text/javascript" src="<path-to-web-synth-ui>/src/js/web-synth-ui.js"></script>
	<link rel="stylesheet" type="text/css" href="<path-to-web-synth-ui>/src/css/web-synth-ui.css">

## Usage

WebSynthUI currently provides three types of control: Knob, Segmented Switch and Toggle Switch.  

### Knob

##### HTML:

	<div class="web-synth-ui knob" id="knob">
		<div class="handle"></div>
	</div>

##### JavaScript:

	var knob = new Knob(document.getElementById('knob'), {
		onUpdate: function(value) {
			// The current value is passed to the onUpdate function when the knob is turned.
		}
	});

	// Update the knob to display and send its current value (optional):
	knob.update();

##### Options:

The `Knob()` constructor accepts several options:

	var knob = Knob(document.getElementById('knob'), {
		minAngle: -135.0,
		maxAngle: 135.0,
		angle: -135.0,
		minValue: 0.0,
		maxValue: 1.0,
		speed: 1.0,
		onUpdate: function(value) {
			...
		}
	});

Options may also be provided as data attributes:

	<div class="web-synth-ui knob" id="knob" 
		data-min-angle="-135" 
		data-max-angle="135" 
		data-angle="-135" 
		data-min-value="0" 
		data-max-value="1" 
		data-speed="1">
		<div class="handle"></div>
	</div>

Options passed to the constructor take precedence over options provided as data attributes. The following options are available:  

##### minAngle (data-min-angle): 
The angle that restricts the knob's rotation to the left (in degrees). Defaults to `-135.0`.  

##### maxAngle (data-max-angle): 
The angle that restricts the knob's rotation to the right (in degrees). Defaults to `135.0`.  

##### angle (data-angle): 
The initial angle (in degrees). Defaults to `-135.0`.  

##### minValue (data-min-value): 
The value produced when the knob is rotated fully to the left. Defaults to `0.0`.  

##### maxValue (data-max-value): 
The value produced when the knob is rotated fully to the right. Defaults to `1.0`.  

##### speed (data-speed): 
The speed of rotation. Defaults to `1.0`. When set to `1.0`, the knob rotates 1 degree per pixel of mouse movement. Values below `1.0` slow the rotation down and make the knob feel less responsive but more accurate. Values above `1.0` speed the rotation up and make the knob feel more responsve but less accurate.  

### Segmented Switch

##### HTML:

	<div class="web-synth-ui switch segmented-switch" id="segmented-switch">
		<div class="pole selected" data-value="1">1</div>
		<div class="pole" data-value="2">2</div>
		<div class="pole" data-value="3">3</div>
	</div>

* Include one `.pole` element for each switch segment. 
* Use `.selected` to indicate the segment that is selected by default. 
* Each segment should have a `data-value` attribute to provide a value when the segment is selected.

##### JavaScript

	var switch = new SegmentedSwitch(document.getElementById('segmented-switch'), {
		onUpdate: function(index, value) {
			// The selected segment index and value are passed to the onUpdate function when the switch is clicked.
		}
	});

	// Update the switch to display and send its current value (optional):
	switch.update();

### Toggle Switch

##### HTML:

	<div class="web-synth-ui switch toggle-switch" id="toggle-switch">
		<div class="indicator"></div>
	</div>

##### JavaScript

	var switch = new ToggleSwitch(document.getElementById('toggle-switch'), {
		onUpdate: function(on) {
			// The switch state (boolean) is passed to the onUpdate function when the switch is clicked.
		}
	});

	// Update the switch to display and send its current state (optional):
	switch.update();

View `/demo/index.html` for examples of each control's the default behaviour.  

## License
WebSynthUI is made available under the MIT License. See LICENSE.txt for details.  

## Credits
WebSynthUI was created by [Tony Wallace](http://tonywallace.ca).  
