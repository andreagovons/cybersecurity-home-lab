# Recon Workflow

This document describes a typical reconnaissance workflow used in the lab.

## Workflow

1. Identify active hosts in a subnet
2. Classify hosts by exposed services
3. Prioritize targets for further analysis
4. Perform single-host enumeration
5. Use AutoRecon AI for triage and reporting
6. Review remediation or next-step guidance

## Example Commands

```bash
python3 main.py 192.168.X.0/24
python3 main.py 192.168.X.100 dual
python3 main.py 192.168.X.100 offensive
