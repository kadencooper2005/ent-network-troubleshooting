
Security Issues

Problem: Port security is blocking legitimate devices.
Devices to Check:

  Access Switches (ASW) → Verify port security settings.

Diagnostic Steps & Fixes

  Check security violations (on the affected switch)

    show port-security interface <INTERFACE>
  <img width="647" alt="image" src="https://github.com/user-attachments/assets/232a2315-a2a4-4e78-b183-e041b927f062" />

  At first the port was err-disabled due to the port blocking the device. Disable port-security for testing, this will remove all security settings on that port
  If the interface was shut down due to security violations, bring it back up 
  

    interface f0/1
    shutdown
    no shutdown
  <img width="724" alt="image" src="https://github.com/user-attachments/assets/eef34c1e-5a77-4d45-a2f5-48e7c5f73e56" />


  To avoid future issues, configure port security to allow up to two MAC addresses and restrict violations:
  
    interface f0/1
    switchport port-security
    switchport port-security maximum 2
    switchport port-security mac-address sticky
    switchport port-security violation restrict

  After making changes, confirm that port security is no longer blocking the device by running:

    show port-security interface f0/1
  <img width="547" alt="image" src="https://github.com/user-attachments/assets/04ce1d6c-dd68-45af-a23b-acf6191b2253" />


Remove blocked MAC address

    clear port-security sticky interface <INTERFACE>

<img width="521" alt="image" src="https://github.com/user-attachments/assets/40394c66-ac87-4634-985a-6c3ab71d3b74" />

Send traffic from a host through the switch to receive a sticky mac address and reset the restrict count back to 0 



<img width="541" alt="image" src="https://github.com/user-attachments/assets/d8abc758-9d2d-4e9a-8d2f-ac188d46b745" />


  
