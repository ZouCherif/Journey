# Switch Interfaces

## Show Interfaces

- `SW1# sh ip int br`

  ![Alt text](./assets/Switch%20interfaces/sh%20ip%20int%20br.png)

  ![Alt Text](./assets/Switch%20interfaces/interface%20Status.png)

  - Ip-Address in **unassigned** because this is Layer 2 switch ports, they don't need an IP adr.

- `SW1# show interfaces status`

  ![Alt text](./assets/Switch%20interfaces/show%20int%20status.png)

## Configuring A Switch Interface Speed and Duplex

![Alt Text](./assets/Switch%20interfaces/confi%20speed.png)

## Configuring many interfaces at the same time

- `SW1(config)# interface range f0/5 - 12`  
  or `SW1(config)# int range f0/5 - 6, f0/9 - 12`

![Alt Text](./assets/Switch%20interfaces/int%20range.png)

## Half and Full Duplex

- `Hald Duplex` The device **can not** send and receive data at the same time, if it is receiving a Frame, it must wait before sending
- `Full Duplex` The device **can** send and receive at the same time

## Speed/Duplex Autonegotiation

## Interface Errors

![Alt Text](./assets/Switch%20interfaces/int%20errors.png)

- `Runts` Frames that are smaller than the minimum frame size (64 bytes)
- `Giants` Frames that are larger than the maximum frame size (1518 bytes)
- `CRC` Frames that failed the CRC check (in the Ethernet FCS trailer)
- `Frame` Frames that have an incorrect format (due to an error)
- `Input errors` Total of various counters, such as the above four
- `Output errors` Frames the switch tried to send, but failed due to an error
