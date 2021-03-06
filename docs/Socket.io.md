<!-- # Socket.io # -->

<p align="center">
  <h1 class="text-center">Socket.io</h1>
</p>

<p align="center">
  <a href="#">
    <img src="../assets/img/io-logo.png" max-width="50px" max-height="50px" alt="IO Logo" />
  </a>
</p>


`tips` `gists` `howto` `socket.io`

---

## Emit cheatsheet ##

```javascript
io.on('connect', onConnect);

function onConnect (socket) {

  // sending to the client
  socket.emit('hello', 'can you hear me?', 1, 2, 'abc');

  // sending to all clients except sender
  socket.broadcast.emit('broadcast', 'hello friends!');

  // sending to all clients in 'game' room except sender
  socket.to('game').emit('nice game', "let's play a game");

  // sending to all clients in 'game1' and/or in 'game2' room, except sender
  socket.to('game1').to('game2').emit('nice game', "let's play a game (too)");

  // sending to all clients in 'game' room, including sender
  io.in('game').emit('big-announcement', 'the game will start soon');

  // sending to all clients in namespace 'myNamespace', including sender
  io.of('myNamespace').emit('bigger-announcement', 'the tournament will start soon');

  // sending to individual socketid (private message)
  socket.to(<socketid>).emit('hey', 'I just met you');

  // sending with acknowledgement
  socket.emit('question', 'do you think so?', function (answer) {});

  // sending without compression
  socket.compress(false).emit('uncompressed', "that's rough");

  // sending a message that might be dropped if the client is not ready to receive messages
  socket.volatile.emit('maybe', 'do you really need it?');

  // sending to all clients on this node (when using multiple nodes)
  io.local.emit('hi', 'my lovely babies');

};
```

**Note**: The following events are reserved and should not be used as event names by your application:

* `error`
* `connect`
* `disconnect`
* `disconnecting`
* `newListener`
* `removeListener`
* `ping`
* `pong`

---

### Source Links ###

[Socket.io Official](https://socket.io/docs/emit-cheatsheet/#emit-cheatsheet)

---

### Related info ###

- [GitHub / Basic writing and formatting syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [BitBucket / Markdown Howto](https://bitbucket.org/tutorials/markdowndemo)
- [Docker / Creating an Automated Build](https://docs.docker.com/docker-hub/builds/)
- [Docker / Linking containers](https://docs.docker.com/engine/userguide/networking/default_network/dockerlinks.md)
- [Docker / Cross-host linking containers](https://docs.docker.com/engine/admin/ambassador_pattern_linking.md)

---

:scorpius:
