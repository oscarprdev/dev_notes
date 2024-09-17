## <span style="color: #2196F3;">Client side</span>

```typescript
	// Connecting to server
	const ws = new WebSocket("ws://localhost:8080", ["json"])
	
	ws.addEventListener("open", () => {
		console.log("connected")
	}) 
```

## <span style="color: #2196F3;">Server side</span>

```typescript
	const server = http.createServer((req, res) => {
		return handler(req, res, {
			public: "./frontend" // Client project folder
		})
	})
	
	sever.on("upgrade", (req, socket) => {
		if (req.headers["upgrade"] !== 'websocket') {
			socket.end("HTTP/1.1 400 Bad Request")
			return
		}
		const acceptKey = req.headers['sec-websocket-key']
		const acceptValue = generateAcceptValue(acceptKey)
		const headers = [
			"HTTP/1.1 101 Web Socket Protocol Handshake",
			"Upgrade: WebSocket",
			"Connection: Upgrade",
			`Sec-WebSocket-Accept: ${acceptValue}`,
			"Sec-WebSocket-Protocol: json",
			"\r\n"
		]
		socket.write(headers.join("\r\n"))
		socket.on("data", (buffer) => {
			// ... // 
			socket.end()
		})
		socket.on("end", () => { ... })
	})

/* SOCKETS KEY GENERATOR*/
	export function generateAcceptValue(acceptKey) {
		return (
			crypto
			.createHash("sha1")
			.update(acceptKey + "258EAFA5-E914-47DA-95CA-C5AB0DC85B11"),
			"binary")
			.digest("base64")
		);
	}
```


## <span style="color: #2196F3;">Socket.io</span>

```typescript
// html
<script src="https://cdn.socket.io/4.1.2/socket.io.min.js" crossorigin="anonymous"/>

// client.js
const socket = io("http://localhost:8080")

socket.on("connect", () => {
	console.log("connected")
})

socket.on("disconnect", () => {
	console.log("disconnected")
})

socket.on("some-action", (data) => {
	// manage payload
})

// server.js
const io = new Server(server, {})
io.on("connection", (socket) => {
	console.log("connected", socket.id)
	
	socket.emit("some-action", { payload })
	
	socket.on("disconnect", () => {
		console.log("disconnected", socket.id)
	})
})
```