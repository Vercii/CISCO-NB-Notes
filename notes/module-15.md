# Module 15 - TCP and UDP

## Transport Layer Protocols

### TCP vs UDP (Transport Layer Protocols)
The Transport Layer is responsible for taking large amounts of data (such as webpages, emails, videos, or voice calls) and breaking them into smaller pieces called segments before sending them across a network.

Each segment contains:

A source port number (where the data came from)
A destination port number (where the data is going)

These port numbers help devices keep track of conversations between applications.

---
### UDP (User Datagram Protocol)
UDP is mainly used for:
- Streaming
- Voice calls (VoIP)
- Online gaming
- Real-time communication

UDP is considered fast and lightweight because it has very little overhead.

<b>Characteristics of UDP</b>
- No acknowledgements
- No sequence numbers
- No retransmission of lost packets
- -Packets may arrive out of order
- Some packets may be lost

In real-time communication, losing a few packets usually does not matter. For example, during a voice call or livestream, missing a tiny amount of data is less disruptive than waiting for lost packets to be resent.

<b>UDP prioritizes:</b>
- Speed
- Low delay
- Continuous communication

Instead of checking whether every packet arrived correctly, UDP simply sends the data as quickly as possible.

---
### TCP (Transmission Control Protocol)
TCP is used when reliability is extremely important.

Examples:
- Web browsing
- File transfers
- Banking transactions
- Emails

TCP includes mechanisms to ensure data arrives correctly and in order.

Characteristics of TCP
- Uses acknowledgements (ACKs)
- Uses sequence numbers
- Retransmits lost packets
- Reorders packets correctly
- Provides reliable communication

Each TCP segment contains:
- Source port
- Destination port
- Sequence number

The sequence number allows the receiving device to:
1. Check if packets are missing
Reassemble packets in the correct order
2. After receiving packets successfully, the destination sends an acknowledgement back to the sender requesting the next sequence of packets.

---

### Main Differences
| TCP                      | UDP                             |
| ------------------------ | ------------------------------- |
| Reliable                 | Faster but less reliable        |
| Uses acknowledgements    | No acknowledgements             |
| Uses sequence numbers    | No sequence numbers             |
| Retransmits lost packets | Does not retransmit packets     |
| Packets arrive in order  | Packets may arrive out of order |
| More overhead            | Less overhead                   |
