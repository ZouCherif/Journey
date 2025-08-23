# Ethernet LAN Switching

## Ethernet Frame

**Data** is first prepared by the top three layers of the OSI model. Once the data is ready, the transport layer (Layer 4) adds a header to it, creating what’s called a **segment**. This segment is then passed to the network layer (Layer 3), where another header is added, turning it into a **packet**. Finally, at the data link layer (Layer 2), both a _header_ and a _trailer_ are added, forming a `frame`.

![Alt Text](./assets/OSI%20&%20TCP-IP/OSI.png)

Now let’s take a look at the different parts that make up a network **frame**.

![Alt Text](./assets/switching/Ethernet%20Frame.png)

- `Preamble`
  - 7 Bytes Long (56 bits)
  - Alternating 1s and 0s (10101010 \* 7)
  - Allows devices to synchronize their receiver clocks
  - When a device sends data over a network, it uses the **preamble** to say: “Hey, get ready — I’m about to send data!”
- `SFD`
  - 1 byte (8 bits)
  - 10101011 (like the preamble but the last bit is 1)
  - Marks the end of the preamble, and the beginning of the rest of the frame
- `Destination`
- `Source`
- `Type`
