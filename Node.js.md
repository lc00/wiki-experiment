## Why server-side JS?

* Node is fast
* Non-blocking IO
* Uses Google's V8 engine
* One language to rule them all
* Good standard library
* npm

## Why not server-side JS?

* You have to think in async
* Has maturity issues
* Callback hell
* JavaScript has quirks

## Single-threaded

* Single-threaded has advantages over threaded
* Node has an event loop handling all requests, which it delegates to POSIX async threads
* Restaurant metaphor -> one waiter who just takes orders and delivers food vs. 10 waiters who do everything
* Don’t use node for CPU intensive tasks (video processing).

## Node Core

* V8 (the engine)
* Libev: The event loop
* LibEio: Async I/O
* LibUv: Abstraction on libEio, libev, etc
* A standard library

## Global Node objects:

* `process` - Running process
* `require` - Function to require package
* `console`
    * `console` object is similar, but different
    * `console.error` prints to `stderr`
    * `console.trace()` to show stack trace
* `global`
* `http` - Has to be imported
* No `document`, `window`, `DOM`

## Modules:

* `var express = require("express");`
* Can be a JS file or a JSON file
* If the thing isn't a file, it looks inside for an `index.js` file.
* Don't have side effects in your modules.
* 4 ways to require:
    * `require("fs")` - Core module or from `node_modules` folder
    * `require("./something")` - For arbitrary files
    * `require("../config.json")` - For arbitrary files
    * `require` returns whatever is hanging off of `module.exports` in that file
* You can immediately invoke modules
* You can export anything (function, object, whatever)

## Module Patterns

* Simple Object API
* Hide private variables
* Returning an object literal
* Revealing Module

```js
var MyModule = (function(){
    function hiddenMethod() {
        return "hey";
    }

    return {
        publicMethod: privateMethod
    };
})();

MyModule.privateMethod(); // undefined
MyModule.publicMethod(); // "hey"
```

* Modules are cached- it's the same object!! Returning just an object is a singleton.
* Object constructor (returns an object with a prototype chain)

## npm

* Is the tool, `npm`
    * Has publishing tools (can include tasks)
* Is the site, [[https://www.npm.org]]
* Is the registry (which is not the actual packages, just pointers to them)
* Can be public or private
* Project Metadata is in `package.json`
    * Create one with `npm init`
* Setting up `npm` defaults:
    * `npm set init.author.name "Kyle Coberly"`
    * `npm set init.author.email "kyle.coberly@gmail.com"`
    * `npm set init.author.url "www.kylecoberly.com"`
* Installing locally
    * `npm install package_name` to try
    * `npm install --save package_name` to install production dependency
    * `npm install --save-dev package_name` to install development dependency
* Installing globally
    * `npm install -g package_name`
* `npm ls`, `npm -g` to list installed packages

## Semantic versioning

* `~1`, `~1.1` goes for highest minor or patch version
* `npm shrinkwrap` - Snapshots every version
* `npm search` - Looks for packages, kind of sucks, use Google
* `npm update` - Updates registry
* `npm rm --save` - Deletes a package

## Process

* The process object has the environment variables, can kill processes, access the shell, etc.

```js
    process.env; // {
        SHELL: "/bin/zsh",
        USER: "kylecoberly",
        HOME: "/home/kylecoberly",
        PORT: 3000,
        NODE_ENV: "development"
    }
```

* Get arguments via `process.argv`
    * Takes the command line as space-delimited tokens
    * Doesn't parse anything
    * Includes `node`
    * Returns array
* To kill node:
    * `process.exit(0)` for success
    * `process.exit(127)` for failure
* To respond to signals:

```js
    process.on("eventName", function(error){
        console.log("error", error);
    });
```

* POSIX codes from OS: `SIGINT`, `ENONT`, `EADDRINUSE`


## `http`/`https` module

* Write and handle HTTP/HTTPS requests
* Use package to auto load on change = nodemon, eg- nodemon server.js

```js
var http = require("http");

var server = http.createServer(function handleRequests(request, response){
    response.writeHead(200, {
        "Content-Type": "text/plain",
        "X-My-Thing": "The internet"
    });
    response.end("Hello world!");
});

server.listen(3000, "127.0.0.1", function(){
    console.log("It's up!");
})
```

## `child_process` Module

* Allows you to create sub-processes.
* `spawn` is an instance of the `ChildProcess` class. Close the input stream to allow the spawned process to continue running.

```js
var execute = require("child_process").exec;
var ps = execute("ps aux", function (err, stdout, stderr){
    // Do something
};
```

```js
    var spawn = require("child_process").spawn;
    var someEvent = spawn("someEvent", ["something"]);
    someEvent.stdout.on("data", function(data){
        tee.stdin.write(data);
    };
```

## Standard streams

* `STDIN`, `STDOUT`, `STDERR`
* Event emitters that have standard events. They are pluggable.
    * `.data()`, `.write()`, `.end()`, `.pipe()`
* Whether it's readable/writeable can depend on perspective
* `STDOUT` and `STDERR` are both blocking. Special streams!
* `stream.tty` will tell you if the user is using it directly, rather than a program

### `STDIN`

* To listen in on data from stdin, use the `data` and `end` events
* `data` is input fed to the program. This may trigger multiple times.
* `end` says the you’re done reading. `STDIN` is paused by default

### `STDOUT`

* `write()` to write to `STDOUT`

### `STDERR`

* For logging, usually

## Buffers

* Buffers are chunks of binary data in memory
* For larger data sets or if you don’t how much of something you'll have:
    * `buffer = new Buffer(26); buffer.toString("utf8", 0, 5);`

## Filesystem IO

* File handling can/should be non-blocking. That's what makes it "web scalable".
* Check that it exists before you start reading
* Don't respond with errors for files that users don't have permissions to access

### fs

* File system is core module
* Race conditions = When something is no longer true after you check it
* Don’t use the sync version of the fs methods! Won’t scale!

```js
fs.readFile("file/path", {options}, function(error, contents){
    if (error){
        // throw...
    }
    console.log(contents);
});
```
### fs Methods

* `fs.writeFile();`
* `fs.appendFile();`
* `fs.exists();`
* `fs.stats.isFile()`
* `fs.stats.isDirectory()`
* `fs.stats.isSocket()`
* `fs.stats.size`
* `fs.stats.mtime`
* `fs.link(“src”, “dest”, “file” callback);`
* `fs.unlink(); // delete`
* `fs.mkdir();`
* `fs.readdir();`
* `fs.rmdir();`

## Sync vs. Async

* `process.nextTick();`
* All async functions require callbacks.
* Callback hell - fight with event emitters, named functions, library, or promises
    * `callback` and `next` mean the same thing
* Event emitter is a string with a corresponding callback
    * Events are an imported module
    * Can also inherit from util.
    * `emitter.listeners(eventName)`
    * `emitter.on(eventName, listener)`
    * `emitter.once(eventName, listener)`
    * `emitter.removeListener(eventName, listener);`

## Connecting to Databases

* Install driver module
* Create a connection
* Connect it
* Query it

### Connecting to Mongo

* Require MongoClient
* Declare URL
* Connect with mongo
* MongoLab = free cloud instances

## Scaling

### Vertical scaling (within server)

* Node is fast, but single-threaded. This means every request uses the same process.
* Non-blocking code ensures that something else is handling async requests, usually via callbacks.
* unclustered node app only using one core.
* Clustered node app can use every core.
* `cluster` module
* Call cluster.fork() once per CPU core
* Strongloop Process Manager does this for you

### Horizontal scaling (across servers)

* Scalability is gained by putting a load balancer in front of multiple servers.

## Framework Patterns

* KISS Servers: small core, small modules (Node core)
* Convention: follow the leader, steep learning curve (Express, restify, Total.js)
* Configuration: open path, manual effort for advanced (Hapi, Kraken)
* ORM & Isomorphic: model-driven, shared code, steep learning (Loopback, Sails, Meteor)

## Server-side Events

* One way, part of HTML5
* `EventSource`
* Add event listeners in your code
* Two newlines is “end of message”
* Don’t close the connection
* Accept-Type: Event-Stream

## Debugging

* `DEBUG` library
* built-in debugger
* Node Inspector = Chome dev tools for node. Use Chrome debugger, etc.
