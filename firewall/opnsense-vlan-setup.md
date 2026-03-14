# OPNsense VLAN and Firewall Overview

This lab uses OPNsense as the main firewall and segmentation point.

## Design Goals

- isolate lab systems from normal devices
- create controlled paths between VLANs
- test security tooling in segmented environments
- simulate real-world lateral movement constraints

## Example VLAN Roles

- **VLAN 1** — super user / management
- **VLAN 2** — servers / infrastructure
- **VLAN 3** — pentest / attacker network
- **VLAN 4** - IoT Home Assistant

## Example Security Logic

- VLAN 3** can reach selected targets for testing
- VLAN 2** is protected and only exposes necessary services
- user networks are separated from attack tooling
- management exposure is minimized where possible

## Notes

Exact rules, credentials, and sensitive internal details are intentionally omitted from this public repository. 

# OPNsense Firewall and VLAN Segmentation

This lab uses OPNsense as the central firewall and network segmentation platform.

The firewall controls communication between multiple VLANs and simulates a small segmented enterprise-style network where traffic flows, access policies, and host exposure can be observed and analyzed.

The lab environment is used to practice:

- network segmentation using VLANs
- firewall rule design and access control
- controlled attack and reconnaissance scenarios
- monitoring and interpreting firewall traffic logs
- understanding network activity and host communication patterns
- identifying suspicious or unexpected traffic between network segments
- evaluating how segmentation affects attack surface and lateral movement

In addition to configuring firewall policies, the lab focuses on understanding how traffic appears in firewall logs and how security analysts can use this information to investigate activity, validate rules, and detect anomalies.

## Network Segmentation

The lab network is divided into several VLANs to simulate real-world network separation.

Example VLAN structure:

- **VLAN1xx – Super User Network**
  - main linux server supervisor
  - internet access

- **VLAN2xx – Active Domain Network**
  - Windows server
  - internal services
  - infrastructure components

- **VLAN3xx – Pentest Network**
  - Kali Linux attacker workstation
  - security testing tools

- **VLAN4xx - IoT Home Assystant**
  - DIY ESP32 MQTT cripted API comunication
  - Tilescale configuration 
  - limited internet acess

This segmentation allows realistic testing of lateral movement restrictions.

## Logical Network Diagram
```
Internet
│
OPNsense Firewall
│
──────────────────────────
│        │      │       | 
VLAN1xx VLAN2xx VLAN3xx VLAN4
Users  Servers Pentest  IoT
|        |      |        |
|        |      |        |---- Home assistant 
|        |      |
|        |      |---- kali linux 
|        |        
|        |---- Win server AD
│        |---- Win client
├── MAC 
├── LLM server


```
## Firewall Design Philosophy

The firewall follows a "default deny" approach.

Key principles:

- block unnecessary inter-VLAN communication
- restrict server exposure
- allow controlled testing from the pentest network
- minimize attack surface between segments


## Example Inter-VLAN Policy

Example rules used in the lab:
```
| Source VLAN | Destination | Allowed |
|-------------|-------------|--------|
| VLAN1xx | Internet | yes |
| VLAN1xx | VLAN2xx | limited |
| VLAN2xx | VLAN1xx | blocked |
| VLAN3xx | VLAN2xx | allowed for testing |
| VLAN4xx | Internet | yes |
```
These rules allow controlled testing scenarios while keeping systems segmented.

## Example Security Scenario

A common lab exercise is to simulate an attacker starting from the pentest VLAN.

Steps:
```
1. Identify active hosts in VLAN20
2. Enumerate exposed services
3. analyze potential attack paths
4. evaluate firewall impact on lateral movement
```
This helps understand how segmentation affects reconnaissance and attack surface.

## Example Log Analysis

Firewall logs are used in the lab to understand how traffic flows between network segments and to verify that security policies behave as intended.

The following example demonstrates how a security analyst might interpret a firewall event.

### Example Event
```
Source IP:      192.168.xxx.10
Source VLAN:    VLAN3xx (Pentest Network)

Destination IP: 192.168.xx.162
Destination VLAN: VLAN2xx (Server Network)

Protocol:       TCP
Destination Port: 445 (SMB)

Action:         Blocked
Firewall Rule:  Inter-VLAN restriction
```
```
### Interpretation

This log entry indicates that a host in the pentest network attempted to connect to an SMB service in the server network.

Because SMB access between these segments is restricted by firewall policy, the connection was blocked.

### Analyst Perspective

From a security monitoring perspective, this type of log entry can represent:

- reconnaissance activity
- service enumeration attempts
- lateral movement testing

Repeated blocked attempts from the same host may indicate scanning behavior.

### Lab Usage

In this lab environment, similar events are intentionally generated to:

- verify firewall rule behavior
- understand how reconnaissance traffic appears in logs
- practice interpreting network activity from firewall events
```
## Integration With AutoRecon AI

The lab uses a custom reconnaissance automation tool:

AutoRecon AI

The tool helps:
```
- scan segmented networks
- classify hosts
- generate analysis reports
- prioritize targets for investigation

Repository:
https://github.com/andreagovons/autorecon-ai
```

## Security Considerations

Sensitive information such as:

- exact IP addresses
- firewall rule exports
- credentials
- private infrastructure details

are intentionally omitted from this public documentation.
