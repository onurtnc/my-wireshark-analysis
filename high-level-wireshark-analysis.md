# Advanced Wireshark Network Traffic Analysis Report

## 1. Executive Summary

This report presents an advanced network traffic analysis conducted using
Wireshark on a captured PCAP file. The objective of the analysis was to identify
abnormal network behavior, focusing on DNS and HTTP traffic patterns that may
indicate automated or malicious activity such as command-and-control (C2)
communication.

The analysis revealed repetitive DNS queries with regular time intervals,
suggesting beaconing behavior commonly associated with malware callbacks.

## 2. Scope & Objectives

**Scope**
- Analysis of DNS and HTTP traffic
- Identification of anomalous communication patterns
- Correlation of network indicators with SOC detection logic

**Objectives**
- Detect automated network behavior
- Distinguish malicious traffic from normal user activity
- Provide actionable findings for SOC investigation and response

## 3. Environment & Tools

- **Tool Used:** Wireshark
- **Data Source:** PCAP network capture
- **Protocols Analyzed:** DNS, HTTP, TCP
- **Analysis Perspective:** Defensive / SOC-focused

## 4. Methodology

The analysis followed a structured SOC-style approach:

1. Initial traffic overview and protocol distribution
2. Focused filtering on DNS traffic
3. Frequency and timing analysis of DNS queries
4. Inspection of HTTP requests following DNS resolution
5. Identification of automation indicators

## 5. Traffic Analysis Findings

### 5.1 DNS Traffic Analysis

**Observations:**
- A single internal host generated a high volume of DNS queries
- Queries targeted the same external domain repeatedly
- Requests occurred at consistent time intervals
- Domain names appeared non-descriptive and low reputation

**Indicators Identified:**
- Repetitive queries (high frequency)
- Regular query timing (automation)
- Lack of diversity in queried domains

These indicators strongly suggest DNS beaconing behavior rather than normal
human-generated traffic.

### 5.2 HTTP Traffic Analysis

Following DNS resolution, HTTP traffic was observed originating from the same
host:

- Repeated HTTP GET requests
- Minimal variation in request headers
- Absence of typical browser behavior patterns

This behavior supports the hypothesis of command-and-control communication
using application-layer protocols.

## 6. Timing & Pattern Analysis

A time-based analysis of DNS queries revealed:

- Consistent intervals between requests
- No correlation with user interaction patterns
- Predictable request frequency

This regularity is a strong indicator of automated malware activity rather than
legitimate application behavior.

## 7. Threat Assessment

**Likely Threat Type:** Malware beaconing / C2 communication

**Potential Impact:**
- Remote command execution
- Data exfiltration
- Persistent unauthorized access

## 8. MITRE ATT&CK Mapping

| Tactic | Technique | Description |
|---|---|---|
| Command and Control | DNS (T1071.004) | DNS used for C2 communication |
| Command and Control | Application Layer Protocol | HTTP used for callback traffic |

## 9. Recommended SOC Actions

- Investigate the affected endpoint using EDR telemetry
- Identify the process responsible for DNS and HTTP traffic
- Isolate the host if malicious activity is confirmed
- Block the suspicious domain at DNS or firewall level
- Initiate incident response procedures

## 10. Conclusion

The analyzed network traffic exhibits multiple characteristics consistent with
automated command-and-control beaconing activity. The combination of repetitive
DNS queries, regular timing, and follow-up HTTP requests strongly indicates
malicious behavior.

This analysis demonstrates how Wireshark can be effectively used to support SOC
operations by providing packet-level evidence for detection, investigation, and
incident response workflows.

## 11. Analyst Notes

This report was created as part of a SOC-focused learning and portfolio project
to demonstrate advanced PCAP analysis, detection logic, and security-oriented
reporting.
