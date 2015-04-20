# Viceroy JS Client

Viceroy is the package for applications that run fully managed advertising with [Digined](https://digined.com/) / [Soda](https://meetsoda.com/). Using a few lines, application developers can integrate [Google Tag Manager](https://www.google.com/tagmanager/) and various event tracking mechanisms with ease. Each installation has a unique filename and secret. These credentials are mapped to GTM containers and other tracking pixels under the hood. 

Viceroy has a smart mechanism so that no events are ever missed. All events that occur before the load of the GTM snippet are queued and fired when the GTM is loaded.

## Integration of Viceroy

This repository contains various examples that demonstrate how Viceory can be easily integrated with your application.

The steps to include viceroy are:

### Step 1
Include the Viceroy Javascript file in your application. To do this, you need an account with us. Get your unique filename and secret by contacting [Digined](https://digined.com/) (details below).

```html
<script type="text/javascript" src="https://viceroy.soda.social/viceroy/{{FILENAME_GOES_HERE}}?secret={{SECRET_GOES_HERE}}"></script>
```

If your application is not registered, you may use the sandbox mode for integration. Below is an example of including the Viceroy library in sandbox mode.

```html
<script type="text/javascript" src="https://viceroy.soda.social/viceroy/sandbox.js"></script>
```

### Step 2
Initialize Viceroy with the default data layer parameters.

```javascript
<script type="text/javascript">
            window.viceroy = new Viceroy({
                defaults: 
                    {
                       'variable-number'   : 123,
                       'variable-string': 'Hello World',
                       'variable-device' : 'mobile'
                    }
            });
</script>
```

### Step 3
Set up the application events in your page that Viceroy needs to track. There are two ways to track events:

##### 1. Add a class and data attributes in the element you wish to track

```html
<button class="viceroy" data-viceroy-event-type="click" data-viceroy-event-data='{"key1": "val1", "key2": "val2"}'>Press me!</button>
```
More info:
* Add class **viceroy** to enable tracking on element
* **data-viceroy-event-type** is the interaction on which the data will be pushed. Examples are click, hover, mousedown, mouseup, etc. There is an exhaustive list of supported DOM events further in the documentation.
* **data-viceroy-event-data** is the data that needs to pushed on the event. Make sure the data is a valid JSON.

##### 2. Call Viceroy through a Javascript function call

You can push data explicitly using
```javascript
window.viceroy.pushDataEvent({foo: 1, bar: "Hello"});
```

and check the data stack using
```javascript
window.viceroy.getDataLayer();
```

:warning: **IMPORTANT:** The ```data-viceroy-event-type``` and ```data-viceroy-event-data``` paramaeters are placeholders. Please make sure that you use something that makes more sense in an actual implementation. 

## Advanced API usage

### Initialization

```javascript
  window.viceory = new Viceroy({
        defaults        : {},
        debug           : 'true', // Allows for debugging (logging/warnings/errors)
        element         : {
            selector        : '.viceroy', // Possible selectors that can be used to recognize the elements
            eventDataAttr   : 'data-viceroy-event-data', // Element's attribute to retrieve event data
            eventTypeAttr   : 'data-viceroy-event-type' // Element's attribute to determine what event to listen on
        }
  });
```

* **defaults** - the data parameters that are always sent when an event is fired.

* **debug** - ("true" or "false") This will switch on/off debug mode. Debug mode will log, warn and throw errors to the browser console (if available).

* **element** - (object). Object Params are selector, eventDataAttr and eventTypeAttr

### Utility Functions

* **window.viceroy.parsePayload** to parse your JSON string
* **window.viceroy.getEventList** to list of all the events that are currently being listened to
* **window.viceroy.getMissedEvents** to view all the events that are in the Queue

## List of supported DOM events

* onautocompleteerror
* onautocomplete
* onwaiting
* onvolumechange
* ontoggle
* ontimeupdate
* onsuspend
* onsubmit
* onstalled
* onshow
* onselect
* onseeking
* onseeked
* onscroll
* onresize
* onreset
* onratechange
* onprogress
* onplaying
* onplay
* onpause
* onmousewheel
* onmouseup
* onmouseover
* onmouseout
* onmousemove
* onmouseleave
* onmouseenter
* onmousedown
* onloadstart
* onloadedmetadata
* onloadeddata
* onload
* onkeyup
* onkeypress
* onkeydown
* oninvalid
* oninput
* onfocus
* onerror
* onended
* onemptied
* ondurationchange
* ondrop
* ondragstart
* ondragover
* ondragleave
* ondragenter
* ondragend
* ondrag
* ondblclick
* oncuechange
* oncontextmenu
* onclose
* onclick
* onchange
* oncanplaythrough
* oncanplay
* oncancel
* onblur
* onabort
* onwebkitfullscreenerror
* onwebkitfullscreenchange
* onwheel
* onselectstart
* onselectionchange
* onsearch
* onreadystatechange
* onpointerlockerror
* onpointerlockchange
* onpaste
* oncut
* oncopy
* onbeforepaste
* onbeforecut
* onbeforecopy
* ontouchstart
* ontouchend
* ontouchmove
* ontouchcancel

## Issues, Support and Authentication

* For Issues with the package and its implementation, please post an issue on Github.
* For Support, questions and requests, post an Issue on Github with an appropriate tag.
* For Authentication and access to Viceroy, send an email to viceroy {[at}] digined {[.dot.}] com
