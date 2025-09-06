# Metasploit Framework

## Overview

**Metasploit** is an open-source penetration testing framework, created by H.D. Moore in 2003 and is now maintained by Rapid7. It provides tools, libraries and modules to help security professionals identify and exploit vulnerabilities in systems.

Metasploit is mainly used for Developing and executing exploits, post-exploitation tasks (like privilege escalation, gathering credentials, etc.), payload generation and information gathering and scanning. It is included in Kali Linux and Parrot OS by default.

### ⚠️ Warning

Metasploit is a powerful offensive tool and must only be used in authorized environments (labs, CTFs, or systems you have permission to test). Unauthorized use is illegal.

## Key Concepts

Metasploit is composed of several key components:

### Modules

A module in Metasploit is a small part of the framework used to perform a task, such as exploiting or scanning a target. A module can be an _exploit_ module, _auxiliary_ module, or _post-exploitation_ module.

`Exploit modules` are used to exploit vulnerabilities in a way that allows the framework to execute arbitrary code. The executed arbitrary code is called a **Payload**.  
`Auxiliary modules` do not exploit a vulnerability, but can perform useful tasks such as scanning, fuzzing, sniffing, Denial of Service, etc.  
`Payload Modules` Payload modules are the code that runs on a target after a successful exploit. They allow you to do things like reverse shell, control the system remotely, or run custom commands on the target machine.  
`Post modules` are used after you’ve already accessed a target. They help you gather information, maintain access, or perform tasks like dumping passwords, collecting system info, or cleaning up traces.  
`Encoder modules` are used to modify payloads to make it more difficult to identify by security defenses, like antivirus or IDSs. They don’t change the payload behavior, they just change its form to make it harder to detect.
