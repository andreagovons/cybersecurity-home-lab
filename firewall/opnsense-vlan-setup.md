# OPNsense VLAN and Firewall Overview

This lab uses OPNsense as the main firewall and segmentation point.

## Design Goals

- isolate lab systems from normal devices
- create controlled paths between VLANs
- test security tooling in segmented environments
- simulate real-world lateral movement constraints

## Example VLAN Roles

- **VLAN 10** — user / normal devices
- **VLAN 20** — servers / infrastructure
- **VLAN 30** — pentest / attacker network

## Example Security Logic

- VLAN 30 can reach selected targets for testing
- VLAN 20 is protected and only exposes necessary services
- user networks are separated from attack tooling
- management exposure is minimized where possible

## Notes

Exact rules, credentials, and sensitive internal details are intentionally omitted from this public repository. 
