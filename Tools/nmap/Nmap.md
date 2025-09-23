# Nmap

## Basic Nmap

- `namp -h` or `man nmap` To show the nmap help.
- `nmap -V` To display the version of the nmap tool.

### Verbose Output

- `-v` The small v option in nmap is used to enable verbose outputproviding more detailed information during the scanning process.
  - `nmap -v <target>` This cmd will perform a scan on the specified target with verbose output enabled
  - If we want more detailed information about the scanning process we use `-vv`

### Scan A Single Target

- `nmap <target>` Executing nmap without any options initiates a fundamentalscan on the target/
  - Nmap **_the wizard of network probing_** will systematically scans the top 1000 most common TCP/IP ports
  - Ports have 6 states:
    - `Open` A service is **actively** waiting connections on this port.
    - `Closed` No service is running on this port.
    - `Filtred`Nmap cannot determine if the port is open because packet filters (like firewalls) are blocking probes.
    - `Unfiltred`The port is reachable, but Nmap cannot determine whether it is open or closed because the probe packets reach the host, but the responses do not give enough information to distinguish the port state.
    - `Open|filtred` Nmap cannot tell if a port is open or filtered because it receives no response; the port might be open (some scan types like UDP or FIN don’t elicit replies) or filtered (a firewall could silently drop packets), so Nmap can’t decide which.
    - `Closed|filtred` Rare state indicating the port appears closed or filtered, usually seen when scan results are ambiguous.

### Scan Multiple Target

- `nmap <target1> <target2> ...`
  - example `nmap 192.168.52.1 192.168.52.2 192.168.52.3`

### Scan An Entire Subnet

- `nmap <target network/CIDR>`
  - exmaple `nmap 192.168.52.0/24`

### Scan A Range Of IP Addresses

- `nmap {range of IP adr}`
  - example `nmap 192.168.52.1-13`

### Scan A List Of Targets

- `nmap -iL <filename.txt>`

### Exclude Targets from Scan

- **_<filename.txt>_** is a file that contains a list of IP addresses.

- `nmap <Targets> --exclude <target>`
  - example `nmap 192.168.52.0/24 --exclude 192.168.52.44`
- `nmap <Targets> --excludefile <filename.txt>`
- We can exclude also a range if IP addresses.

### Selecting A Network Interface

- Nmap usually detects automatically our Active interface, however, there is situations where we need to choose a different interface to address networking issues.
- `nmap -e <interface> <target>`
  - example `nmap -e lo 192.168.52.3`

### Scan An IPv6 Target

- `nmap -6 <IPv6 target>`
  - example `nmap -6 fe80::9d77:c9db:7a26:cb33`

### Scan Random Targets

- `nmap -iR <number of targets>`
  - example `nmap -iR 4`

### Display Port State Reason Codes

- `nmap --reason <target>`
- This displays a new information explaining why each port is in its current state.

### Only Display Open Ports

- `nmap --open <target>`

### Trace Packets

- `nmap --packet-trace <target>`
- Gives a detailed log of packets journey sent and received.

## Port Scanning

### Perform A Fast Scan

- `nmap -F <target>`
  - By default nmap scans the top 1000 ports but with the `-F` option nmap trims that list down to 100 in order to optimize scanning experience.

### Scan Specific Ports

- `nmap -p <Ports> <target>`
  - Example `nmap 80 192.168.52.1`
  - Or `nmap 80,139,50-100 192.168.52.1`
- Using Port name also `nmap <Port names(service name)> <target>`
  - Example `nmap http,msrpc,apex-mesh 192.168.52.1 `
- `nmap -p "*" <target>` Scans all 65k ports
- `nmap -sU -sT -p U:[port num for UDP] T:[port num for tcp] <Target>`
  - Example `nmap -sU -sT -p U:53,T:25 192.168.52.1`
  - this command is used to check both UDP and TCP services on specific ports of a target host. It helps you find out which of those services (like DNS on UDP 53 or SMTP on TCP 25) are open or responding.
    This command runs a combined scan: -sU sends UDP probes and -sT performs a TCP connect scan.
  - It targets UDP port 53 and TCP port 25 on the host 192.168.52.1, checking their states simultaneously.

### Scan top Ports

- `nmap --top-ports <number of ports> <target>`

## foundational Scanning
