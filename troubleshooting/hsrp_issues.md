HSRP Issues

Problem: HSRP failover is not working, or the standby router is not taking over.
Devices to Check:

Distribution Switches (DSW) → Ensure HSRP settings match on both devices.

Diagnostic Steps & Fixes

  Check HSRP status (on both primary and standby switches)

    show standby brief
<img width="742" alt="image" src="https://github.com/user-attachments/assets/6d2eedc8-dd33-4eca-ad51-3f55ea4be813" />
This Layer 3 switch is running HSRP for gateway redundancy across multiple VLANs. It is Active for VLANs 10 and 99 and Standby for VLANs 20 and 30, indicating load balancing with another switch. Preempt is enabled for VLANs 10 and 99, allowing this switch to reclaim the Active role if it recovers from failure. This setup ensures seamless failover and high availability. If preempt is not enabled and the switch goes down, it will not reclaim the Active role.


Verify priority settings (on the primary switch)

    show running-config | include standby

<img width="474" alt="image" src="https://github.com/user-attachments/assets/75c9c3c1-0e64-4dc5-92a1-89263d2c7dc3" />
The standby priority indicates which switch will be Active or Standby. Having a priority over 100 will set the switch as the Active switch, In this case I set the priority to 105 for groups 1 and 2 (VLAN 20, VLAN 99)

    

  Adjust priority if needed:

    interface vlan <VLAN_ID>
    standby <GROUP_ID> priority 110

Check preempt settings (on the standby switch)

    show standby
<img width="831" alt="image" src="https://github.com/user-attachments/assets/447e2edb-f26f-4d33-ae8c-0b7b9389a54e" />
You can use show standby brief to print a summary of HSRP including Active and Standby groups, what VLAN they are in, group number etc.


  If missing, enable:

    interface vlan <VLAN_ID>
    standby <GROUP_ID> preempt
I have enabled preempt in groups 1 and 2 so they can reclaim their positions as Active switches when recovered from failure.


