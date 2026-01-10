https://www.loom.com/share/850a771235e741f7a42fb8ec787ec1e1
# Capturing and Analyzing Network Traffic with TCPdump

## Introduction

TCPdump is a powerful command-line packet analyzer used by security analysts and network engineers to capture and inspect network traffic in real time. It helps identify suspicious activity, troubleshoot network issues, and understand how data moves across a network.

In this lab, you will capture live network traffic, save it to a file, and analyze packet data using various TCPdump options.

---

## Objectives

By the end of this lab, you will be able to:

- Identify available network interfaces
- Capture live network traffic using TCPdump
- Filter traffic by port
- Save captured packets to a `.pcap` file
- Analyze captured traffic in verbose and hex formats

---

## Prerequisites

- Linux-based system
- Administrative (sudo) privileges
- TCPdump installed

---

## Step 1: Display Network Interfaces

First, identify the available network interfaces on the system.

```bash
sudo ifconfig

Step 2: List Available Interfaces for TCPdump
Use TCPdump to list all interfaces it can capture traffic from.
sudo tcpdump -D

Step 3: Capture Live Traffic on an Interface
Capture 5 packets on the eth0 interface with verbose output.
sudo tcpdump -i eth0 -v -c5
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
22:24:18.910372 IP 
(tos 0x0, ttl 64, id 5802, offset 0, flags [DF], proto TCP (6), length 134)
7acb26dc1f44.5000 > nginx-us-east1-c.c.qwiklabs-terminal-vms-prod-00.internal.59788:
Flags [P.], cksum 0x5851 (incorrect > 0x30d3), seq 1080713945:1080714027, 
ack 62760789, win 501, options [nop,nop,TS val 1017464119 ecr 3001513453], length 82
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &

Step 4: Capture HTTP Traffic and Save to a File
Capture 9 packets on port 80 (HTTP traffic) and write them to a file named capture.pcap.

Step 5: Generate Traffic
Use curl to generate HTTP traffic.
curl opensource.google.com

Step 6: Verify the Capture File
Confirm that the capture file was created.
ls -l capture.pcap

Step 7: Read the Capture File (Verbose Output)
Analyze the captured packets with verbose details.
sudo tcpdump -nn -r capture.pcap -v

Step 8: Analyze Packets in Hex and ASCII Format
View packet contents in both hexadecimal and ASCII formats.
sudo tcpdump -nn -r capture.pcap -X
