- [Types of clients](#types-of-clients)
  - [Servers](#servers)
  - [Server models](#server-models)
- [AuthZ vs AuthN](#authz-vs-authn)
- [Authentication protocols](#authentication-protocols)
  - [Kerberos](#kerberos)
  - [TSL/SSL](#tslssl)
  - [Authorization](#authorization)
- [Network security](#network-security)
  - [Access control](#access-control)
  - [Malware](#malware)
  - [Using analytics](#using-analytics)
  - [Azure tools](#azure-tools)
  - [VPN](#vpn)
- [Network security zones](#network-security-zones)
  - [Trusted + Private zones](#trusted--private-zones)
  - [Public zones](#public-zones)
  - [Perimeter network](#perimeter-network)
  - [zone-filtering policies](#zone-filtering-policies)
- [Firewalls](#firewalls)
  - [Firewall types](#firewall-types)
- [Azure network security tools](#azure-network-security-tools)
- [Network monitoring](#network-monitoring)
  - [Agent vs Agentless based monitoring](#agent-vs-agentless-based-monitoring)
  - [Protocols](#protocols)
- [FCAPS](#fcaps)


## Types of clients

- thick clients use local storage & use local gpu
- hybrid clients don't use local storage but use local cpu
- thin clients don't use local storage nor local cpu
- thick client: laptops, desktops
- thin client: web apps
- hybrid: ??

### Servers

- consist of hardware, cpus, cores, memory
- associated with switches, routers, load balancers & firewalls

### Server models

- request-response: client sends a request to a server, the server performs an activity, sends a response back to the client. Examples: REST API, GraphQL 
- peer-to-peer (P2P): every device connected to the network is both a client & a server. Each network device can send requests to other devices on the network
- publish-subscribe: is a messaging pattern, with clients subscribing to a service running on a server. Once the server receives a message (or an activity has been performed?), the server sends a response to each client that's subscribed. Example: RSS

## AuthZ vs AuthN

To authenticate users commonly involves one or more of the following
- password
- 2FA, or one-time-codes
- token-based
- biometric auth
- transactional/context rules
- SSO

## Authentication protocols

### Kerberos

- microsoft uses Kerberos as default auth protocol
- involves 3 stages: Authentication Server (AS), Database, Ticket Granting Server (TGS)

### TSL/SSL

- encrypted protocol 
- used in browser, identified by the padock icon 
- also used by files transfers, VOIP, email
- SSL is predecessor of TLS and is now deprecated

### Authorization

- once authentication has been completed, user can begin requesting/using service and apps they are authorized to do so

## Network security

### Access control

Limit users to the permission level they require for their action on your network

### Malware

Types of malware include

- ransomware
- viruses
- spyware
- trojans

### Using analytics

Monitoring common behaviours for users can help raise security concerns. Example being if a user suddenly logs in to their network/app from a completely different location & timezone. Applying security policies and verification codes can help mitigate this. 

### Azure tools

- Azure Network Watcher for analyzing web traffic running on Azure

### VPN

- virtual private networks create an encrypted tunnel (using TLS) to faciliate secure comms between networks

## Network security zones

### Trusted + Private zones

- these zones contain resources/devices that should never be accessible to anyone outside your org
- examples include printers, workstations & internal servers
- the resources int his zone can be locked down by configuring static IP addresses 

### Public zones

- this zone is for resources that can be accessed by users outside your org, i.e unrestricted (unless configured otherwise)

### Perimeter network

- this zone is where resources/services can be configured for targeted access 

### zone-filtering policies

- **inside-to-outside & inside-to-perimeter-network**: handles all traffic originating from inside the org
- **outside-to-inside**: blocks incoming public traffic into the internal network, unless configured as a trusted source for internal users
- **outside-perimeter-network**: inspects all traffic from outside heading to the perimeter network
- **perimeter-network-to-outside**: perimeter network traffic that leaves the network

## Firewalls

### Firewall types

- **hardware firewall**: installed on physical devices part of the network, e.g routers
- **software firewall**: configured on servers or workstations
- **application-layer firewalls**: target and filter application traffic, HTTP/S requests can be blocked
- **packet filtering firewalls**: target data packets travelling in the network, certain packets can be blocked
- **circuit-level firewalls**: targets TCP & UDP connections are valid, includes checks against source/destination addresses meet defined rules
- **proxy server firewalls**: sit between clients and requested networks, allowing monitoring, filtering of in-bound/out-bound requests
- **stateful firewalls**: network connection characteristics are stored, allowing filtering of traffic based on certain data & rules
- **next-generation firewalls**: deeper versio of **stateful**, includes VPN + packet filtering support

## Azure network security tools

- recommend disabling ssh/rdp access in favor of established VPNs
- use load balances to distribute network traffic across servers, improving performance for end users
- Azure provides DDoS monitoring and mitigations, in-built into Azure

## Network monitoring

Networks monitoring includes
 
- switches
- routers
- servers
- firewalls

### Agent vs Agentless based monitoring

- agents are installed on a target device to gather data (e.g process performance, hardware stats) to send to a solution which then analyses said data
- alternatively. agentless solutions themselves analyse & read the data from a device. This method is less granular as agents, as it runs at a higher level
- gathering data on a machine can contribute to a higher load on that machine, regardless of approach

### Protocols

- Simple Network Management Protocol (SNMP): Linux servers, switchers, routers use SNMP. An SNMP agent collects data on a device to send back to an NMS (network monitoring and management solution)
- Windows Management Instrumentation (WMI): Windows use WMI to read data & trigger processes on Windows devices. The next iteration of WMI is known as Windows Management Infrastructure (confusingly, also known as WMI)
- System Logging Protocol (Syslog): this protocol allows devices to send logs & events on servers

## FCAPS

The categories of network management can be summarised as FCAPS: F**ault, **C**onfiguration, **A**ccounting, **P**erformance and **S**ecurity

- **F**ault management: relates to the processes and tasks used to identify and resolve faults on the network
- **C**onfiguration management: includes aspects like collecting information based on changes made to device configurations, physical hardware, software updates and network changes
- **A**ccounting/administration: applies when you're dealing with a network used in a service-provider setting, and all the tasks and functions that apply. With service-provider networks, usage needs to be monitored to track utilization and billing for users. Administration includes tasks like managing permissions and user passwords
- **P**erformance management: covers anything that's done to manage the performance of your network. Aspects include monitoring throughput, monitoring usage, and improving response times
- **S**ecurity: encompasses all the tasks you do to secure your network. These tasks include protecting devices, restricting access to network resources, or protecting user activity in the network