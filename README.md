# Design-and-Implementation-of-a-Simple-Networking-Project-1
### Project #1: Design and Implementation of a Simple Networking Project

#### Case Study and Requirements

1. **Network Design**: 
   - Connect ACCOUNTS and DELIVERY departments.
   - Each department should contain at least two PCs.
   - Appropriate number of switches and routers should be used.
   - Use network 192.168.40.0.
   - Configure all interfaces with correct IP addresses, subnet mask, and gateways.
   - Connect all devices using appropriate cables.
   - Test communication between devices in both departments.

#### Technologies Implemented

1. **Creating a Simple Network using a Router and Access Layer Switch**:
   - Use one router to connect two departments.
   - Use one switch per department to connect the PCs.

2. **Connecting Networking Devices with Correct Cabling**:
   - Use straight-through cables to connect PCs to switches.
   - Use a cross-over cable or straight-through cable (if supported by the router) to connect switches to the router.

3. **Connecting Two Networks using a Router**:
   - Router interfaces will serve as gateways for the two networks (departments).
   - The router will handle traffic between the ACCOUNTS and DELIVERY networks.

4. **Subnetting and IP Addressing**:
   - The given network 192.168.40.0/24 can be divided into two subnets:
     - ACCOUNTS: 192.168.40.0/25
     - DELIVERY: 192.168.40.128/25

5. **Assigning IP Addresses to Router's Interfaces**:
   - Router interface for ACCOUNTS: 192.168.40.1/25
   - Router interface for DELIVERY: 192.168.40.129/25

6. **Static IP Address Allocation to Host Devices**:
   - ACCOUNTS:
     - PC1: 192.168.40.2/25, Gateway: 192.168.40.1
     - PC2: 192.168.40.3/25, Gateway: 192.168.40.1
   - DELIVERY:
     - PC1: 192.168.40.130/25, Gateway: 192.168.40.129
     - PC2: 192.168.40.131/25, Gateway: 192.168.40.129

7. **Test and Verifying Network Communication**:
   - Use the ping command to test connectivity between PCs in both departments.
   - Verify that devices can communicate across the router.

#### Detailed Pointwise Implementation

1. **Setting Up the Devices**:
   - Drag and drop the required devices in Cisco Packet Tracer: one router, two switches, and four PCs.
   
2. **Connecting the Devices**:
   - Use straight-through cables to connect each PC to its respective switch.
   - Use a cross-over cable or straight-through cable (if the router supports it) to connect each switch to the router.

3. **Configuring Router Interfaces**:
   - Open the CLI for the router.
   - Enter global configuration mode:
     ```bash
     Router> enable
     Router# configure terminal
     ```
   - Configure the interface for the ACCOUNTS network:
     ```bash
     Router(config)# interface gigabitEthernet 0/0
     Router(config-if)# ip address 192.168.40.1 255.255.255.128
     Router(config-if)# no shutdown
     ```
   - Configure the interface for the DELIVERY network:
     ```bash
     Router(config)# interface gigabitEthernet 0/1
     Router(config-if)# ip address 192.168.40.129 255.255.255.128
     Router(config-if)# no shutdown
     ```

4. **Configuring Switches and PCs**:
   - No specific configuration is needed for switches apart from the default settings.
   - Configure IP addresses for each PC:
     - For ACCOUNTS:
       - PC1: IP: 192.168.40.2, Subnet Mask: 255.255.255.128, Gateway: 192.168.40.1
       - PC2: IP: 192.168.40.3, Subnet Mask: 255.255.255.128, Gateway: 192.168.40.1
     - For DELIVERY:
       - PC1: IP: 192.168.40.130, Subnet Mask: 255.255.255.128, Gateway: 192.168.40.129
       - PC2: IP: 192.168.40.131, Subnet Mask: 255.255.255.128, Gateway: 192.168.40.129

5. **Testing Network Communication**:
   - Use the ping command to test connectivity:
     - From PC1 in ACCOUNTS, ping PC2 in ACCOUNTS.
     - From PC1 in DELIVERY, ping PC2 in DELIVERY.
     - From PC1 in ACCOUNTS, ping PC1 in DELIVERY to verify cross-network communication.

By following these steps, you will have a functional network connecting the ACCOUNTS and DELIVERY departments, enabling communication within and between the departments.
