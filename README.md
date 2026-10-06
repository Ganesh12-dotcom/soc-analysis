# soc-analysis
this is the trace file i have solved uploded on the malware.net 
# Incident Report: Natureforce Malware Infection

## Executive Summary
A malicious executable (`runner_ilove.exe`) was delivered over an unencrypted connection to an internal endpoint. The payload is associated with the CNCMachineRMS RAT. The infected host was identified through PCAP analysis, and the malicious binary was successfully extracted and hashed for EDR blocklisting.

## Victim & Environment Details
| Asset Attribute | Identified Detail |
| :--- | :--- |
| **Hostname** | DESKTOP-4VGYQX7 |
| **Victim IP Address** | 10.10.1.128 |
| **Victim MAC Address** | 00:22:fb:ec:7e:e7 |
| **Domain Controller** | 10.10.1.10 (WIN-LEKBU2OY51N) |

## Indicators of Compromise (IOCs)
* **Malicious File Name:** `runner_ilove.exe`
* **SHA-256 Hash:** b789adce70c028a6d17be45ec34667aa95586350ee0c4057e75b138b1ad35061
* **Attacker IP Address:** 107.175.82.242
* **C2 Traffic Port:** TCP 443 (195.64.128.106)

## Investigation Methodology
1. **Network Flow Analysis:** Filtered `ip.addr == 107.175.82.242` to track the initial payload delivery.
2. **Endpoint Identification:** Correlated the internal IP address with the specific machine hostname using Kerberos authentication packets.
3. **Payload Extraction:** Extracted the payload via Wireshark's HTTP object export function.
4. **Integrity Verification:** Executed `sha256sum` against the extracted binary to generate an immutable IOC.
