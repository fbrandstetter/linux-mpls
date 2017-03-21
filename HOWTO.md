## How To

This guide describes how to enable MPLS in Linux and use it route packets.

## Requirements

* Linux Kernel 4.1+

## Install

Firstly, we need to enable the kernel module:

    modprobe mpls_router
    
Afterwards, we have to enable MPLS in sysctl.conf:

    sudo sysctl -w net.mpls.conf.eth0.input=1 
    sudo sysctl -w net.mpls.conf.eth1.input=1 
    sudo sysctl -w net.mpls.platform_labels=10000

Next, we can add a route and route it through a label:

    ip route add 10.0.0.0/8 encap mpls 10 via inet 192.168.0.1

To verify we created the route properly, list the MPLS routes through:

    ip -f mpls route show
    
## Usage

MPLS can be used for large-network deployments using Linux routers and it can greatly reduce hassle within your network. By using MPLS, you can overlay any Layer 2 technology, for example VPLS is getting a thing when using MPLS.
