## Websockets

* `npm install --save ws`
* Web sockets are bi-directional
* Not fully supported in browsers
* Need a web socket server
* long-lived XHR request
* `ws.send`, `ws.on`
* `new WebSocket`
* Use libraries: `socket.io`, `engine.io`, `sock.js`

## Socket.io

```js
io.on("connection", function(socket){
    socket.on("chat message", function(message){
        io.emit("chat message", message);
    });
});

socket.on("chat message", function(message){
});
```

## Primus

* Primus is an abstraction-abstraction

```js
primusServer = new Primus;
primusServer.on("connection", function(socket){
    socket.on("data" function(message){
    });
});
```
