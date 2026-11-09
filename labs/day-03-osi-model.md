# OSI Model

[Back to all labs](../README.md)

| | |
|---|---|
| Area | Core networking and Cisco IOS |
| Packet Tracer file | [day-03-osi-model.pkt](day-03-osi-model.pkt) |
| Status | Completed |
| Key topics | OSI layers, simulation mode, DHCP |

![Server, two switches and two routers across two subnets](day-03-osi-model.png)

## The scenario

| Network | Devices |
|---|---|
| 192.168.1.0/24 | SRV1 (.100), PC1, switches SW1 and SW2, and R1's G0/0 (.1) |
| 10.0.0.0/24 | The link between R1 (.1) and R2 (.2) |

The tasks were:

1. Use simulation mode to analyse the traffic moving through the network, and work out which OSI layers it uses.
2. Release and renew PC1's IP address to generate Layer 7 traffic, then analyse that traffic too.

## What I did

- **Simulation mode.** Packet Tracer can pause the network and step through traffic one event at a time. Opening any packet shows its contents layer by layer in the OSI model view: the Ethernet frame (Layer 2), the IP packet (Layer 3), the TCP or UDP segment (Layer 4) and the application data (Layer 7).
- **Release and renew.** I released PC1's IP address and asked for a new one, which made PC1 run DHCP from scratch, and I followed the exchange in simulation mode.

## The DHCP exchange (DORA)

| Step | Message | What it shows at each layer |
|---|---|---|
| 1 | **Discover** (PC1 to everyone) | PC1 has no address yet, so it sends from 0.0.0.0 to the broadcast address 255.255.255.255, and to the broadcast MAC address FFFF.FFFF.FFFF at Layer 2 |
| 2 | **Offer** (server to PC1) | The DHCP server offers an address |
| 3 | **Request** (PC1) | PC1 asks for the offered address |
| 4 | **Acknowledge** (server to PC1) | The server confirms it, and PC1 configures its address |

DHCP is an application-layer protocol (Layer 7) carried over UDP (Layer 4), using port 68 on the client and port 67 on the server. Seeing the same exchange from Layer 2 up to Layer 7 is the point of the lab: every application message depends on all the layers beneath it.

## Skills shown

- **The OSI model in practice:** reading real packets layer by layer, not just reciting the seven layers.
- **DHCP:** the Discover, Offer, Request, Acknowledge sequence, and why the first messages are broadcasts.
- **Packet Tracer simulation mode:** stepping through events and opening individual packets to inspect them.

## Why it matters

"No IP address" and "can't reach the server" tickets are solved by finding which layer is failing. A PC on a 169.254.x.x address means the DHCP exchange never completed, and knowing that the Discover is a broadcast tells you where to look next. Working through the layers in order is how you troubleshoot logically rather than guess.
