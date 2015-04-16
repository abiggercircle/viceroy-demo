# Viceroy JS Client

Viceroy is the package for applications that run fully managed advertising with Digined. Using a few lines application developers, can integrate Google Tag Manager and various event tracking mechanisms. Each installation has a unique filename and secret. These credentials are mapped to GTm containers and other tracking pixels under the hood. 

There is also a queuing mechanism so that no events are missed. All events that occur before the load of the GTM snippet are queued and fired when the GTM is loaded.

