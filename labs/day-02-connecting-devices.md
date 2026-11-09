# Connecting Devices

[Back to all labs](../README.md)

| | |
|---|---|
| Area | Core networking and Cisco IOS |
| Packet Tracer file | [day-02-connecting-devices.pkt](day-02-connecting-devices.pkt) |
| Status | Completed |
| Key topics | Straight-through vs crossover copper, fibre, cable distance limits, Auto MDI-X |

![Routers, switches and end devices connected with copper and fibre](day-02-connecting-devices.png)

## The task

Cable 4 routers, 8 switches, 3 PCs and a server according to the labels, choosing the right cable for each link. The lab assumes Auto MDI-X is turned off, so the switches can't correct a wrong copper cable for me. Every choice had to be right first time.

## The rules I applied

| Situation | Cable | Why |
|---|---|---|
| Unlike devices (router to switch, switch to PC or server) | Copper **straight-through** | One end transmits on the pins the other end receives on |
| Like devices (switch to switch, router to router) | Copper **crossover** | Both ends transmit on the same pins, so the pairs have to be swapped |
| Longer than 100 m | **Fibre** | 100 m is the maximum length for UTP copper Ethernet |
| Fibre over a few hundred metres | **Multimode** | Cheaper, and fine for short runs inside a site |
| Fibre over kilometres | **Single-mode** | Carries the signal much further |

## Every link and the cable I used

| Link | Distance | Cable |
|---|---|---|
| R1 – R2 | 50 m | Copper crossover (router to router) |
| R1 – R3 | 3 km | Fibre, single-mode (too far for copper or multimode) |
| R3 – R4 | 250 m | Fibre, multimode (too far for copper, short enough for multimode) |
| R2 – SW1, R2 – SW2, R4 – SW5, R4 – SW6 | | Copper straight-through (router to switch) |
| SW1 – SW2, SW1 – SW3, SW2 – SW4, SW5 – SW6, SW5 – SW7, SW6 – SW8 | | Copper crossover (switch to switch) |
| SW3 – PC1, SW4 – PC2, SW7 – PC3, SW8 – SRV1 | | Copper straight-through (switch to end device) |

In the diagram, a solid black line is straight-through, a dashed line is crossover, and a coloured line is fibre. Packet Tracer doesn't model single-mode and multimode separately, so the fibre choices in the table are the ones I'd make on a real site.

Links into the routers show red because router interfaces stay shut down until they're configured. That's expected at this stage: the cabling is correct, and the configuration comes in later labs.

## Skills shown

- **Physical layer knowledge:** picking straight-through, crossover or fibre for each link without relying on the equipment to fix mistakes.
- **Distance limits:** the 100 m limit for copper, and choosing multimode or single-mode fibre by distance.
- **Working from a spec:** cabling a 16-device network exactly as labelled.

## Why it matters

The wrong cable is still one of the most common causes of a "link down" or flapping-link fault, especially on older kit without Auto MDI-X. This is the knowledge you need for patching, comms room work and data centre cabling, and for spotting a physical fault before anyone starts troubleshooting the configuration.
