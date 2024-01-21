---
layout: default
title: Computers
parent: PureNet
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Computers

Below is a list of all of the computers running on PureNet, including information about
 their hardware and software configuration

## Studio 1

### PURE-S1-01

- Stone PC-1210
  - i5-4570S
  - 16GB DDR3
  - 240GB SSD
- Windows 10 22H2, Domain Joined
- DHCP

### PURE-S1-02

- Stone PC-1210
  - i5-4570S
  - 8GB DDR3
  - 120GB SSD
- Windows 10 22H2, Domain Joined
- DHCP

## Studio 2

### PURE-S2-01

- Stone PC-1210
  - i5-4570S
  - 8GB DDR3
  - 240GB SSD
- Windows 10 22H2, Domain Joined
- DHCP


## Server Room

### Jack Hayes

- Dell Optiplex 7010 USFF
  - i3-2120
  - 4GB DDR3
  - 900GB HDD
- Fedora 39 Server Edition
- Static - `10.0.0.101`

### Clara Amfo

- Stone PC-1210
  - i5-4570S
  - 8GB DDR3
  - 120GB SSD
- Fedora 39 KDE
- Static - `10.0.0.104`

### Craig Charles

- Dell Optiplex 7010 USFF
  - i3-2120
  - 4GB DDR3
  - 900GB HDD
- OPNSense
- Static - `10.0.0.1`

### ReadyNAS

- Netgear ReadyNAS 204
  - Unknown hardware
  - 3x 1TB HDD, 1x 2TB HDD
- NASOS
- Static - `10.0.0.103`

### Paul O'Grady

- HPE Proliant DL380p Gen 8
  - 2x Xeon E5-2680 V2
  - 96GB ECC DDR3
  - 500GB SSD
  - 8x 900GB HDD (2 Spares)
- Proxmox 8
- Static - `10.0.0.100`
- iLO - `10.0.0.99`

## VMs

### Jordan North

- Paul O'Grady
  - 8 Cores
  - 16GB RAM
  - 64GB Boot
- Windows Server 2022
- Static - `10.0.1.1`

### Annie Mac

- Paul O'Grady
  - 8 Cores
  - 16GB RAM
  - 32GB Boot
  - 8x 900GB HDD (SAS HBA Passed through)
- TrueNAS Core 13
- Static - `10.0.1.2`

## The Cloud

### icecast-test.purefm.xyz

- Linode
  - 1 Core
  - 1GB RAM
  - 25GB SSD
- Debian 10
- Static - `80.85.85.21`