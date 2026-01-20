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
Step 1: Display Network Interfaces

First, identify the available network interfaces on the system.

sudo ifconfig

<img width="803" height="542" alt="1" src="https://github.com/user-attachments/assets/2e82ac98-cac1-4264-ba18-22251521bb1a" />


Step 2: List Available Interfaces for tcpdump

Display the list of interfaces from which tcpdump can capture packets.

sudo tcpdump -D

<img width="1470" height="956" alt="step2" src="https://github.com/user-attachments/assets/3830b142-2335-4530-9e5b-11f1224650dd" />


Step 3: Capture Live Traffic on an Interface

Capture 5 packets on the eth0 interface with verbose output.

sudo tcpdump -i eth0 -v -c5

<img width="1470" height="956" alt="3" src="https://github.com/user-attachments/assets/d1625c95-ba1e-4740-ba20-1499683947c2" />

Step 4:Capture HTTP Traffic and Save to a File
Capture 9 packets on port 80 (HTTP traffic) and write them to a file named capture.pcap.
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &

<img width="596" height="59" alt="step 4" src="https://github.com/user-attachments/assets/ccd1130d-063c-472f-befa-9e4fc5d82e89" />


Step 5: Generate Traffic

Use curl to generate HTTP requests and trigger capture activity.

curl opensource.google.com

<img width="577" height="89" alt="5" src="https://github.com/user-attachments/assets/1a544875-e6c5-434f-9740-b06023a85b89" />


Step 6: Verify the Capture File

Confirm that the capture file was successfully created.

ls -l capture.pcap

<img width="727" height="77" alt="6" src="https://github.com/user-attachments/assets/fe109ef6-4292-4e6a-b0bb-ec13d8a31654" />


Step 7: Read the Capture File (Verbose Output)

Analyze the captured packets with detailed output.

sudo tcpdump -nn -r capture.pcap -v

<img width="1470" height="956" alt="step 7" src="https://github.com/user-attachments/assets/ef4c0d97-9b88-4bd4-a077-d9d8f42a089b" />


Step 8: Analyze Packets in Hex and ASCII Format

View packet contents in both hexadecimal and ASCII formats for deeper analysis.

sudo tcpdump -nn -r capture.pcap -X

<img width="1470" height="956" alt="step8" src="https://github.com/user-attachments/assets/ef515ad4-9f8d-4dc1-a303-16e33ec73989" />


Summary:

Identified network interfaces
Captured live network traffic
Saved HTTP packets into a capture file
Analyzed and inspected packet details
This hands-on process demonstrates essential tcpdump workflow skills for network analysis and troubleshooting.












