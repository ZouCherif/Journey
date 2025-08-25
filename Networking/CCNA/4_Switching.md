# Ethernet LAN Switching (Part 1)

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

![alt text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%201.png)

- SW1 receives the frame on interface F0/1

  - SW1 checks the **source** MAC AAAA.AA00.0001 and learns (MAC AAAA.AA00.0001 is connected to F0/1)
  - SW1 adds this info to its MAC table.

  ![alt text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%202.png)

  - This is called `Dynamically Learned Mac Address`

- SW1 then checks its MAC table for the **destination** MAC AAAA.AA00.0003

  - It does not know this MAC yet.
  - This is an `unknown unicast frame`.
  - SW1 **floods** the frame out all other interfaces (F0/2 and F0/3).

  ![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%203.png)

  - PC2 drops the frame

- SW2 receives the frame on interface F0/3

  - SW2 checks the **source** MAC AAAA.AA00.0001 and learns (MAC AAAA.AA00.0001 is on F0/3)
  - SW2 adds this info to its MAC table.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%204.png)

- SW2 checks for **destination** MAC AAAA.AA00.0003

  - Unknown, not in the table (`unknown unicast frame`)
  - SW2 **floods** the frame to F0/1 and F0/2.
  - PC4 drops the frame
  - PC3 sees its own MAC as the destination and accepts the frame.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%205.png)

### Step 2: PC3 sends a frame to PC1 (Reply)

![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%206.png)

- SW2 receives the frame on interface F0/1

  - SW2 learns that AAAA.AA00.0003 is on F0/1, updates its MAC table.
  - SW2 checks for AAAA.AA00.0001 in its MAC table – it knows it’s on F0/3
  - SW2 forwards the frame only to interface F0/3 (`known unicast`)

  ![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%207.png)

- SW1 receives the frame on interface F0/3

  - SW1 learns that AAAA.AA00.0003 is on F0/3, updates its MAC table.
  - SW1 checks for AAAA.AA00.0001 in its MAC table – it knows it’s on F0/1
  - SW1 forwards the frame only to interface F0/1 (known unicast)
  - PC1 receives the frame and processes it.

  ![Alt Text](./assets/switching/Mac%20adr%20Learning/Mac%20adr%20Learning%208.png)

# Ethernet LAN Switching (Part 2)

## ⚠️ Note

- The Preamble + SFD is usually not considered part of the Ethernet header
- Therefore the size of the Ethernet header + trailer is 18 bytes (6 + 6 + 2 + 4)
- The minimum size for an Ethernet frame (Header + Payload [Packet] + Trailer) is 64 bytes
- 64 bytes - 18 bytes (header + trailer size) = 46 bytes
- Therefore the minimum payload (packet) size is 46 bytes
- If the payload is less than 46 bytes, padding bytes are added
- ie. 34-byte packet + 12-byte padding = 46 bytes

## ARP (Address Resolution Protocol)

- ARP is used to discover the Layer 2 address (MAC address) of a known Layer 3 address (IP address)
- Consists of two messages: `ARP Request` and `ARP Reply`
- ARP Request is **broadcast** = sent to all hosts on the network
- ARP Reply is **unicast** = sent only to one host (the host that sent the request)

1. PC1 prepares the ARP req to be sent.

   ![Alt Text](./assets/switching/ARP/ARP%201.png)

2. SW1 receives the frame and add PC1 MAC adr to its table

   ![Alt Text](./assets/switching/ARP/ARP%202.png)

3. Since the destination MAC adr is **broadcast**, SW1 broadwast the frame to all his interfaces except G0/0, PC2 ignores the frame because its IP adr does not match the destination IP.

   ![Alt Text](./assets/switching/ARP/ARP%203.png)

4. SW1 adds the MAC adr of PC1 to its MAC table.
5. SW2 broadcast the frame on all interfaces except G0/2.
6. PC4 ignores the frame
7. PC3 IP match the destination IP adr on the frame, so sends an **ARP reply** (MAC src his own MAC adr, PC1 MAC adr as Dest adr, same for IP addrs).
8. SW2 adds PC3 MAC adr to its MAC table.
9. Since it is a unicast frame SW2 will only send the frame on the interface G0/2 to SW1 (Know Unicast Frame == Forward).
10. SW1 learns PC3 MAC adr.
11. PC1 finally receives the ARP reply, and use the PC3 MAC adr and add it to its **ARP table**.

![Alt Text](./assets/switching/ARP/ARP%204.png)

### ARP table

![Alt Text](./assets/switching/ARP/ARP%20table.png)

- Type static = default entry
- Type dynamic = learned via ARP

## Ping

- A network utility that is used to test reachability
- Measures round-trip time
- Uses two messages: `ICMP Echo Request` and `ICMP Echo Reply`
