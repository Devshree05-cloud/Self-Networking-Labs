Completing the Layer 2 CCNA protocols with this final self lab.

In this lab, I observed:

1. DTP mode.

2. STP working.

And tried:

1. VTP server, client and transparent modes.

2. EtherChannel LACP.

Mistakes and Solutions:

1. VTP didn't work.

   Reason - I configured VTP modes, but not the same VTP Domain.

   I solved this problem using <vtp domain cisco> command on all three switches.

2. EtherChannel pairing was showing the P and s status for the paired interfaces, instead of P and P, which indicates both were not active EtherChannel pairs.

   Reason - I forgot to configure the newer physical link the same as the older one with which it was being paired for EtherChannel. Things like access or trunk, VLAN numbers, interfaces, native VLANs, allowed VLANs, VLANs in management domain, active VLANs, etc, all should be the same. 

   I made their VLAN database same and it worked successfully.

3. For detailed documentation with commands and screenshots, kindly review the attached PDF.
