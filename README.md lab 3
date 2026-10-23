# COMPUTER NETWORKS LAB – LAB 3

## Experiment Title
**Router Configuration (Configuring Passwords, Console, VTY, and Interface Configuration)**

## 1. Aim
To configure a Cisco router using the Command Line Interface (CLI), secure administrative and remote access by setting console, enable, and VTY passwords, configure IP addresses on Gigabit Ethernet interfaces to connect two distinct subnets, and verify inter-subnet routing.

## 2. Software and Hardware Requirements
- Cisco Packet Tracer
- Cisco 2911 Integrated Services Router (Router0)
- Two PCs (PC0 and PC1)
- Copper Straight-Through cables (RJ-45)
- Windows PC to run Cisco Packet Tracer

## 3. Brief Theory

### Router
A router is a networking device that operates at Layer 3 (Network Layer) of the OSI model. It forwards data packets between different networks using IP addresses and routing tables.

### Cisco IOS Command Modes
- **User EXEC Mode (`Router>`):** Used for basic diagnostic commands.
- **Privileged EXEC Mode (`Router#`):** Provides access to administrative and troubleshooting commands. It is entered using the `enable` command.
- **Global Configuration Mode (`Router(config)#`):** Used to modify system-wide settings through `configure terminal`.
- **Interface Configuration Mode (`Router(config-if)#`):** Used to configure interface IP addresses and activate interfaces.
- **Line Configuration Mode (`Router(config-line)#`):** Used to configure console and VTY access.

### Router Security
Passwords help prevent unauthorized access to network devices. The console password protects direct console access, the enable password restricts access to privileged EXEC mode, and VTY passwords secure remote terminal access through protocols such as Telnet.

### Inter-Subnet Routing
Two devices belonging to different IP networks cannot communicate directly through Layer 2 switching alone. A router forwards packets between these networks. Each PC must have a default gateway configured to point to the router interface connected to its subnet.

## 4. Network Topology

The network consists of a Cisco 2911 router connected to two PCs through separate Gigabit Ethernet interfaces.

- PC0 is connected to Router0 GigabitEthernet0/0.
- PC1 is connected to Router0 GigabitEthernet0/1.
- LAN 1 uses the network address `192.168.1.0/24`.
- LAN 2 uses the network address `192.168.2.0/24`.

**Topology:**

`PC0 ↔ Router0 ↔ PC1`

The router acts as the default gateway for both networks and enables communication between the two subnets.

## 5. IP Address Configuration

| Device | Interface | IPv4 Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| Router0 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 | N/A |
| Router0 | GigabitEthernet0/1 | 192.168.2.1 | 255.255.255.0 | N/A |
| PC0 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC1 | FastEthernet0 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |

Both PCs use static IP addressing. Each PC uses the IP address of its corresponding router interface as its default gateway.

## 6. Step-by-Step Procedure

1. Open Cisco Packet Tracer and select the Logical workspace.
2. Place a Cisco 2911 router and two PCs (PC0 and PC1) in the workspace.
3. Connect PC0 FastEthernet0 to Router0 GigabitEthernet0/0 using a Copper Straight-Through cable.
4. Connect PC1 FastEthernet0 to Router0 GigabitEthernet0/1 using another Copper Straight-Through cable.
5. Open Router0, select the CLI tab, and enter `no` to skip the initial configuration dialog if prompted.
6. Enter the commands below to configure console, enable, and VTY passwords.
7. Configure IP addresses on both router interfaces and enable them using `no shutdown`.
8. Save the router configuration.
9. Configure static IP addresses and default gateways on PC0 and PC1.
10. Verify the router interface status using `show ip interface brief`.
11. Test gateway reachability and communication between the two subnets using the `ping` command.

## 7. Router Configuration Commands

### Step 1: Configure Console Password

```text
Router> enable
Router# configure terminal
Router(config)# line console 0
Router(config-line)# password cisco
Router(config-line)# login
Router(config-line)# exit
```

### Step 2: Configure Enable Password

```text
Router(config)# enable password cisco
```

### Step 3: Configure VTY Password

```text
Router(config)# line vty 0 4
Router(config-line)# password cisco
Router(config-line)# login
Router(config-line)# exit
```

### Step 4: Configure Router Interface GigabitEthernet0/0

```text
Router(config)# interface gigabitEthernet 0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

### Step 5: Configure Router Interface GigabitEthernet0/1

```text
Router(config)# interface gigabitEthernet 0/1
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# end
```

### Step 6: Save the Configuration

```text
Router# copy running-config startup-config
```

Save the configuration when prompted.

## 8. PC Configuration

### PC0 Configuration

Open PC0 and navigate to **Desktop → IP Configuration**. Select Static and enter:

- IPv4 Address: `192.168.1.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`

### PC1 Configuration

Open PC1 and navigate to **Desktop → IP Configuration**. Select Static and enter:

- IPv4 Address: `192.168.2.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.2.1`

## 9. Testing and Verification

### A. Verify Router Interfaces

Execute the following command in the router CLI:

```text
Router# show ip interface brief
```

The configured interfaces should show the following addresses and statuses:

- GigabitEthernet0/0 — `192.168.1.1`, up/up
- GigabitEthernet0/1 — `192.168.2.1`, up/up

The unused interfaces GigabitEthernet0/2 and Vlan1 remain administratively down in the recorded experiment.

### B. Test Default Gateway Connectivity

From PC0, open **Desktop → Command Prompt** and execute:

```text
ping 192.168.1.1
```

The recorded test returned four replies, with 0% packet loss.

### C. Test Inter-Subnet Communication

From PC0, execute:

```text
ping 192.168.2.2
```

The recorded result was:

- The first packet timed out.
- The next three packets received replies from PC1.
- Packets sent: 4
- Packets received: 3
- Packets lost: 1
- Packet loss: 25%

The initial timeout was attributed in the experiment report to ARP address resolution while the router resolved PC1's MAC address. Subsequent packets were successfully routed to PC1.

## 10. Result

A network topology using a Cisco 2911 router and two PCs was configured in Cisco Packet Tracer. Console, enable, and VTY passwords were configured. The router interfaces GigabitEthernet0/0 and GigabitEthernet0/1 were assigned IP addresses and enabled. The PCs were configured with static IP addresses and appropriate default gateways. Inter-subnet communication was tested successfully after the initial ping timeout.

## 11. Conclusion

This experiment demonstrated router configuration using Cisco IOS CLI commands. Console, VTY, and privileged EXEC password configuration provided basic access protection. Configuring and enabling router interfaces established connectivity between two different IP subnets. Static IP addressing and default gateway configuration allowed the PCs to communicate through the router. The experiment also demonstrated how to verify interface status and test network connectivity using the ping command.

## 12. Screenshots / Practical Evidence

Add your actual Packet Tracer screenshots in the following order:

1. Network topology showing Router0 connected to PC0 and PC1.
2. PC0 static IP configuration.
3. Command Prompt showing ping tests to the default gateway and PC1.
4. Router CLI showing interface configuration, interface status, and saving the configuration.

## 13. GitHub Repository

**Suggested repository name:** `computer-networks-lab-3-router-configuration`

Recommended repository structure:

```text
computer-networks-lab-3-router-configuration/
├── README.md
├── screenshots/
│   ├── network-topology.png
│   ├── pc0-ip-configuration.png
│   ├── ping-test.png
│   └── router-cli.png
└── lab3.pkt
```

Upload the Packet Tracer `.pkt` file only if you have saved your own working project. Add your actual screenshots to the `screenshots` folder and use this report as the repository's `README.md`.
