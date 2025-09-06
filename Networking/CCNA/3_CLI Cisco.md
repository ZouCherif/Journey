# CLI

- To configure a switch, we use the console ports (Rj-45, USB mini-B), with a **Rollover cable** (pin 1 to 8, 2-7, 3-6, 4-5...).
- After connecting our computer to the device (switch), we use a terminal emulator **Putty**.

## User Exec Mode

- `Router>` "Router" default hostname of the device, ">" means we are in the User Exec mode.
- User exec mode is very limited, we can loos at some things but we can't make any changes.

## Privileged Exec Mode

- `Router> enable` command allows us to enter Privileged EXEC mode.
- `Router#` means we are in the Privileged Exec mode.
- In this mode we have the complete access to view the device configuration, but we can not change make changes yet.
- We can change the time on the device, restart, save the config files.

### ⚠️ Note

We use the `?` cmd to view the available cmds

## Global Configuration Mode

- To enter the Global Config mode we execute
  - `Router# configure terminal`
  - `Router(config)#`

## Enable Password

- `Router(config)# enable password CCNA` "CCNA" is the password

## Running/Startup Config

- There is two seperate configuration files kept on the device

  - `Running config` the current active configuration file on the device. as we enter the cmds in the cli, we edit the active configuration

  - `Statup config` the config file that will be loaded upon restart of the device

- We use the cmd `show` to view the config files
  - `show running-config` and `show startup-config`

### Saving The Configuration

- There is three ways to save the configuration
  - `Router# write`
  - `Router# write memory`
  - `Router# copy running-config startup-config`

## Service Password Encryption

- `Router(config)# service password-encryption`
  - encryption type 7 (not very secure)
- Now if we check the running config cmd we will notice that the password is encrypted

## Other method to enable pwd encryption

- `Router(config)# enable secret CISCO`
- Encryption type 5 (MD5 encryption)

### ⚠️ Note

- If both the enable secret and enable password are configured, the **enable password will be ignored, only the enable secret willbe valid**
- `Router(config)# do sh run` Or do show running-config, the **do** cmd allow us to execute privileged cmds in other conf levels

## Canceling Cmds

- To cancel a cmd we use `no` cmd
  - `Router(config)# no service password-encryption`

### ⚠️ Note

- Here service password-encryption will not be used in future cmds, but current pwd will still encrypted and it does not affect enable secret

## Changing Hostname

- `Router(config)# hostname R1`
  - `R1(config)#`

## ARP Table

- `PC1# show arp`

## MAC Address Table

- `SW1# show mac address-table`
- To clear the MAC table use the cmd: `SW1# clear mac Address-table dynamic`
- To delete only one MAC adr: `SW1# clear mac address-table dynamic address <mac-addresss>`
- To delete all MAC addresses for one interface: `SW1# clear mac address-table interface <interface-id(ex: Gi0/0)>`

## IP Adresses Of A Router Interfaces

- `R1# show ip interface brief`

![Alt Text](./assets/CLI/ip%20interfaces%20brief.png)

- **administratively down**: Interface has been disabled with the **`shutdown`** command (This is the default Status of Cisco router interfaces)
- The **Status** column is the Layer 1 status (is the interface shutdown, is the cable attached ...etc)
- The **Protocol** column refers to the Layer 2 status (is Ethernet function properly)

### Configuring IP Addresses

- `R1# conf t`
  - `R1(config)# interface gigabitethernet 0/0` or `in g0/0`
  - `R1(config-if)# ip address 10.255.255.254 255.0.0.0`
  - `R1(config-if)# no shutdown` to enable the interface

## Some `Show` Cmds

- `R1# show interfaces g0/0` it shows info about the interface
- `R1# show interfaces description`
  - `R1(config-if)# description <ex: ## to SW1 ##>` to set a description

## Switch interfaces (6_Switch interafaces.md)
