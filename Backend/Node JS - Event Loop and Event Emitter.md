#### Event loop
It performs non-blocking I/O operations 

The phases of Event Loop 
=> Each have a FIFO queue of callbacks to execute

- timers - setTimeout/setIntervals
- pending callbacks
- idle, prepare
- poll - incoming connections, data etc
- check
- close callbacks

####  Event Driven Architecture
Basically, event happens and just react to it
##### Observer pattern

**Event Emitter**  --(Emits event)--> **Event Listener** --(Calls Event Handler)->**Event Handler**

```
const server = http.createServer() //Instance of Even Emitter Class

server.listen(8000, '127.0.0.1', () => {
	console.log("listening to the port")
})

// below "server" is emitter and "on" is event listener
server.on("requests", (req, res) => {
	//event handler which is a callback function
	res.end("Hello from server!")
})
```

