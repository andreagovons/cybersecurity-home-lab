# Cybersecurity Home Lab

## Lab Goals

This home lab was built to practice real-world cybersecurity tasks such as:

- network segmentation with VLANs
- firewall rule design and traffic control
- reconnaissance and host triage
- Windows and Linux service exposure analysis
- testing automation tools such as AutoRecon AI

The lab environment simulates a small segmented infrastructure where security testing can be performed safely.
Personal cybersecurity home lab built for hands-on learning, network segmentation, defensive testing, and offensive security practice.

This lab is designed to simulate a small segmented environment with:

- firewall-based network control
- VLAN separation
- Windows and Linux systems
- vulnerable lab targets
- local AI-assisted reconnaissance tooling

---
## Lab Architecture

The lab network is segmented using OPNsense firewall and multiple VLANs to simulate a small enterprise-style environment.
```
Internet
   │
OPNsense Firewall / Router
   │
────────────────────────────────────────────────────
│            │             │             │          │
│            │             │             │          │
VLAN1        VLAN200       VLAN210       VLAN300    VLAN400
Management   Server Zone   AI Analysis   Pentest    IoT
                             Zone        Lab-KALI
│            │             │             │          │
│            │             │             │          ├─ Home Assistant
│            │             │             │          └─ IoT Devices
│            │             │
│            │             └─ LLM Server (Ollama)
│            │
│            ├─ Windows Server (Active Directory)
│            ├─ Windows Client Machines
│            └─ Metasploitable (pivot / escalation target)
│
│                                        └─ Kali Linux (attacker machine)
│
└─ Management Access
   ├─ OPNsense Admin
   ├─ Switch Management
   └─ Lab Administration
```
### Network Segmentation Strategy
```
The lab network is segmented using multiple VLANs to simulate a small enterprise environment.

VLAN1 – Management
Used for administrative access to infrastructure components such as the firewall and network switch.

VLAN200 – Server Zone
Contains Windows Server (Active Directory), Windows clients, and a vulnerable Metasploitable host used for pivoting and privilege escalation scenarios.

VLAN210 – AI Analysis Zone
Dedicated network segment hosting the LLM server running Ollama. This system provides AI-assisted reconnaissance analysis and is isolated from vulnerable targets.

VLAN300 – Pentest Lab
Contains the Kali Linux attacker machine used to perform reconnaissance and security testing within the lab.

VLAN400 – IoT Network
Isolated network hosting Home Assistant and IoT devices to simulate a consumer automation environment.

Inter-VLAN traffic is controlled by OPNsense firewall rules following a default-deny strategy.
Only specific traffic required for lab testing is allowed between segments.

```
## Goals

- practice network reconnaissance safely
- understand firewall rules and segmentation
- simulate attack paths in a controlled lab
- test detection, hardening, and remediation ideas
- support CompTIA PenTest+ and cybersecurity analyst learning

---

## Lab Components

- OPNsense firewall
- VLAN-based segmentation
- Kali Linux attacker machine
- Windows server / Windows workstation systems
- Metasploitable target
- Dedicated LLM server with Ollama
- AutoRecon AI for local-first recon and triage

---
## Skills Demonstrated

This lab demonstrates hands-on experience with:

- network segmentation and VLAN design
- firewall configuration and traffic control
- host discovery and reconnaissance
- service enumeration and triage
- lab-based penetration testing workflows
- AI-assisted analysis for security triage

---
## Repository Structure

```text
cybersecurity-home-lab
├── diagrams
├── firewall
├── lab-machines
├── attack-scenarios
└── README.md
```
```
Included Documentation
	•	firewall/opnsense-vlan-setup.md
Overview of VLAN design and firewall logic
	•	lab-machines/kali.md
Purpose of the attacker / recon machine
	•	lab-machines/windows-server.md
Windows services and lab role
	•	lab-machines/metasploitable.md
Vulnerable target overview
	•	lab-machines/llm-server.md
Dedicated Ollama-based AI analysis node
	•	attack-scenarios/recon-workflow.md
Example reconnaissance workflow using AutoRecon AI
```
⸻

Related Project
```
This lab uses the following custom reconnaissance tool:
	•	AutoRecon AI￼
```
⸻

Security Notice

This repository documents a private lab environment for authorized learning and testing only.

Sensitive information, real credentials, exact internal configuration values, and private network details have been intentionally sanitized.
