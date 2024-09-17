## <span style="color: #2196F3;">UDP</span>

*User Datagram Protocol*

*It does not establish a dedicated end-to-end connection before transmitting data. Instead, it sends packets (or datagrams) directly to the receiver without verifying the readiness or state of the receiver.*

**Client**  -----  *request*   ----> **Server** 
**Client**  <---- *response* ---- **Server** 
**Client**  <---- *response* ---- **Server** 

>[!danger] Features
>- QUIK
>- Web RTC (stream)
>- http 3
## <span style="color: #2196F3;">TCP</span>

*Transmission Control Protocol*

*It is reliable, connection-oriented communication channel between two devices (hosts) on a network. It ensures that data is transmitted accurately and in the correct order, with error detection and correction mechanisms.*

*1. Verification*
**Client**  -----  *SYN*   ----> **Server** 
**Client**  <---- *SYN ACK* ---- **Server** 
**Client**  -----  *ACK*  -----> **Server** 

*2. Normal flow*
**Client**  -----  *request*  -----> **Server** 
**Client**  <---- *response* ---- **Server** 

>[!danger] Features
>- http 1.1
>- http 2
>- Server sent events
>- Web sockets

## <span style="color: #2196F3;">Polling</span>

*Request every x seconds*

```typescript
	setInterval(() => fetch(...), timeout)
```

*Pros*
1. Easy & cheap to implement
2. 99% of servers support

*Cons*
1. High CPU usage due to open TCP connection every request
2. Network & data inefficient
3. HTTP 1.1 requires request headers in every request
4. Latency degradation on mobile networks

*Usage:*
1. Desktop apps where some delays are acceptable

*Avoid:*
1. Mobile web applications

## <span style="color: #2196F3;">Server Sent Events</span>

*Enables a server to push updates to a client’s web browser in real-time, without the need for the client to repeatedly request updates through polling or long-polling*

*Pros*
1. Automatic reconnection handling
2. Battery efficient
3. Easy to scale in terms of infrastructure
4. Minimal network overhead, receive data without headers
5. Fast

*Cons*
1. You can not push data to the server
2. Only string data is supported, payload need to be parsed

*Usage:*
1. Desktop / mobile app with minimum latency
2. Alternative to web-sockets
3. Large text-data streaming

*Avoid:*
1. Simple desktop apps (long-polling is better in these cases)

## <span style="color: #2196F3;">Web-sockets</span>

*Bi-directional communication protocol that enables a persistent, low-latency, and efficient connection between a client (usually a web browser) and a server.*

*Pros*
1. Almost real-time communication
2. Unlimited number of connections

*Cons*
1. Infrastructure cost
2. Engineering cost
3. Reconnection is not implemented
4. Stateful
5. Computing resource ineffeciency (constant TCP connection, CPU drain, duplex antenna)

*Usage:*
1. Real-time communication environments.
2. Online gaming
3. Trading
4. Location tracking

## <span style="color: #2196F3;">REST vs GraphQL</span>

*REST*
1. Small applications
2. Public API
3. Limited budget & readonly requests
4. Not Isomorphic data types
5. Critical bundle size
6. Simple API model

*GraphQL*
1. Isomorphic data types (almost stable types)
2. Complex API model
