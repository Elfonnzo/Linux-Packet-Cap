# **Network Traffic Analysis with tcpdump**

## **Project Overview**
The goal of this exercise was to identify network interfaces, inspect network traffic, capture packet data, and filter captured network traffic using `tcpdump`. The scenario takes place on a virtual Linux system simulating live network traffic.

---

## **Task 1: Identify Network Interfaces**

1. First, the `sudo ifconfig` command is used to list all available network interfaces.
   - This displays `eth0` as the primary Ethernet interface and `lo` as the loopback interface 
which is used for internal communications.

![Alt Text](PKT%201.png)

2.  The `sudo tcpdump -D` command reveals all network interfaces capable of packet capture.

![Alt Text](PKT%202.png)

---

## **Task 2: Inspect Network Traffic with tcpdump**

1. The live network packet data is then filtered from the `eth0` interface with `tcpdump`and is run with the following options:
   - `-i eth0`: Is used to capture data specifically from the `eth0` interface.
   - `-v`: Displays detailed packet information.
   - `-c5`: Defines that 5 packets are captured before exiting.

![Alt Text](PKT%203.png)

2. The result gives us the relevant network packet details including timestamps, source/destination IPs, TCP flags, and checksums.

---

## **Task 3: Capture Network Traffic**

1. I now need to restrict my search by using a filter and other tcpdump configuration options to save a sample that contains only web (TCP port 80) network packet data before then saving it to a file:
   - `i eth0`: Captures the data from the eth0 interface.
   - `-nn`: This disables the IP/port resolution to avoid security risks.
   - `-c9`: Defines that 9 packets are captured before exiting.
   - `port 80` Filters only port 80 traffic. (This is the default HTTP port.)
   - `-w capture.pcap`: Saves the data to `capture.pcap`.
   - `&` This instructs the Bash shell to run the command in the background.

![Alt Text](PKT%204.png)

2. The `curl` command is then used to generate HTTP (TCP port 80) traffic from the website `opensource.google.com` which can then be captured.

![Alt Text](PKT%205.png)

3. I then verify the success of the packet capture by using the `ls -l capture.pcap` command.

![Alt Text](PKT%206.png)

---

## **Task 4: Filter Captured Packet Data**

1. Next I filter the packet header data from the `capture.pcap` file using the `sudo tcpdump` command along with the following options:
   - `nn`: Disables port and protocol name lookup.
   - `r`: Reads the capture data from the named file.
   - `v`: Displays detailed packet data.

![Alt Text](PKT%207.png)
![Alt Text](PKT%207-2.png)
 


2. The filtering command can also be extended to extract more detailed hexadecimal and ASCII data:
   - `nn`: Disables port and protocol name lookup.
   - `r`: Reads the capture data from the named file.
   - `x`: Displays the hexadecimal and ASCII output format packet data. This is primarily used to detect patterns or anomalies during malware analysis or forensic analysis.

![Alt Text](PKT%208.png)
![Alt Text](PKT%208-2.png)

---

## **Conclusion**
By utilising `tcpdump` and its associated options, I successfully analyzed network traffic and demonstrated how security analysts:
- Identify network interfaces.
- Capture and inspect live traffic.
- Save network traffic to a file.
- Filter and analyze captured data.


