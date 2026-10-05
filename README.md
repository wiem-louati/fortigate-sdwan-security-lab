# FortiGate SD-WAN & Network Security Lab

**An independent project exploring network segmentation, security policies and resilient WAN connectivity in EVE-NG.**

| Project detail | Description |
|---|---|
| Environment | EVE-NG virtual lab |
| Technologies | FortiGate, Cisco IOS, Linux, Windows |
| Duration | Approximately two months, June–July 2026 |
| Ownership | Independently designed, implemented and tested |
| Focus | Firewall security, network segmentation and SD-WAN failover |

## Overview

After earning my Fortinet NSE 4 certification, I chose to build a complete network security infrastructure from an empty topology. My goal was to translate certification knowledge into practical experience and understand how routing, security policies and WAN redundancy interact in a working environment.

I was responsible for the entire project: architecture design, device configuration, troubleshooting and functional validation.

## Network Architecture

The lab consisted of a FortiGate firewall connected to two Cisco routers representing separate internet providers. Each router used NAT overload to simulate upstream internet connectivity.

The architecture separated the network into WAN, LAN and DMZ zones. Linux and Windows machines acted as clients and servers, generating traffic to test connectivity and policy enforcement.

The two simulated providers created separate paths for testing WAN redundancy within the virtual environment.

## Technical Implementation

### Network segmentation and firewall policies

I configured separate network zones and firewall policies to define which traffic could pass between them.

This required considering both connectivity requirements and security boundaries: which services should be reachable, from which sources, and through which interfaces.

### Security profiles

I configured the following FortiGate security profiles:

- Intrusion prevention system (IPS)
- Antivirus
- Web filtering
- DNS filtering

These configurations formed the security inspection layer. Configuring a profile and demonstrating its detection effectiveness are separate tasks; the validation described below focuses on traffic permissions and WAN failover.

### SD-WAN and resilient connectivity

I configured both WAN connections as SD-WAN members and implemented:

- Link health monitoring
- Performance SLA checks
- SD-WAN traffic-selection rules
- Automatic failover when a WAN path became unavailable

The objective was to maintain an available forwarding path when one simulated provider connection failed.

## Validation Approach

I treated testing as part of implementation. A configuration being accepted by a device was only the starting point; I also checked its effect on traffic.

| Test | Method | Behaviour checked |
|---|---|---|
| WAN failover | Disconnect a WAN link while generating traffic | Traffic switches to the available WAN connection |
| Permitted traffic | Generate traffic matching an allow policy | Intended communication succeeds |
| Restricted traffic | Attempt communication outside the permitted flows | The firewall blocks the traffic |

These tests helped me assess whether the architecture behaved as intended under both normal conditions and simulated failures.

The project demonstrated functional failover in a virtual lab. It did not establish production-scale performance, zero packet loss or uninterrupted preservation of existing sessions.

## Skills Developed

- Designing a network with explicit security boundaries
- Configuring FortiGate firewall policies and security profiles
- Configuring Cisco routing and NAT overload
- Implementing SD-WAN with health checks and failover
- Using Linux and Windows hosts for practical traffic testing
- Troubleshooting interactions between routing, NAT and firewall policies
- Validating system behaviour through controlled tests

## Reflection

The most valuable part of this project was learning to reason about the architecture as a complete system. Routing, NAT, firewall policies and SD-WAN each have their own configuration, but successful communication depends on their interaction.

Working independently taught me to break a large task into manageable layers, establish basic connectivity, introduce security controls and test the resulting behaviour before proceeding.

This is also the approach I would bring to experimental research: define the intended behaviour, build a controlled environment, introduce failures and evaluate the results.

## Repository Contents

This initial version contains the project overview. Original configuration exports, topology screenshots and detailed test records are not yet included.
# fortigate-sdwan-security-lab
FortiGate SD-WAN and network security lab in EVE-NG:segmentation, firewall policies and WAN failover
