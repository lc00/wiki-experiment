## Setup

Install with `npm i -S @feathersjs/feathers`. Setup:

```js
const feathers = require("@feathers/feathers");
const app = feathers();
```

## Services

A service looks like this:

```js
class Messages {
    constructor(){
    }
    async find(parameters){
    }
    async get(id, parameters){
    }
    async create(data, parameters){
    }
    async patch(id, data, parameters){
    }
    async remove(id, parameters){
    }
}

app.use("messages", new Messages());
```

* You can access a registered service method with `app.service("messages").get()`, etc.
* Each time a service method is called, its emits an event, eg. `app.service("messages").on("created", message => {})`
* You can trigger a custom event with `service.emit("custom-event", data)`


## Hooks

* Hooks are for functionality that is shared across services
* They are middleware functions that can be registered before, after, or on the errors of a service method
* Used for things like validation, auth, logging, populating relations, and sending notifations
* A hook without a path (`app.hooks()`) is application-wide, good for logging and error-handling
* A hook gets passed a context object, and is expected to return it. It has:
    * `app` - The app instance
    * `service` - The current service
    * `path` - The current path for this service
    * `method` - The service's method
    * `type` - The hook type
    * `params.query` - The query string
    * `params.provider` - rest, socketio, etc.
    * `id`
    * `data`
    * `error` - Available in `error` hooks
    * `result` - Returned valued in `after` hooks

```js
function setTimestamp(name){
    return async (context) => {
        context.data[name] = new Date();
        return context;
    }
}

app.service("messages").hooks({
    before: {
        create: setTimestamp("createdAt");
    },
    after: {
        find: [control(), the(), order()]
    }
});
```

## Errors

```js
const {BadRequest} = require("@feathersjs/errors");

async function validate(context){
    const {data} = context;

    if (!data.text){
        throw new BadRequest("Needs text");
    }

    // Sanitizing
    context.data = {
        text: data.text.toString();
    };

    return context;
}

app.service("message").hooks({
    before: {
        post: valildate,
        patch: validate,
        update: validate
    }
});
```

## Transports

* HTTP REST via Express
* Socket.io
* Primus

### REST

* Uses a specialized version of Express
* Services are registered just like routes

```js
const feathers = require("@feathersjs/feathers");
const express = require("@feathersjs/express");

const app = express(feathers());

app.use(express.json();
app.use(express.urlencoded({extended: true});
app.configure(express.rest());

app.use("messages", new Messages());

const port = process.env.PORT || 3000;
app.use(express.errorHandler()); // Has to be last
const server = app.listen(port);
server.on("listening", () => {
    console.log(`Listening on localhost:${port}`);
});
```

### Socket.io

* Install with `npm i -S @feathersjs/socketio`

```js
// Server
const feathers = require("@feathersjs/feathers");
const socketio = require("@feathersjs/socketio");

const app = feathers(); // Can be combined with Express
app.configure(socketio());

app.on("connection", connection => {
    app.channel("chatroom").join(connection);
    app.publish(() => app.channel("chatroom"));
});

app.listen(3000);

// Client
const socket = io("http://localhost:3000");

socket.on("messages created", message => {
    console.log("Someone created a message", message);
});
socket.emit("create", "messages", (error, messageList({
    if (error) throw error
    console.log("Messages:", messageList);
}));

```

## Feathers Knex

```js
const knex = require("knex");
const service = require("feathers-knex");

const db = knex({
    client: "pg",
    connection: `postgres:///appname`
});

app.use("/messages", service({
    Model: db, // Connection instance
    name: "message" // Name of table,
    id: "id", // Name of primary key,
    events: [] // List of custom events,
    pagination: {
        default: 10,
        maxSize: 100
    }
}));

// Equivalent to GET localhost:3000/messages?text[$like]=Hello%
app.service("messages").find({
    query: {
        text: {
            $like: "Hello%"
        }
    }
});
```

### Transactions

```js
const {transaction} = require("feathers-knex").hooks;

module.exports = {
    before: {
        all: [transaction.start()],
    },
    after: {
        all: [transaction.end()],
    }
    error: {
        all: [transaction.rollback()],
    }
};
```

### Customizing a find

```js
app.service("messages").hooks({
    before: {
        find(context){
            const query = this.createQuery(context.params);
            query.orderBy("name", "desc"); // Or whatever
            context.params.knex = query;
            return context;
        }
    }
});
```

## Feathers Client

```js
const app = feathers();

// Sockets
const socket = io("http://localhost:3000");
app.configure(feathers.socketio(socket));

// Or REST
const rest = feathers.rest("http://localhost:3000");
app.configure(rest.fetch(window.fetch));

app.service("messages").on("created", message => {
    console.log("Someone created a message", message);
});

async function createAndList(){
    await app.service("messages").create({
        text: "Hello from a client!"
    });

    const messages = await app.service("messages").find();

    console.log("messages", messages);
}

createAndList();
```

## CLI

* Setup with `npm i -S @feathersjs/cli -g`

### Configure functions

* Functions that take the Feathers `app` object, do something like register a service on it, and then return it. Called with `app.configure()`.
* Set the function as the export for the module
* Naming convention is `name.type.js`

### Hook functions

* Utility functions for hooks
* Exported out directly
* Located in `/hooks/name.js`
