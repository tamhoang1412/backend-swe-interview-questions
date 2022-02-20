# Topic: NETWORKING

## How TCP open a connection? What does it need to open a connection?

TCP needs to open a connection to determine if the server is available to respond and know there is a way from it to the server before transferring data. To open a connection, firstly server must be bound and listen to a port, it is passive open. Then a process called 3-way handshake happens:

- Client sent SYN packet to the server with sequence num A
- Server sends SYN-ACK packet to the client with rand sequence num B and ack num A' > A (eg A+1)
- Client sends ACK packet to the server, with ack num B' > B (eg B+1) and the sequence number is A' ( the ack num it received in step 2)

## Why there are 3 way handshakes but not 2 way?

2-way will establish a half-duplex connection only. It means this is a one-direction connection the client is the only sender and the server is the only receiver. 3-way will establish a full-duplex connection, both client and server are sender and receiver.

## What is syn, ack mean?

Syn means synchronizaton. SYN packet is sent when the sender tries to connect to the receiver.
Ack means acknowledgment. ACK packet is sent by the receiver to the sender to help the sender know that the SYN packet that it sent before reached the destination successfully.

## Why they have to send 2 "random" sequence numbers? The purpose of this sequence number?

Sequence numbers are used to keep track of the order of data. The initial sequence number needs to be chosen randomly so the data in one flow will not be conflicted with other data bytes in other flows which are transmitted in the same TCP connection. Because sequence number is 32-bit integer so the maximum value of a sequence number is 2^32 - 1. So if the amount of data is greater than 4GB, at least one sequence number value will be reused.

## What if the 3rd handshake fail? How the server can detect it and what does it do in this case?

Retry and timeout.

## How TCP handles the connection?

To be defined

## What happens if some bits are wrong due to connection errors? How to detect them and fix them?

If some bits are wrong, the checksum of this packet will not match. In this case, the receiver will discard this packet.

## How the timeout is handled? what if the timeout is expired?

To be defined

## What will happen if some "packet" is missing on the way?

When a packet is missing, network congestion is assumed to happen. TCP has its own way to deal with network congestion. It is called TCP Congestion control. It starts when slow-start phrase, in which the transmit rate (congestion window) grows exponentially, doubling each round trip time. When a packet is lost, congestion avoidance begins. The transmit rate is cut into half, then increase linearly, usually by 1 each RTT.

## How to detect the appropriate number of packets to send (speed of sending packet)?

Like above.

## How TCP close the connection?

It does a 4-way handshake. Firstly peer A send a FIN packet to peer B. Then peer B send an ACK packet for the FIN it receives. After that peer B send it own FIN packet to peer A. Then peer A send ACK packet to the peer B. Connection is over.
Step 2 and 3 can be merged by one, so it will be 3-way handshake instead.

## What if the internet is dropped in the middle of the connection? Or in case one peer is crash?

To be defined

## How long you can keep a TCP connection alive?

To be defined
