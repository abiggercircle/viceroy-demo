# Viceroy JS Client

Viceroy is the package for applications that run fully managed advertising with Digined. Using a few lines application developers, can integrate Google Tag Manager and various event tracking mechanisms. Each installation has a unique filename and secret. These credentials are mapped to GTM containers and other tracking pixels under the hood. 

There is also a queuing mechanism so that no events are missed. All events that occur before the load of the GTM snippet are queued and fired when the GTM is loaded.

## Integration of Viceroy

This repository contains various examples that demonstrate how Viceory can be easily integrated with your application.

The steps to include viceroy are:

### Step 1
Include the Javascript file in your application. If you do not have this, get your unique filename and secret from Digined (details below).

```
<script type="text/javascript" src="https://viceroy.soda.social/viceroy/{{FILENAME_GOES_HERE}}?secret={{SECRET_GOES_HERE}}"></script>
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
Set up the application events that Viceroy needs to track. There are two ways to track events:

##### Add a class and data attributes in the element you wish to track

```html
<button class="viceroy" data-viceroy-event-type="click" data-viceroy-event-data='{"key1": "val1", "key2": "val2"}'>Press me!</button>
```
More info:
* Add class **viceroy** to enable tracking on element
* **data-viceroy-event-type** is the interaction on which the data will be pushed. Examples are click, hover, mousedown, mouseup, etc. There is an exhuaustive list of events available [here](http://www.w3.org/wiki/List_of_events).
* **data-viceroy-event-data** is the data that needs to pushed on the event. Make sure the data is a valid JSON.

##### Call Viceroy through a Javascript function call

You can push data explicitly using
```javascript
window.viceroy.pushDataEvent({foo: 1, bar: "Hello"});
```

and check the data stack using
```javascript
window.viceroy.getDataLayer();
```

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

* window.viceroy.parsePayload - parse your JSON string
* window.viceroy.getEventList - list of all the events that are currently being listened to
* window.viceroy.getMissedEvents - View all the events that are in the Queue

## Issues, Support and Authentication

* For Issues with the package and its implementation, please post an issue on Github.
* For Support, questions and requests, post an Issue on Github with an appropriate tag.
* For Authentication and access to Viceroy, send an email to viceroy {[at}] digined {[.dot.}] com