# OSI And TCP/IP Models

Networking models categorize and provide a structure for networking protocols and standards.

- `Protocols` A set of rules defining how network devices and software should work

## OSI (Open Systems Interconnection)

### 7. Application Layer

- Interacts with software applications
- HTTP and HTTPS are Layer 7 protocols
- Identifying communication partners
- Synchronizing communication

### 6. Presentation Layer

- translate between application and network formats
- encryption/decryption

### 5. Session Layer

- Controls dialogues (Sessions) between communicating hosts

### ⚠️ Note

- Network engineers typically don't work with the top three layers of the OSI model, but developers do, as they use them to connect their applications over networks.
- Data prepared at the top 3 layers, the 4 bottom layer do the work to send data over network.

### 4. Transport Layer

- Segments and reassembles data
- Breaks large pieces of data into smaller segments which can be more easily sent over the network
- Provide host-to-host communication
- Data in this layer is called **`Segment`**

### 3. Network Layer

- Provides connectivity between end hosts on different networks
- Provides logical addressing (IP addresses)
- path selection between source and destination
- Data in this layer is called **`Packet`**

### 2. Data Link Layer

- Provides node-to-node connectivity and data transfer (for example, PC to switch, switch to router, router to router)
- Defines how data is formatted for transmission over a physical medium
- Detects and (possibly) corrects Physical Layer errors
- Data in this layer is called **`Frame`**

### 1. Physical Layer

- Defines physical characteristics of the medium used to transfer data (voltage, distance, cables)
- Bits converted into electrical/radio signals

### Encapsulation/De-encapsulation

![Alt Text](./assets/OSI%20&%20TCP-IP/OSI.png)
