Problem: Devices cannot communicate across the network.
Possible Causes & Solutions:

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
