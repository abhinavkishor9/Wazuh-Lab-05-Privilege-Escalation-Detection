# Investigation Notes

## Objective

Investigate privilege escalation activity generated through sudo command execution and validate Wazuh detection.

---

## Detection Source

Linux Authentication Logs

```text
/var/log/secure
```

---

## Activity Performed

User executed:

```bash
sudo tail -f /var/log/secure
```

This triggered sudo authentication events.

---

## Evidence

Observed log entries:

```text
pam_unix(sudo:auth)
session opened for user root
authentication failures
```

---

## Analysis

The events indicate:

1. User attempted privilege escalation.
2. PAM authentication process validated credentials.
3. Root session was created after successful authentication.
4. Events were written to `/var/log/secure`.
5. Wazuh collected and indexed the events.

---

## Threat Hunting Queries

Search:

```text
sudo
```

Alternative:

```text
rule.groups:sudo
```

---

## Findings

| Finding | Status |
|----------|---------|
| Authentication Logged | Yes |
| sudo Activity Detected | Yes |
| Events Collected by Wazuh | Yes |
| Threat Hunting Visibility | Yes |

---

## Conclusion

Privilege escalation activity was successfully generated, collected, and investigated using Wazuh Threat Hunting.
