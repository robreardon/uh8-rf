# uh8-rf
This repository contains test code to control a UH8-RF wiring centre or RF-Switch remotely using rfcat.

It was developed using a HackRF One, Universal Radio Hacker (URH) and a large amount of trial and error.

## Protocols

### UH8-RF

Packet Structure
| Sync | Sync | Header | uh8Addr | Encoded Bits (nibble) | uh8Zone (nibble) | statMode | Fixed | Chksum | Chksum |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2D | D4 | C9 | 16 | 32 | 7 | 02 | 64 | 12 | 4D |

Encoded Bits
| 3 | 2 | 1 | 0 |
| -- | -- | -- | -- |
| Failsafe | Hotwater | Uhf or Radiator | Heating |

### RF-Receiver

Packet Structure
| Sync | Sync | Header | Header | Header | recvAddr+1 | Static | Static | recvAddr+2 | Heating/HW | On/Off | recvAddr | Fixed | Fixed | MsgNo | Fixed | Chksum | Chksum |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CC | 35 | 28 | 0A | 69 | 74 | 0B | 4E | 64 | 09 | 00 | 01 | 64 | 02 | 0D | 0B |
