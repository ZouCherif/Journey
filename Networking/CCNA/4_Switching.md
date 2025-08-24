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
- `Destination` and `Source`
  - Mac address
  - 6 bytes (48 bits)
- `Type` or `Length`
  - 2 bytes (16 bits)
  - A value of 1500 or less in this field indicates the LENGTH of the Packet (in bytes)
  - A value of 1536 or greater in this field indicates the TYPE of the encapsulated packet (usually IPv4 or IPv6), and the length is determined via other methods
- `FCS`
  - 4 bytes (36 bits)
  - Detects corrupted data by running a 'CRC' algorithm over
    the received data

## How Switches Handle Frames in a LAN

### Step 1: PC1 sends a frame to PC3

![alt text](./assets/switching/Mac%20adr%20Learning%201.png)

- SW1 receives the frame on interface F0/1

  - SW1 checks the **source** MAC AAAA.AA00.0001 and learns (MAC AAAA.AA00.0001 is connected to F0/1)
  - SW1 adds this info to its MAC table.

  ![alt text](./assets/switching/Mac%20adr%20Learning%202.png)

  - This is called `Dynamically Learned Mac Address`

- SW1 then checks its MAC table for the **destination** MAC AAAA.AA00.0003

  - It does not know this MAC yet.
  - This is an `unknown unicast frame`.
  - SW1 **floods** the frame out all other interfaces (F0/2 and F0/3).

  ![Alt Text](./assets/switching/Mac%20adr%20Learning%203.png)

  - PC2 drops the frame

- SW2 receives the frame on interface F0/3

  - SW2 checks the **source** MAC AAAA.AA00.0001 and learns (MAC AAAA.AA00.0001 is on F0/3)
  - SW2 adds this info to its MAC table.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning%204.png)

- SW2 checks for **destination** MAC AAAA.AA00.0003

  - Unknown, not in the table (`unknown unicast frame`)
  - SW2 **floods** the frame to F0/1 and F0/2.
  - PC4 drops the frame
  - PC3 sees its own MAC as the destination and accepts the frame.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning%205.png)

### Step 2: PC3 sends a frame to PC1 (Reply)

![Alt Text](./assets/switching/Mac%20adr%20Learning%206.png)

- SW2 receives the frame on interface F0/1

  - SW2 learns that AAAA.AA00.0003 is on F0/1, updates its MAC table.
  - SW2 checks for AAAA.AA00.0001 in its MAC table – it knows it’s on F0/3
  - SW2 forwards the frame only to interface F0/3 (`known unicast`)

  ![Alt Text](./assets/switching/Mac%20adr%20Learning%207.png)

- SW1 receives the frame on interface F0/3

  - SW1 learns that AAAA.AA00.0003 is on F0/3, updates its MAC table.
  - SW1 checks for AAAA.AA00.0001 in its MAC table – it knows it’s on F0/1
  - SW1 forwards the frame only to interface F0/1 (known unicast)
  - PC1 receives the frame and processes it.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning%208.png)
