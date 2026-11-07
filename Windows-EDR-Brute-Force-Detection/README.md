# Windows EDR-Style Monitoring & Brute-Force Detection Using Splunk

This project demonstrates Windows endpoint monitoring and brute-force detection using Splunk Enterprise SIEM. \
Windows Security Event Logs and Performance Monitor data are ingested into Splunk to monitor endpoint activity and identify suspicious authentication behavior. \
The primary detection focuses on repeated failed logon attempts using Windows Security Event ID 4625.

## Objectives

- Monitor Windows Security Event Logs.
- Analyze Windows Performance Monitor data.
- Monitor CPU Load and Network Interface activity.
- Detect repeated failed logon attempts.
- Implement time-based detection logic.
- Configure scheduled alerts.
- Enable email notifications for detection results.

## Detection Use Case: Brute-Force Attack

Windows Security Event ID `4625` represents a failed logon attempt.
Repeated failed logons within a short period may indicate:
- Password guessing.
- Brute-force attacks.
- Suspicious authentication behavior.
- Unauthorized access attempts.

### Detection Logic

1. Monitor Event ID 4625.
2. Group events into three-minute windows.
3. Count failed logons by account.
4. Identify accounts with more than three failed attempts within a time bucket.

## Alert Configuration

| Parameter | Configuration |
|---|---|
| Alert Name | EDR - Brute Force1 |
| Trigger Condition | Number of Results > 0 |
| Schedule | Weekly, Thursday, 7:00 |
| Action | Send Email |

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Brute Force | T1110 | Adversaries attempt to gain access by guessing passwords or other authentication credentials. |

## SPL Queries

Refer to [queries.txt](./queries.txt).

## LinkedIn Reference

[Windows EDR Lab — Splunk Brute-Force Detection](https://www.linkedin.com/feed/update/urn:li:activity:7425164389286211585/)
