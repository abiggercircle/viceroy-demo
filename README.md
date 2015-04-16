# Viceroy JS Client

Viceroy is the package for applications that run fully managed advertising with Digined. Using a few lines application developers, can integrate Google Tag Manager and various event tracking mechanisms. Each installation has a unique filename and secret. These credentials are mapped to GTm containers and other tracking pixels under the hood. 

There is also a queuing mechanism so that no events are missed. All events that occur before the load of the GTM snippet are queued and fired when the GTM is loaded.

## Integration of Viceroy

This repository contains various examples that demonstrate how Viceory can be easily integrated with your application.

The steps to include viceroy are:

### Step 1
Include the Javascript file in your application. If you do not have this, get your unique filename and secret from Digined (details below).

### Step 2
Initialize Viceroy with the default data layer parameters.


### Step 3
Set up the application events that Viceroy needs to track.

## Customization options for Viceroy

## Issues, Support and Authentication

* For Issues with the package and its implementation, please post an issue on Github.
* For Support and questions, post an Issue on Github with an appropriate tag.
* For Authentication and access to Viceroy, send an email to viceroy {[at}] digined {[.dot.}] com
