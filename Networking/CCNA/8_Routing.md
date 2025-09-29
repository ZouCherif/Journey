# Routing fundamentals

## What is Routing?

**_Routing_** is the process that routers use to determine the path that IP packets should take over a network to reach their destination.

- Routers store routes to all their known destinations in a `Routing Table`

There are two main routing methods (methods that routers use to learn routes):

- `Dynamic Routing` Routers use dynamic routing protocols (ie. OSPF) to share routing information with each other automatically and build
  their routing tables.

- `Static Routing` A network engineer/admin manually configures routes on the router.

A **_route_** tells the router: to send a packet to destination X, you should send the packet to **next-hop** Y (the next router in the path to the destination).

- If the destination is directly connected to the router, send the packet directly to the destination.
- If the destination is the router's own IP address, receive the packet for yourself (don't forward it).

`R1# show ip route` to view the routing table

![Alt Text](./assets/Routing/routing_table.png)

### Note

If a router receives a packet and it doesn't have a route that matches the packet's destination, it will `drop` the packet.

- This is different than switches, which **flood** frames if they don't have a MAC table entry for the destination.

If a router receives a packet and it has multiple routes that match the packet's destination, it will use the most specific matching route to
forward the packet.

- **_Most specific_** matching route = the matching route with the longest prefix length.
  → This is different than switches, which look for an **exact** match in the MAC address table to forward frames.

## Static Routing
