---
permalink: basic-network-troubleshooting-with-powershell/
audit_date:
title: 'Basic Network Troubleshooting with Powershell'
type: article
created_date: '2021-05-05'
created_by: Dave Myers
last_modified_date: '2021-05-06'
last_modified_by: Dave Myers
product: Cloud Product
product_url: cloud-product
---


**This article is to help assist in checking basic network connectivity issues using Powershell cmdlets. We'll show you some basic network troubleshooting tools for checking network connectivity and configuration.**

### Prerequisites
Windows Powershell 

### Prowershell Syntax
A quick note on Powershell Cmdlets syntax. This is useful to understanding what the cmdlet is expected to perform.
1. Powershell is not case sensitive.
2. Cmdlets always use a Verb-Noun structure. This is helpful with understanding the function of a given command.
3. Cmdlets output can be modified with parameters.
4. Parameter names always start with a dash like -name, -object, -list
5. "**Get-Help** "***Command Name***" *-Full*" - Will return help for command usage.

### Powershell networking cmdlets functions and techniques.
    
1) **Get-NetAdapter**  - List all Network Adapters
    - Ex: **Get-NetAdapter**  *-Name* "Ethernet" 
    - The *-Name* argument is added to filter out for a specific network adapter in the output. In this case searching for  Ethernet adapter (Wildcards can be added to the begining and end of argument criterier.) to further specify your search.
2) **Test-NetConnection** *-ComputerName* "Hostname or IP" 
    - Test network connectivity to another computer. Hostname should be used when testing network connectivity. If you get an error "Host not Found" then try the command again using the ipaddress of the destination. If it returns successfully this would indicate there may be an issue with DNS resolution. 
3) **Test-NetConnection** "Hostname or IP address" *-Port* #  
    - Will test connectivity to a specific port of the destination.
4) **Get-NetAdapter** *-Name* "Local Area Connection" | **Get-DnsClientServerAddress** 
    - Gets DNS Server Address.
5) **Resolve-DnsName** 'Hostname or IP'
    - Get the DNS Server for a remote host or IP.
6) **Get-NetRoute**
    - Returns Route table for all interfaces. 
7) **Disable-NetAdapter** *-Name* "Adapter Name" and **Enable-NetAdapter** *-Name* "Adapter Name"
    - Will Enable or Disable a network interface.
8) **Get-NetIPConfiguration**
    - Returns IP configuration details.