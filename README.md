WebSocketServer
===============
A WebSocket server implementation for Node.js, various features to still implement such as support for wss:// and preformance analytics centre.

Installation
============
Install using npm - https://npmjs.org/package/websocketserver

<pre>npm install websocketserver</pre>

Basic Usage
===========
In a project require the websocketserver module and create an instance of it:

<pre>var WebSocketServer = require("websocketserver");
var server = new WebSocketServer("all", 9000);</pre>

This will create a WebSocket server that runs on 9000 (default 8080) and uses a sendMethod that sends recieved connections to all server connections. Four sendMethods can be used:
 
  1) "all" - will send received messages to all users
  
  2) "others" - will send messages to all users apart from the sender
  
  3) "echo" - will echo the message back to the sender
  
  4) "none" - will not automatically send any messages (useful for when more control is needed over message sending, use API to send messages)
  
Events
======
The server emits events on a new connection, message and a closed connection:

  1) "connection" event - use to built a list of connections
  
  <pre>var connectionList = [];
server.on("connection", function(id) {
    connectionList.push(id);
});</pre>

  2) "message" event - get hold of the message
  <pre>server.on("message", function(data, id) {
  var mes = server.unmaskMessage(data);
  var str = server.convertToString(mes.message);
  console.log(str);
});</pre>

  3) "connectionclosed" - log a connection has left (can also use id to remove from connectionList)
  <pre>server.on("closedconnection", function(id) {
  console.log("Connection " + id + " has left the server");
});</pre>
  
Functions
==========

Need finishing
  
      
