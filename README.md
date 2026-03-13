# Cybersecurity Home Lab

Personal cybersecurity home lab built for hands-on learning, network segmentation, defensive testing, and offensive security practice.

This lab is designed to simulate a small segmented environment with:

- firewall-based network control
- VLAN separation
- Windows and Linux systems
- vulnerable lab targets
- local AI-assisted reconnaissance tooling

---

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

## Repository Structure

```text
cybersecurity-home-lab
├── diagrams
├── firewall
├── lab-machines
├── attack-scenarios
└── README.md
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

⸻

Related Project

This lab uses the following custom reconnaissance tool:
	•	AutoRecon AI￼

⸻

Security Notice

This repository documents a private lab environment for authorized learning and testing only.

Sensitive information, real credentials, exact internal configuration values, and private network details have been intentionally sanitized.
