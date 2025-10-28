Packet Filtering Firewall (Java)

A Java-based packet filtering firewall that inspects and filters network packets based on predefined user rules such as IP address, port, and protocol.
This project demonstrates the working principles of a network-layer firewall using packet inspection and rule-based decision-making.

📋 Table of Contents

Overview

Features

System Architecture

Prerequisites

Installation

Usage

Configuration

Example Rules

Testing

Future Enhancements

Contributors

License

🚀 Overview

This Java project simulates the working of a Packet Filtering Firewall — one of the most common types of firewalls used in networks.
It examines incoming and outgoing packets based on a set of filtering rules and determines whether to allow or block them.

The main goals of this project are:

To demonstrate basic network packet filtering concepts.

To show how firewall rule sets can be implemented in software.

To serve as an educational tool for understanding firewalls and network security.

⚙️ Features

✅ Rule-based packet filtering (ALLOW / DENY)
✅ Filtering by IP address, port number, and protocol (TCP/UDP/ICMP)
✅ Logging of allowed and blocked packets
✅ Modular code design (easy to extend)
✅ Command-line configuration and rule loading
✅ Works on simulated or captured packet data (no kernel-level access needed)

🧩 System Architecture

Packet Capture — Simulated or captured network packet data is read.

Packet Parser — Extracts source IP, destination IP, ports, and protocol.

Rule Engine — Compares packet details against user-defined rules.

Decision Module — Decides whether to ALLOW or DROP the packet.

Logger — Records all actions for analysis.

Flow:

Incoming Packet → Parse Header → Match Rule → (ALLOW / DROP) → Log

🧰 Prerequisites

Java 8 or higher

(Optional) Wireshark / tcpdump if testing with live traffic

Basic understanding of IP and TCP/UDP networking

🔧 Installation
# Clone the repository
git clone https://github.com/kurachatarani1/packet-filtering-firewall.git

# Navigate into the project directory
cd packet-filtering-firewall

# Compile the Java files
javac -d bin src/*.java

# Run the program
java -cp bin Main


If the project uses packages:

javac -d bin src/com/firewall/*.java
java -cp bin com.firewall.Main

▶️ Usage

You can run the firewall and specify a rule file and optional log file:

java -cp bin com.firewall.Main rules.txt log.txt


Or interactively enter rules through the console (depending on implementation).

⚙️ Configuration (Rules File Format)

Each line in rules.txt represents a rule:

ACTION  PROTOCOL  SRC_IP     SRC_PORT   DST_IP     DST_PORT

Example:
ALLOW TCP 192.168.1.5  ANY   10.0.0.2  80
DROP  UDP ANY          ANY   ANY       53
DROP  ICMP ANY         ANY   ANY       ANY


Explanation:

Allows TCP traffic from 192.168.1.5 to 10.0.0.2:80

Blocks all UDP packets to port 53

Drops all ICMP (ping) packets

🧪 Testing

You can simulate or test the firewall by:

Sending sample packets using Java socket code.

Loading a set of packets from a log or pcap file.

Observing whether packets are allowed or dropped.

For example:

java -cp bin com.firewall.Main rules.txt sample_packets.txt


Expected Output:

Packet [TCP 192.168.1.5 → 10.0.0.2:80] → ALLOWED
Packet [UDP 192.168.1.9 → 8.8.8.8:53] → DROPPED
