# SNORT-

SNORT-NIDS-NIPS-PROJECT

### Network Intrusion Detection & Prevention System (NIDS/NIPS) Lab with Snort

## Table of Contents
1. [Project Overview](#project-overview)
2. [IDS vs. IPS Core Concepts](#ids-vs-ips-core-concepts)
3. [Snort Operation Modes](#snort-operation-modes)
4. [Snort Log & PCAP Investigation](#snort-log--pcap-investigation)
5. [Custom Snort Rules Creation](#custom-snort-rules-creation)
6. [Tools & Technologies](#tools--technologies)
7. [Conclusion](#conclusion)

---

1. Project Overview
<a id="project-overview"></a>

This project documents a hands-on lab environment utilizing **Snort**—an open-source rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS). The lab explores Snort's core operational modes (Sniffer, Logger, and IDS/IPS), traffic log processing, PCAP file investigation, and writing custom local rules to detect specific malicious flags and indicators.

2. IDS vs. IPS Core Concepts

<a id="ids-vs-ips-core-concepts"></a>

* **Intrusion Detection System (IDS):** Passive traffic monitoring that triggers alerts when suspicious activity is detected.
  * *Network-Based IDS (NIDS):* Monitors traffic flow across an entire subnet.
  * *Host-Based IDS (HIDS):* Monitors traffic flow on a single endpoint device.
* **Intrusion Prevention System (IPS):** Active protection solution responsible for stopping, preventing, or terminating suspicious events as soon as they are identified.
  * *Host-Based IPS (HIPS):* Terminates connections on a single device.
  * *Network-Based IPS (NIPS):* Protects traffic across an entire subnet by terminating flagged connections.
  * *Behavior-Based IPS:* Identifies network anomalies and terminates connections via behavior analysis.
  * *Wireless IPS:* Protects wireless traffic and mitigates wireless attacks.

---

3. Snort Operation Modes
<a id="snort-operation-modes"></a>

* **Sniffer Mode:** Real-time packet observation (`-v`, `-d`, `-e`, `-X`, `-i`).
* **Logger Mode:** Capturing and storing packet logs to disk (`-l`, `-K ASCII`, `-r`, `-n`).
* **IDS/IPS Mode:** Analyzing traffic against predefined rule databases and taking defensive actions (`-c`, `-T`, `-N`, `-D`, `-A`).
---
## 4. 📑 Lab Walkthrough & Documentation
<a id="lab-walkthrough--documentation"></a>

Due to the extensive nature of this practical lab, including packet forensic tasks, traffic generator scripts, pcap investigations, and custom local rule syntax, the full step-by-step documentation and evidence screenshots have been placed in a dedicated file:

👉 **[Read the Full Step-by-Step Snort Lab Walkthrough](./Snort-Lab-Walkthrough.md)**

---

## 5. Tools & Technologies Used
<a id="tools--technologies"></a>
* **Snort (v2/v3)** (NIDS/NIPS packet processing and rule matching)
* **Linux Terminal & Shell Scripts** (`traffic-generator.sh`, log analysis)
* **PCAP Analysis Tools** (`mx-1.pcap`, `mx-2.pcap`, `task9.pcap`)

---

## 6. Conclusion
<a id="conclusion"></a>

> **Snort provides robust capabilities for network visibility, attack surface monitoring, and active traffic defense. Writing custom detection rules is crucial for tailoring an NIDS/NIPS to address specific threat vectors.**
