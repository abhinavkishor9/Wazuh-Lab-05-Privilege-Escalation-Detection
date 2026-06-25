# Wazuh-Lab-05-Privilege-Escalation-Detection

## Overview

This lab demonstrates how Wazuh can detect and monitor privilege escalation activity on a Linux endpoint.

The objective is to generate sudo-related events, verify their presence in Linux authentication logs, and observe how Wazuh processes and displays these events in Threat Hunting.

---

## Lab Objectives

- Generate privilege escalation activity using sudo
- Monitor authentication logs on Linux
- Validate Wazuh log collection
- Investigate security events in Threat Hunting
- Correlate Linux logs with Wazuh alerts

---

## Lab Environment

| Component | Details |
|------------|----------|
| Wazuh Manager | Rocky Linux |
| Endpoint | Rocky Linux (Agent 001) |
| Wazuh Version | 4.14.x |
| Log Source | /var/log/secure |
| Event Type | Privilege Escalation |
| Detection Method | sudo authentication monitoring |

---

## Attack Simulation

A sudo command was executed from a standard user account.

```bash
sudo tail -f /var/log/secure
```

The system generated authentication events related to privilege escalation.

---

## Evidence Collection

### Verify sudo Activity

```bash
sudo tail -f /var/log/secure
```

Observed events:

```text
pam_unix(sudo:auth)
sudo session opened
authentication failures
```

---

### Threat Hunting Investigation

Navigate to:

```text
Threat Hunting → Events
```

Search for:

```text
sudo
```

or

```text
rule.groups:sudo
```

---

## Key Findings

- Wazuh successfully collected Linux authentication logs.
- sudo activity was recorded in `/var/log/secure`.
- Authentication events were visible in Threat Hunting.
- Privilege escalation attempts can be correlated using sudo-related events.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|------------|-------------|
| T1548.003 | Abuse Elevation Control Mechanism: sudo |

---

## Outcome

This lab validated Wazuh's ability to monitor and detect privilege escalation activity through Linux authentication logs and Threat Hunting analysis.

---

