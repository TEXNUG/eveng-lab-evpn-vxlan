# eveng-lab-evpn-vxlan
EVE-NG Multi-Tenant EVPN/VXLAN Lab topology 

<p align="center">
    <img src="media/lab-topo-2021_11_11.png" width="800"/>
</p>

## Overview

<p>This lab represents a dual datacenter network design, interconnected via L3 IP WAN / Core.  Local DataCenter Layer3 Leaf/Spine networks with EVPN overlay (eBGP over eBGP) within each DataCenter offer RED, BLUE, and GREEN tenant services for demo'ing Layer2 and Layer3 network availability.  An additional Layer3 network (RED) is attached to the IP WAN Core network, highlighting insertion of arbitrary Layer3 services into the overlay.
<p>The Out-Of-Band (OOB) management network is a bridge to a network interface on the EVE-NG host offering DHCP services as well as client connectivity to network nodes.


## Node Details

FRR01:  WAN Router 1<br>
  Open Source Node - debian 10 system running FRR
  Attachment point for VSR1K (L3 RED network extension)
FRR02:  WAN Router 2
  Open Source Node - debian 10 system running FRR
  Attachment point for RouteServer1 (FRR EVPN Route Server)
FRR03:  WAN Router 3
  Open Source Node - debian 10 system running FRR
  Attachment point for DataCenter2
FRR04:  WAN Router 4
  Open Source Node - debian 10 system running FRR
FRR05:  WAN Router 5
  Open Source Node - debian 10 system running FRR
  Attachment point for DataCenter1
    runs ISI (WAN), BGP (DC1 peer)

DC1SP1:  DataCenter 1 Spine
  Open Source Node - debian 10 system running FRR
  Attachment point for DC1 Leafs
   runs BGP (L3LS underlay for DC)
DC1LF1:  DataCenter 1 Leaf1
  Arista vEOS-Lab (freely available)
  Attachment points:
    Host1 (tenant GREEN)
    Host3 (tenant BLUE)
  runs BGP (eBGP underlay, eBGP Overlay)
DC1LF2:  DataCenter 1 Leaf2
  Arista vEOS-Lab (freely available)
  Attachment points:
    Host5 (tenant RED)
    Host7 (tenant GREEN)
  runs BGP (eBGP underlay, eBGP Overlay)


DC2SP1:  DataCenter 2 Spine
  Open Source Node - debian 10 system running FRR
  Attachment point for DC1 Leafs
   runs BGP (L3LS underlay for DC)
DC2LF1:  DataCenter 2 Leaf1
  Arista vEOS-Lab (freely available)
  Attachment points:
    Host2 (tenant GREEN)
    Host4 (tenant BLUE)
  runs BGP (eBGP underlay, eBGP Overlay)
DC2LF2:  DataCenter 2 Leaf2
  Arista vEOS-Lab (freely available)
  Attachment points:
    Host6 (tenant RED)
    Host8 (tenant GREEN)
  runs BGP (eBGP underlay, eBGP Overlay)


