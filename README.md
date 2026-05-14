# Secure STM32 Zigbee Communication System - Operation CLEARWAY

## Overview

Operation CLEARWAY is a dual-node embedded communication system built using STM32 microcontrollers and XBee/Zigbee wireless modules. The project demonstrates secure wireless packet transmission, acknowledgement handling, replay protection and EEPROM-based storage.

The system was developed as an embedded systems project using C and STM32 HAL.

## System Architecture

The project uses two STM32 nodes:

### Node A - Secure Threat Sender

Node A builds compact threat-report packets, encrypts the payload, sends the data over XBee/Zigbee and waits for acknowledgement responses from Node B.

### Node B - Secure Receiver and Audit Logger

Node B receives encrypted packets, validates and decrypts them, checks for replayed sequence numbers, stores verified threat data in external EEPROM and sends an acknowledgement response back to Node A.

## Key Features

- Dual-node STM32 communication system
- XBee/Zigbee API Mode 2 wireless communication
- UART-based serial communication
- I2C EEPROM data storage using 24LC64 memory
- XTEA-based encrypted packet payloads
- Packet validation and keyed check byte
- Replay protection using sequence tracking
- ACK response system with status codes
- EEPROM threat-record storage
- Circular audit logging
- Modular embedded C drivers for transport, security and memory

## Technologies Used

- STM32 Nucleo-F411RE
- Embedded C
- STM32 HAL
- UART
- I2C
- GPIO
- XBee/Zigbee
- XCTU
- 24LC64 EEPROM
- XTEA encryption

## Packet Flow

1. Node A creates a threat report.
2. The payload is encrypted and packed into a secure frame.
3. The packet is sent over XBee/Zigbee.
4. Node B receives and validates the packet.
5. Node B checks for replayed sequence numbers.
6. Valid packets are stored in EEPROM.
7. Node B sends an ACK response back to Node A.

## Project Structure

```text
firmware/
├── clearway-node-a-sender/
└── clearway-node-b-receiver/

docs/
├── system-overview.md
├── packet-format.md
└── wiring-diagram.md
