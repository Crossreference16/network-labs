# Day 04: Basic Device Security

[Back to all labs](../README.md)

| | |
|---|---|
| Area | Fundamentals and device basics |
| Packet Tracer file | [day-04-basic-device-security.pkt](day-04-basic-device-security.pkt) |
| Status | Completed |

![Router, switch and PCs used for IOS security configuration](day-04-basic-device-security.png)

## What I built

On router R1 and switch SW1, from the command line:

- Set hostnames with `hostname`.
- Set an enable password, then tested access from user EXEC mode.
- Encrypted all passwords with `service password-encryption`, and checked the running configuration before and after.
- Replaced it with a hashed `enable secret` and confirmed the secret takes priority over the enable password.
- Saved the running configuration to the startup configuration so it survives a reload.

## Skills shown

- Cisco IOS command line: user EXEC, privileged EXEC and global configuration modes.
- The difference between weak (type 7) password encryption and a hashed enable secret.
- Running configuration versus startup configuration.

## Why it matters

This is the first hardening applied to any new Cisco device. Forgetting to save the configuration is a classic cause of devices losing their settings after a power cut.
