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
```
## Example Scenario

A typical lab exercise may follow this workflow:

1. Scan the network to identify active hosts
2. Classify hosts based on exposed services
3. Identify potentially high-value targets
4. Perform focused enumeration on selected hosts
5. Generate analysis reports using AutoRecon AI
6. Review potential security improvements

This simulates how a security analyst might triage hosts during an internal assessment.
