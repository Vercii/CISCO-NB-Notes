# Module 7 - The Access Layer

## Ethernet Frame
- Preamble: Get the receiving NIC card in sync with the bits that are coming down the cable.
- Start Frame Delimiter: Acts as a marker signaling the end of the preamble and the start of the Ethernet frame.
- Destination MAC Address: MAC Address of the destination on that network.
- Source MAC Address: MAC Address of the origin device.
- Length/Type: Indicates either the length or the type of the data.
- DATA: The actual encapsulated data, could be an IPv4, IPv6, or other protocols.
- Frame Check Sequence: Makes sure there were no errors along the way in transmission.

Ethernet doesn't care what kind of data is being sent, it only cares about sending the data.

## Encapsulation
Specific format rules are followed in order for data to be delivered and processed.

The process of placing one message format inside another message format is <b>Encapsulation</b>.

De-encapsulation is the reverse of this process.

Each computer message is encapsulated in a frame (the specific format), which acts like an envelope; it has the address of the destination and the source host.

The format and contents of a frame depends on the type of message being sent and the channel it is communicated through.

Incorrectly formatted messages will not be delivered.

### Encapsulation Analogy
An envelope has the address of the sender and receiver, each located at the proper place on the envelope. If the destination address and formatting are not correct, the letter is not delivered.

The process of placing one message format (the letter) inside another message format (the envelope) is called encapsulation. De-encapsulation occurs when the process is reversed by the recipient and the letter is removed from the envelope.

## Ethernet Switches
Ethernet switches make their forwarding decision based on destination MAC address.

Ethernet switches add entries to their MAC address table based on the source MAC address.
