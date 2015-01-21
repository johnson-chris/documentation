<B>Identify challenges within a physical network interface</B>

Physical networks are rigid, complex and often vendor specific. Network provisioning is often slow and workload placement and mobility is limited by physical topology and manual provisioning. Dynamic virtual environments get tied to inflexible dedicated hardware.

Workload placement and mobility is limited, Network Provisioning is slow, VLAN sprawl, Firewall rule sprawl, choke points, Security blind spots and Increased complexity


<B>Explain common VMware NSX terms</B>

Logical Switching - Reproduce the complete L2 and L3 switching functionality in a virtual environment decoupled from underlaying hardware.

NSX Gateway - L2 gateway for seamless connection to physical workloads and legacy VLAN’s

Logical Routing - Routing between logical switches, providing dynamic routing within different virtual networks.

Logical Firewall - Distributed firewall, kernel enabled line rate performance, virtualization and identity aware with activity monitoring. 

Logical Load Balancer - Full featured load balancer with SSL term

Logical VPN - Site-toSite & Remote Access VPN in software

NSX API - RESTful API for integration into any cloud management platform

NSX Edge - A virtual appliance that offers L2, L3, perimeter firewall, load-balancing and other services such as SSL VPN, DHCP

NSX vSwitch - (VDS or OVS-based) Support for overlay networking protocols VXLAN, STT and GRE, L2 overlay over existing IP networks, EW-NS for tenant isolation, facilities massive scale hypervisors, Port Mirroring, Netflow/IPFIX, cfg backups, Network Health Checks, QoS, and LACP

Consumption Layer - Driving via the NSX manager UI In a vSphere environment this is available via VSphere WebUI. Out of box support for vCloud Automation Center (VCAC), vCloud Director and OpenStack Neutron plugin for NSX.

Management Plane - NSX Manager Single point of configuration and REST API entry points 

Control Plane - NSX Controller - In a vSphere environment with VDS this enables multicast free VXLAN, control plane programming elements such as VDR. Any control plane failures do not impact data plane traffic


<B>Describe and differentiate functions and services performed by VMware NSX</B> 

Logical Layer 2 - Enabling extension of a L2 segment / IP Subnet anywhere in the fabric irrespective of the physical network design

Distributed L3 Routing - Routing between IP subnets handled in a logical space without traffic going out to the physical router, preformed in the HV kernel with minimal CPU/Mem overhead. NSX Edge provides vehicle to do full dynamic route peering with OSPF, BGP and IS-IS on the physical network.

Distributed Firewall - Security enforcement done in kernel and VNIC itself. Allowing for highly scalable firewall rule enforcement in a highly scalable manner without creating bottlenecks and can perform at line-rate.

Logical Load-balancing - Support L4-L7 with SSL termination

SSL VPN -enable L2 VPN services 


<B>Describe common use cases for VMware NSX</B> 

Network Automation and Configuration allowing for self service and rapid application deployments 

Streamlines ongoing administration, monitoring and troubleshooting adding increased network visability

Requires fewer switch-ports and less networking appliancies

Data Center defragmentation allowing for higher utilization of data center resources 

Support for tenants along with dev,test prod on the same physical infrastructure