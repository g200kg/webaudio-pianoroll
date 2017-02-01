# webaudio-pianoroll
[Polymer] Pianoroll GUI library for Web application / relevant to webaudio-controls

`webaudio-pianoroll` is a Polymer GUI module for pianoroll.
Using webaudio-pianoroll with webaudio-controls makes it easy to build webaudio application.

`webaudio-controls` is here :  
[webaudio-controls](https://github.com/g200kg/webaudio-controls)

* Editmode - `webaudio-pianoroll` has four edit mode, `gridmono`, `gridpoly`, `dragmono` and `dragpoly`. `grid` types are just toggle the grid cell by clicking, and the note length is always 1 tick. that matches to rhythm machine like one. The other hand, `drag` types can specify note length by dragging. that are matches generic pianoroll apps.
* Many customize options.
* Play support - `webaudio-pianoroll` has not direct sound generation function, but has play support function.

Live Demo page is available.  
'gridmono' mode demo : [Live Demo](./index.html)  
'dragpoly' timebase=480 mode demo : [Live Demo](./index3.html)  

---
## Usage

- Install Polymer
> Use command 'bower install --save Polymer/polymer', if you use bower. Or download zipped file and deploy appropriately.

- load webcomponents.js and polymer in your HTML  
> &lt;script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"&gt;&lt;/script&gt;<br/>
  &lt;link rel="import" href="bower_components/polymer/polymer.html"&gt;

- load `webaudio-pianoroll` in your HTML  
> &lt;link rel="import" href="bower_components/webaudio-pianoroll/webaudio-pianoroll.html" &gt;

- insert `webaudio-pianoroll` element
> &lt;webaudio-pianoroll&gt;&lt;/webaudio-pianoroll&gt;  

## Attributes

|Attribute|Options|Default   |Description               |
|---------|-------|----------|--------------------------|
|**width**    |Number |640       | width of element in px   |
|**height**   |Number |320       | height of element in px  |
|**editmode** |String |"gridmono"| combination of "grid"/"drag" + "mono"/"poly"|
|**timebase** |Number |16        | time resolution of 1 bar, <br/>(1 bar / timebase = 1 tick)  |
|**xrange**   |Number |16        | time axis view range in tick|
|**yrange**   |Number |16        | y axis view range in note number|
|**xoffset**  |Number |0         | time axis offset in tick|
|**yoffset**  |Number |60        | y axis offset in note number|
|**grid**     |Number |4         | time axis grid density in tick|
|**xruler**   |Number |24        | time axis ruler height in px|
|**yruler**   |Number |24        | y axis ruler width in px|
|**octadj**   |Number |-1        | ruler octave value adjust <br/>(-1 : 60=C4)|
|**cursor**   |Number |0         |current play position in tick|
|**markstart**|Number |0         | play range start marker position in tick|
|**markend**  |Number |16        | play range end marker position in tick|
|**collt**    |String |"#ccc"    | score background (light part) color|
|**coldk**    |String |"#aaa"    | score background (dark part) color|
|**colgrid**  |String |"#666"    | score grid color|
|**colnote**  |String |"#f22"    | note color |
|**colnotesel**|String|"#0f0"    | selected note color (for editmode="drag")|
|**colnoteborder**|String|"#000" | note border color|
|**colrulerbg**|String|"#666"    | ruler background color|
|**colrulerfg**|String|"#fff"    | ruler foreground color|
|**colrulerborder**|String|"#000"| ruler border color|
|**bgsrc**|String|null| background image url. To make visible this, you should set collt/coldk non-opaque with 'rgba(r,g,b,a)' style. |
|**cursorsrc**|String| internal resource| playcursor image url|
|**cursoroffset**|Number|0|playcursor image x offset in px|
|**markstartsrc**|String|internal resource| markstart image url|
|**markstartoffset**|Number|0| markstart image x offset in px|
|**markendsrc**|String|internal resource| markend image url|
|**markendoffset**|Number|-24| markend image  x offset in px|
|**kbsrc**|String|internal resource| keyboard image url|
|**kbwidth**|Number|40|keyboard image width in px|
|**loop**     |Number |1         | loop play|
|**preload**|Number |1| data preload when play in sec|
|**tempo**|Number|120|tempo when play|


## Functions

|Function|Description|
|--------|-----------|
|**redraw()**| redraw all|
|**getMMLString()**| get MML string of current data. <br/>Note that this function is for `mono` type editmode.|
|**setMMLString(str)**| set MML string to webaudio-pianoroll. <br/>Note that this function is for `mono` type editmode.|
|**locate(tick)**| set cursor to specified tick|
|**play(audioContext, callback, starttick)**|play current data. `webaudio-pianoroll` does not generate sound directly, but it passes necessary information to the specified callback function. `audioContext` is used to control the time axis. If `starttick` is not specified, play from current cursor position.|

## Callback
play() function passes necessary data for playing to callback function like :
`callback({t:noteOnTime, g:noteOffTime, n:noteNumber})`

Here the noteOnTime and noteOffTime is audioContext timeline value.

## DataStructure
If you want to access directly to sequence data, you can touch the `DOMElement.sequence`.

`DOMElement.sequence` is an Array of noteEvents. Here the noteEvent is a object of one note infomation of:  
`{t:noteOnTick g:noteLength n:noteNumber}`

## License
`webaudio-pianoroll` is licensed under the Apache License, Version 2.0
