## Wireshark & Network Traffic Analysis

This section includes hands-on network traffic analysis performed using
Wireshark and PCAP files, focusing on SOC and defensive security use cases.

### Analysis Scope
- DNS traffic inspection and anomaly detection
- HTTP request analysis and pattern identification
- Detection of repetitive and automated network behavior
- Identification of potential command-and-control (C2) communication
- Basic protocol-level investigation (DNS, HTTP, TCP)

### Techniques Used
- Filtering traffic using protocol and field-based filters
- Identifying abnormal query frequency and regular intervals
- Distinguishing human-generated traffic from automated behavior
- Correlating network indicators with endpoint and SIEM findings

### Example Use Cases
- DNS beaconing detection through PCAP analysis
- Investigation of suspicious outbound connections
- Supporting SIEM alerts with packet-level evidence
- Providing network context for incident response decisions

### Skills Demonstrated
- Practical PCAP analysis with Wireshark
- Network protocol understanding
- SOC-style investigation mindset
- Incident analysis and reporting

> Note: These analyses are performed in a defensive security context
to support detection, investigation, and incident response workflows.
