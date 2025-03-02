## **Connectivity Issues**
**Problem:** Devices cannot communicate across the network.  

### **Devices to Check:**  
- **Access Switches (ASW)** → Ensure correct VLAN assignments and trunking.  
- **Distribution Switches (DSW)** → Verify routing and inter-VLAN communication.  
- **Core Switches (CSW) / Routers (R1)** → Check default routes and interface status.  

Check interface status

    show ip interface brief

If an interface is administratively down, enable it:

    interface <INTERFACE>
    no shutdown

Check if the default gateway is set

    show ip route

If missing, add it:

    ip default-gateway <GATEWAY_IP>

Check physical cable connections

    show interfaces status

Verify trunk links are properly set up

    show interfaces trunk
