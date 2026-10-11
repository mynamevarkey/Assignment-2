# PCCST501 Computer Networks - Assignment 3

**Module 3: Data-Link Layer, Wireless LANs & Mobile IP**
**Title:** LAN, Ethernet & Wireless Network Investigation
**Course Outcome:** CO3
**Due date:** 17 August 2026
**Submitted by:** Varkey  |  Roll No.: ____________

## Overview

This repository holds my report and supporting evidence for Assignment 3. The report analyses how the data-link layer provides framing, MAC addressing, node-to-node delivery and access to shared media, with emphasis on Ethernet and IEEE 802.11 wireless networking, and ends with Mobile IP.

## Repository structure

```
pccst501-assignment3/
|-- README.md
|-- report/
|   `-- PCCST501_Assignment3_Report.pdf
|-- captures/
|   |-- ethernet_capture.pcapng        # Q3 wired capture
|   `-- wlan_capture.pcapng            # Q10 wireless monitor-mode capture
|-- screenshots/
|   |-- q3_ethernet_frames.png         # packet list with eth.src / eth.dst columns
|   |-- q3_ethernet_header.png         # expanded Ethernet II tree
|   |-- q4_mac_table.png               # switch MAC address table
|   `-- q10_wlan_frame.png             # decoded 802.11 frame
|-- diagrams/
|   |-- ethernet_frame                 # Q2
|   |-- wlan_design                    # Q8
|   `-- mobile_ip                      # Q9
`-- docs/
    `-- references.md
```

## Question index

| Q | Topic | Report section |
|---|-------|----------------|
| 1 | Data-link layer responsibilities; LLC vs MAC | Q1 |
| 2 | Ethernet frame format and fields | Q2 (Figure 2.1) |
| 3 | Wireshark capture, MAC addresses of 5+ frames | Q3 |
| 4 | Switch MAC learning and forwarding table | Q4 (Figure 4.1) |
| 5 | Hub vs switch vs bridge | Q5 (comparison table) |
| 6 | CSMA/CD and full-duplex switched Ethernet | Q6 |
| 7 | CSMA/CA in 802.11 vs CSMA/CD | Q7 (Figure 7.1) |
| 8 | Wireless LAN design for a college lab | Q8 (Figure 8.1) |
| 9 | Mobile IP | Q9 (Figure 9.1) |
| 10 | Wired vs wireless frame comparison | Q10 (Figure 10.1, comparison table) |

## Deliverables checklist

- [x] PDF report
- [x] Ethernet frame diagram
- [ ] Wireshark screenshots (add my own live captures to `screenshots/`)
- [x] Wireless LAN design
- [x] Comparison tables
- [x] README.md

## How the evidence was produced

**Wired capture (Q3)**
1. Open Wireshark on the Ethernet interface and start capturing.
2. Generate traffic: `ping <gateway>`, `nslookup example.com`, open a web page.
3. Filter with `arp || icmp || dns`; add `eth.src` and `eth.dst` as columns.
4. Save as `captures/ethernet_capture.pcapng` and screenshot the packet list and the expanded *Ethernet II* tree.

**Wireless capture (Q10)**
```bash
sudo ip link set wlan0 down && sudo iw dev wlan0 set type monitor
sudo ip link set wlan0 up && sudo iw dev wlan0 set channel 6
wireshark -i wlan0 -k
```
Useful filters: `wlan.fc.type_subtype == 0x08` (beacons), `wlan.addr == <station MAC>`.

**Switch table (Q4)**
```
Switch# clear mac address-table dynamic
Switch# show mac address-table dynamic
```

## References

1. IEEE Std 802.3-2022, *IEEE Standard for Ethernet*.
2. IEEE Std 802.11-2020, *Wireless LAN MAC and PHY Specifications*.
3. IEEE Std 802.2-1998, *Logical Link Control*.
4. RFC 5944, *IP Mobility Support for IPv4, Revised*; RFC 6275, *Mobility Support in IPv6*; RFC 826, *ARP*.
5. Kurose & Ross, *Computer Networking: A Top-Down Approach*; Forouzan, *Data Communications and Networking*; Tanenbaum & Wetherall, *Computer Networks*.
6. Wireshark User's Guide, https://www.wireshark.org/docs/

## Submission

Repository link submitted through the course Google Form.
