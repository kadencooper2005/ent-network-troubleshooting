## **Connectivity Issues**
**Problem:** Devices cannot communicate across the network.  

### **Devices to Check:**  
- **Access Switches (ASW)** → Ensure correct VLAN assignments and trunking.  
- **Distribution Switches (DSW)** → Verify routing and inter-VLAN communication.  
- **Core Switches (CSW) / Routers (R1)** → Check default routes and interface status.  

Check interface status

    show ip interface brief
    <img width="678" alt="image" src="https://github.com/user-attachments/assets/e4c541e6-9234-4c62-b951-7f8f7693d940" />


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
