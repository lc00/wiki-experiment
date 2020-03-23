## Big Ideas

* A particular serviceWorker runs completely independently of the page it works for- different process, and they can't see each other directly
  * That means the page can't see its service workers' `console.log`s on the page
  * It doesn't have access to the DOM or anything in JS scope
* Service workers are primarily for intercepting, caching, and responding to fetch requests
  * Can also manage push notifications
* Service workers are scoped (default scope is anything under the location of the file, can be narrowed to a particular range of API requests)

### Gotchas

* They don't work in private tabs in Firefox
* Firefox allows you to inspect running service workers at `about:debugging` (scroll down)
* "Fetch" events are much broader than just `fetch`, and also includes document navigation and static assets
* Service workers only work over HTTPS (and localhost)
* Turning on an active service worker has a little bit of overhead, so don't run fetch requests through it if you don't have to

## Registering a Service Worker

This is the only thing that actually goes in the app:

```js
if ("serviceWorker" in navigator)(
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("/service-worker.js").then(() => console.log("Registered!"))
  })
)
```

Logging the registration is optional.

## Service Worker Events

### Install

Runs if the service worker has never been installed, or if the service worker it got is different than the active one

```js
self.addEventListener("install", event => {
  event.waitUntil(
    // Preload anything for new cache
  )
})
```

### Activate

Runs after every tab using the old service worker is closed

```js
self.addEventListener("activate", event => {
  event.waitUntil(
    self.skipWaiting() // Don't wait for other tabs to close

    // Delete entire old cache

    self.clients.claim() // Immediately turns on SW without waiting for a navigation event
  )
})
```

### Fetch

Runs on any network activity.

```js
self.addEventListener("fetch", fetchEvent => {
  fetchEvent.respondWith(someResponse) // Can stub one out with `new Response(body, options)`
})
```

## Cache Methods

### All Caches

```js
caches.keys() // iterable list of caches for this domain
caches.open("some-cache") // Returns a promise with that cache
caches.delete("some-cache")
```

### Deleting old caches

```js
caches.keys().then(cacheNames => {
  return Promise.all(
    cacheNames.map(cacheName => caches.delete(cacheName);
  )
})
```

### Working with a cache

Caching a response:

```js
caches.open("some-cache")
  .then(cache => {
    cache.put(request, response.clone()) // .clone allows the response to pass unaltered back to the client
  })
```

Finding a cached response:

```js
caches.open("some-cache")
  .then(cache => {
    cache.match(someRequest) // matching response
    cache.match(someUrl) // matching response
    cache.match(/someUrlPattern/) // matching response
  })
```

Precaching a response:

```js
caches.open("some-cache")
  .then(cache => {
    cache.add(url) // make a request and cache its response
    cache.addAll([url1, url2, url3]) // precache more than one
  })
```

## Client API

Available inside service workers, gets client objects so you can send them messages

```js
self.clients.matchAll()
self.clients.get(id)
self.clients.openWindow(url) // Open the app
self.clients.claim() // Make an activated service worker the controller for a page, prevents having to navigate or refresh
```

Sending messages:

```js
someClient.postMessage({
  anythingYouWant: "Really",
})
```

Receiving messages on the client:

```js
navigator.serviceWorker.addEventListener("message", event => {
   console.log(event.data) // { anythingYouWant: "Really" }
})
```
