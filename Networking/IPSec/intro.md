## Why we need IPSec

- because IP was not born with the security mind
  - protocol is connectionless
  - protocol is unreliable-packets can be lost or relayed
  - protocol does not garentee order of the packets
  - ip packets can be sniffed
  - \\ can be spoofed

## IPSec Overview

- IPSec refers to a set of standards developed by security working group od the IETF
- before encapsulation, the packets are protected with:
  - MAC(integrity + authentication)
  - encryption(confidentiality)
  - numbreing (to avoid replay packets)
