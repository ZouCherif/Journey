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
