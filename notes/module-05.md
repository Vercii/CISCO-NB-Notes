# Module 5

## Communication Protocols

Protocols are a set of rules that devices follow in order to communicate across a network. These rules define:

- How messages are formatted
- How data is transmitted
- How devices identify each other
- How successful communication is confirmed

Protocols are important because they allow devices to communicate properly in both wired and wireless environments. Without shared protocols, devices on a network would not be able to understand each other.

### Aspects of Communication

- Message format
- Message size
- Timing
- Encoding
- Encapsulation
- Message pattern

---

### Encoding

Encoding is the process of converting data into signals that can be transmitted across a network.

Examples:
- Electrical signals through copper cables
- Light signals through fiber-optic cables
- Wireless radio signals through the air

### Encapsulation

Encapsulation is the process of adding protocol information to data as it moves through the network layers before transmission.

Each layer adds its own information to help devices properly deliver and process the data.


## Network Communication

Devices require addressing and network configuration information in order to communicate across networks.

Protocols help devices determine:
- Their IP address
- Which network they belong to
- The default gateway address
- The DNS server address

Different protocols work together to allow communication between devices.

## Network Protocols

- Ethernet: Standard used for wired LAN communication.
- IP (Internet Protocol): Handles addressing and routing between networks.
- TCP (Transmission Control Protocol): Ensures reliable and ordered delivery of data.
- HTTP (HyperText Transfer Protocol): Used for transferring web pages and web resources.

## TCP/IP Model
- Application: Represents data to the user and provides network services to applications.
- Transport: Supports communication between devices across different networks.
- Internet: Determines the best path for data to travel through the network.
- Network Access: Controls the hardware devices and media responsible for transmitting data.

## OSI Model
- Application: Contains protocols used for process-to-process communication.
- Presentation: Provides a common format for transferred data between devices.
- Session: Establishes, manages, and terminates communication sessions between applications.
- Transport: Defines services for segmenting, transferring, and reassembling data between end devices.
- Network: Provides logical addressing and routing between networks. IP addressing operates at this layer.
- Data Link: Defines methods for exchanging data frames across a shared medium.
- Physical: Represents the physical hardware, cables, signals, and media used for communication.

## Difference Between TCP/IP and OSI
The OSI model is a conceptual framework used to understand how network communication works, while the TCP/IP model is the practical protocol suite used on modern networks and the internet.

## Key Takeaways
- Protocols are rules that allow devices to communicate properly.
- Multiple protocols work together to transmit data across networks.
- IP handles addressing and routing.
- TCP ensures reliable data delivery.
- Encapsulation adds protocol information as data moves through layers.
- The TCP/IP and OSI models help explain how network communication functions.
