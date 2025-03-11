# **Network Traffic Analysis with tcpdump**

## **Project Overview**
The goal of this exercise was to identify network interfaces, inspect network traffic, capture packet data, and filter captured network traffic using `tcpdump` on a Linux system.

---

## **Task 1: Identify Network Interfaces**
![Alt Text](PKT%201.png)
1. Used the `ifconfig` command to list available network interfaces.
   - Identified `eth0` as the primary Ethernet interface.
   - Noted the loopback interface `lo` for internal communications.

![Alt Text](PKT%202.png)

2. Verified available interfaces for packet capture using:
   ```bash
   sudo tcpdump -D
   ```
   - Listed all interfaces capable of capturing network traffic.

---

## **Task 2: Inspect Network Traffic with tcpdump**
![Alt Text](PKT%203.png)
1. Captured and analyzed live packet data from `eth0`:
   ```bash
   sudo tcpdump -i eth0 -v -c5
   ```
   - `-i eth0`: Captured data from interface `eth0`.
   - `-v`: Displayed detailed packet information.
   - `-c5`: Captured 5 packets before exiting.

2. Observed network packet details including timestamps, source/destination IPs, TCP flags, and checksums.

---

## **Task 3: Capture Network Traffic**
![Alt Text](PKT%204.png)
1. Captured HTTP (port 80) traffic and saved it to a file:
   ```bash
   sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
   ```
   - `-nn`: Disabled IP/port resolution to avoid security risks.
   - `-c9`: Captured 9 packets.
   - `-w capture.pcap`: Saved data to `capture.pcap`.

2. Generated HTTP traffic using:
   ```bash
   curl opensource.google.com
   ```

3. Verified successful packet capture:
   ```bash
   ls -l capture.pcap
   ```

---

## **Task 4: Filter Captured Packet Data**

1. Analyzed packet headers from the `capture.pcap` file:
   ```bash
   sudo tcpdump -nn -r capture.pcap -v
   ```
   - Displayed timestamp, protocol, IP details, flags, and checksum.

2. Extracted detailed hexadecimal and ASCII data:
   ```bash
   sudo tcpdump -nn -r capture.pcap -X
   ```
   - Helped in deep packet inspection for forensic analysis.

---

## **Conclusion**
This exercise provided hands-on experience with `tcpdump` to analyze network traffic. We successfully:
- Identified network interfaces.
- Captured and inspected live traffic.
- Saved network traffic to a file.
- Filtered and analyzed captured data.

Understanding `tcpdump` is crucial for network troubleshooting, security analysis, and forensic investigations.

