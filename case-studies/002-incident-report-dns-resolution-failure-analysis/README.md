# Case Study 002 — DNS Resolution Failure Analysis

## Executive Summary

This case study analyzes a website availability incident in which users were unable to access **[www.yummyrecipesforme.com]** and received a "destination port unreachable" error.

The incident was analyzed using **tcpdump** to capture and inspect network traffic. The packet capture showed that the browser sent DNS queries using **UDP to port 53**, but instead of receiving a DNS response, the client received **ICMP messages indicating that UDP port 53 was unreachable**.

The analysis identified the affected service and the immediate technical issue responsible for the DNS resolution failure. The available evidence did not establish the underlying root cause.

The incident report therefore also identifies areas that should be investigated further by the responsible teams to determine why the DNS service was unavailable.

---

## Incident

**Website:** [www.yummyrecipesforme.com]

**Incident Type:** Website Availability / DNS Resolution Failure

**Affected Service:** Domain Name System (DNS)

**Affected Port:** UDP 53

**Analysis Tool:** tcpdump

---

## Objectives

* Analyze the network traffic associated with the incident
* Identify the affected network protocol and service
* Interpret the DNS request and ICMP error response
* Determine the immediate technical issue shown by the packet capture
* Document the impact of the DNS failure
* Identify appropriate areas for further investigation

---

## Technologies & Protocols

* tcpdump
* Domain Name System (DNS)
* User Datagram Protocol (UDP)
* Internet Control Message Protocol (ICMP)
* Hypertext Transfer Protocol Secure (HTTPS)
* DNS A Records

---

## Skills Demonstrated

* Network Traffic Analysis
* Packet Capture Analysis
* Protocol Identification
* DNS Analysis
* Incident Documentation
* Technical Reporting
* Evidence-Based Analysis
* Investigation Planning

---

## Key Findings

| Finding                          | Result                            |
| -------------------------------- | --------------------------------- |
| DNS query transmitted by client  | Confirmed                         |
| DNS protocol involved            | Confirmed                         |
| UDP used for DNS request         | Confirmed                         |
| Destination port                 | UDP 53                            |
| DNS response received            | No                                |
| ICMP error received              | Confirmed                         |
| ICMP error                       | UDP port 53 unreachable           |
| DNS service available on port 53 | No                                |
| HTTPS connection possible        | No, because DNS resolution failed |
| Root cause of DNS unavailability | Not determined                    |

---

## Recommendations

The complete analysis and follow-up recommendations are available in the attached incident report.

Highlights include:

* Verify the DNS service status
* Review DNS and operating-system logs
* Inspect firewall configuration and recent changes
* Validate DNS configuration
* Verify network connectivity
* Review recent system and infrastructure changes
* Review authentication and administrative activity
* Investigate potential security causes if supporting evidence is identified

These recommendations represent **areas for further investigation** and were not performed as part of the network traffic analysis.

---

## Lessons Learned

One of the main lessons from this analysis was understanding the distinction between identifying an immediate technical issue and determining its underlying root cause.

The packet capture provided enough evidence to identify the affected service, protocol, port, and communication failure, but it did not provide enough information to determine why the DNS service was unavailable.

The analysis also demonstrated the importance of recognizing the limits of available evidence and identifying appropriate next steps when additional investigation is required.

---

## Repository Contents

| File                                                | Description                               |
| --------------------------------------------------- | ----------------------------------------- |
| assessment-002.pdf                                  | Original incident scenario and assessment |
| incident-report-dns-resolution-failure-analysis.pdf | Network analysis and incident report      |
| README.md                                           | Case study overview and key findings      |
