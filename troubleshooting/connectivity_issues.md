## **Connectivity Issues**
**Problem:** Devices cannot communicate across the network.  

### **Devices to Check:**  
- **Access Switches (ASW)** → Ensure correct VLAN assignments and trunking.  
- **Distribution Switches (DSW)** → Verify routing and inter-VLAN communication.  
- **Core Switches (CSW) / Routers (R1)** → Check default routes and interface status.  

Check interface status

    show ip interface brief
<img width="646" alt="image" src="https://github.com/user-attachments/assets/6320bb1c-b8c5-4fba-840a-b23b93dc775d" />
As we can see, the f0/1 interface is administratively down down. Switch interfaces are by defualt up/up but to demonstrate a connectivity issue I used int f0/1, then shutdown to put it in a down state




If an interface is administratively down, enable it:

    interface <INTERFACE>
    no shutdown
<img width="647" alt="image" src="https://github.com/user-attachments/assets/93f585b7-0711-4637-9459-a0105e4a247b" />
the down interface was f0/1 like mentioned aboved, so by enabling it, you're allowing traffic to pass to and from this interface

Check if the default gateway is set

    show ip route
You can only use show ip route on layer 3 switches and routers, so I will be showing a screen shot from a multilayer-switch (DSW-A2).
<img width="751" alt="image" src="https://github.com/user-attachments/assets/66b4a25a-8d45-4fb1-8024-4b95166db56d" />


If missing, add it:

    ip default-gateway <GATEWAY_IP>

Check physical cable connections

    show interfaces status
<img width="719" alt="image" src="https://github.com/user-attachments/assets/f232a401-79f4-49d7-829f-db14a48c131b" />
As you can see, we have the appropriate interfaces in the "connected state" as trunk ports verifying them as connected trunk ports.


Verify trunk links are properly set up

    show interfaces trunk
<img width="729" alt="image" src="https://github.com/user-attachments/assets/e220ef16-1580-4107-a09d-caec0c9fc26c" />
Using this command, you can comfirm that trunk links are properly setup and are in the status "trunking" with the appropriate encapsulation type of dot1q.

