# **Network Traffic Analysis with tcpdump**

## **Project Overview**
The goal of this exercise was to identify network interfaces, inspect network traffic, capture packet data, and filter captured network traffic using `tcpdump`. The scenario takes place on a virtual Linux system simulating live network traffic.

---

## **Task 1: Identify Network Interfaces**
![Alt Text](PKT%201.png)
1. First the `ifconfig` command is used to list available network interfaces.
   - This displays `eth0` as the primary Ethernet interface and `lo` as the loopback interface 
 for internal communications.

![Alt Text](PKT%202.png)

2.  The `sudo tcpdump -D` command reveals all network interfaces capable of packet capture.


---

## **Task 2: Inspect Network Traffic with tcpdump**
![Alt Text](PKT%203.png)
1. The live network packet data is then filtered from the `eth0` interface with `tcpdump`and is run with the following options:
   - `-i eth0`: Is used to capture data specifically from the `eth0` interface.
   - `-v`: Displays detailed packet information.
   - `-c5`: Defines that 5 packets are captured before exiting.

2. The result gives us the relevant network packet details including timestamps, source/destination IPs, TCP flags, and checksums.

---

## **Task 3: Capture Network Traffic**
![Alt Text](PKT%204.png)
1. I now need to restrict our search by using a filter and other tcpdump configuration options to save a sample that contains only web (TCP port 80) network packet data before then saving it to a file:
   - `-nn`: This Disables the IP/port resolution to avoid security risks.
   - `-c9`: Defines that 9 packets are captured.
   - `-w capture.pcap`: Saves the data to `capture.pcap`.

![Alt Text](PKT%205.png)

2. Generated HTTP traffic using:
   ```bash
   curl opensource.google.com
   ```
![Alt Text](PKT%206.png)

3. Verified successful packet capture:
   ```bash
   ls -l capture.pcap
   ```

---

## **Task 4: Filter Captured Packet Data**
![Alt Text](PKT%207.png)
![Alt Text](PKT%207-2.png)
1. Analyzed packet headers from the `capture.pcap` file:
   ```bash
   sudo tcpdump -nn -r capture.pcap -v
   ```
   - Displayed timestamp, protocol, IP details, flags, and checksum.

![Alt Text](PKT%208.png)
![Alt Text](PKT%208-2.png)
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

