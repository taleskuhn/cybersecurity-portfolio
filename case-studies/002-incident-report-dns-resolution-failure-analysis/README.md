# Case Study 002 — DNS Resolution Failure Analysis

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#case-study-002--dns-resolution-failure-analysis)

## Executive Summary

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#executive-summary)

This case study analyzes a website availability incident in which users were unable to access **[www.yummyrecipesforme.com](http://www.yummyrecipesforme.com)** and received a "destination port unreachable" error.

The incident was analyzed using **tcpdump** to capture and inspect network traffic. The packet capture showed that the browser sent DNS queries using **UDP to port 53**, but instead of receiving a DNS response, the client received **ICMP messages indicating that UDP port 53 was unreachable**.

The analysis identified the affected service and the immediate network-level issue responsible for the DNS resolution failure.

The available evidence did not establish the underlying root cause. As a follow-up, the incident report identifies the systems, logs, configurations, and administrative activity that should be investigated by the responsible teams to determine why the DNS service was unavailable.

---

## Incident

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#incident)

**Website:** [www.yummyrecipesforme.com](http://www.yummyrecipesforme.com)

**Incident Type:** Website Availability / DNS Resolution Failure

**Affected Service:** Domain Name System (DNS)

**Affected Port:** UDP 53

**Analysis Tool:** tcpdump

---

## Objectives

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#objectives)

* Analyze the network traffic associated with the incident
* Identify the affected network protocol and service
* Interpret the DNS request and ICMP error response
* Determine the immediate technical issue shown by the packet capture
* Document the impact of the DNS failure
* Identify appropriate next steps for determining the underlying root cause

---

## Technologies & Protocols

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#technologies--protocols)

* tcpdump
* Domain Name System (DNS)
* User Datagram Protocol (UDP)
* Internet Control Message Protocol (ICMP)
* Hypertext Transfer Protocol Secure (HTTPS)
* DNS A Records

---

## Skills Demonstrated

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#skills-demonstrated)

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

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#key-findings)

| **Finding**                      | **Result**                        |
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

## Network Traffic Analysis

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#network-traffic-analysis)

The tcpdump capture showed that the client attempted to resolve **[www.yummyrecipesforme.com](http://www.yummyrecipesforme.com)** by sending a DNS query to the DNS server at **203.0.113.2**.

The relevant traffic was:

```text
Client
192.51.100.15
      |
      | UDP / Port 53
      | DNS query
      v
DNS Server
203.0.113.2
      |
      | ICMP
      | "udp port 53 unreachable"
      v
Client
192.51.100.15
```

The DNS query requested an **A record**, which is used to obtain the IPv4 address associated with a domain name.

Instead of receiving a DNS response, the client received an ICMP error indicating that **UDP port 53 was unreachable**.

This prevented the domain name from being resolved and consequently prevented the browser from proceeding to the subsequent HTTPS connection.

---

## Impact

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#impact)

Because the DNS resolution process failed, clients could not obtain the IP address associated with **[www.yummyrecipesforme.com](http://www.yummyrecipesforme.com)**.

Without the destination IP address, the browser could not establish the HTTPS connection required to access the website.

The incident therefore resulted in a **website availability issue caused by DNS resolution failure**.

---

## Root Cause Assessment

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#root-cause-assessment)

The packet capture established that DNS requests were being sent to **UDP port 53** and that the client received an ICMP message indicating that the port was unreachable.

This identifies the immediate technical issue observed during the incident: **the DNS service was unavailable on UDP port 53 at the time of the capture**.

However, the packet capture does not establish why the service was unavailable.

No definitive root cause was assigned based solely on the available network evidence.

---

## Recommended Next Steps

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#recommended-next-steps)

As a follow-up to the network analysis, the incident report identifies several areas that should be investigated by the responsible teams to determine the underlying cause of the outage:

* Verify the DNS service status
* Review DNS and operating-system logs
* Inspect firewall rules and recent changes
* Validate DNS configuration
* Verify network connectivity between clients and the DNS server
* Review recent system and infrastructure changes
* Review authentication and administrative activity
* Investigate potential security causes if supporting evidence is identified

These steps are **recommendations for further investigation**, rather than investigations performed as part of this case study.

---

## Lessons Learned

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#lessons-learned)

One of the main lessons from this case was understanding the distinction between identifying a technical issue and determining its underlying cause.

The packet capture provided enough evidence to identify the affected service, protocol, port, and communication failure. However, it did not provide enough information to determine why the DNS service was unavailable.

The case also demonstrated the importance of recognizing the limits of available evidence and defining appropriate next steps when additional investigation is required.

---

## Repository Contents

[svg](https://github.com/taleskuhn/cybersecurity-portfolio/blob/main/case-studies/002-dns-resolution-failure-analysis/README.md#repository-contents)

| **File**                                            | **Description**                           |
| --------------------------------------------------- | ----------------------------------------- |
| assessment-002.pdf                                  | Original incident scenario and assessment |
| incident-report-dns-resolution-failure-analysis.pdf | Network analysis and incident report      |
| README.md                                           | Case study overview and key findings      |


