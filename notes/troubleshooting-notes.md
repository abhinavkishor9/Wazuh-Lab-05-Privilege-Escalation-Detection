# Troubleshooting Notes

## Issue 1 – No Events Appearing in Threat Hunting

### Symptoms

```text
No results match your search criteria
```

### Resolution

Increase the time range:

```text
Last 24 Hours
```

or

```text
Last 7 Days
```

Refresh the page after generating activity.

---

## Issue 2 – Searching "sudo" Returns No Results

### Cause

Events may not have been indexed yet.

### Resolution

Generate additional sudo activity:

```bash
sudo ls
sudo whoami
sudo tail -f /var/log/secure
```

Wait 1–2 minutes and refresh Threat Hunting.

---

## Issue 3 – Agent Filter Hides Results

### Symptoms

Only a specific endpoint is displayed.

### Resolution

Remove:

```text
agent.id:001
```

from active filters.

---

## Issue 4 – Verify Wazuh Agent Connectivity

Check agent status:

```bash
sudo /var/ossec/bin/manage_agents -l
```

Expected:

```text
Status: Active
```

---

## Issue 5 – Confirm Log Generation

Verify Linux logs directly:

```bash
sudo tail -f /var/log/secure
```

Expected events:

```text
pam_unix(sudo:auth)
session opened
authentication failure
```

---

## Issue 6 – Wazuh Not Receiving Logs

Restart agent:

```bash
sudo systemctl restart wazuh-agent
```

Verify:

```bash
sudo systemctl status wazuh-agent
```

---

## Validation Checklist

- [x] Agent connected
- [x] sudo activity generated
- [x] Authentication logs recorded
- [x] Events visible in Threat Hunting
- [x] Wazuh detection validated
