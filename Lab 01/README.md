I built a full network topology from scratch and it really tested my problem solving mindset on a higher level than guided labs. 

What I did:

1. I took 10 end hosts, two routers, 2 switches, 1 multilayer switch and 4 VLANs.

2. I created all the subnets and allotted IPv4 addresses to devices.

3. Introduced VLAN10 traffic as untagged and used native vlan concept for it.

4. The traffic of the other VLANs was 802.1Q tagged.

5. SW1 and SW2 had access ports to the end hosts, and were connected with trunk ports to each other.

6. SW2 is then connected to R1 and Router on a stick (ROAS) concept is used.

7. From R1 to R2, static routing was applied. Same for R2 and SW3, as SW3 behaved as a layer 3 device (multilayer switch).

8. SW3 used Inter-VLAN routing for VLAN20 and VLAN30. R2 was the default route for it if the end hosts want to ping a device in VLAN10 or VLAN40.

9. Mistake:

I forgot to create each VLAN on each router (to make it available in the management domain). It is necessary, cause forwarding traffic to a different VLAN requires its details on the Swtiches.

10. Problem occured:

I observed a 50% packet loss on VLAN20 and VLAN30.

11. Troubleshooting:

Simulation mode is the real saviour. I tracked the defaulter. It was the problem with ip route. On SW3, due to a previous configuration, IP address 192.168.1.8/29 was assigned both the interface f0/1 (when switchport is enabled on multilayer switch) and VLAN20 (when no switchport command is enabled, the interface behaves as a routed port and VLANs are part of Serial Virtual Interfaces).

And to my surprise, the <shutdown> and <no shutdown> command on the interface f0/1 worked. 

12. The lab worked successfully. Each VLAN is able to ping another.

13. Kindly review the attached PDF for detailed documentation of commands, pings and network topology. 

