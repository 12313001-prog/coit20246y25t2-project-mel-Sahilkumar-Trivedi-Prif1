# 4.1.1 Network Design

This is the section that describes the final network layout based on the Truelec head office and the Brisbane branch. The design will form the basis for assurance on the optimality with regard to the required performance, security, scalability and redundancy as well as ensuring the operational requirements of the company.


| [Assumptions](#Assumptions) | [Network Architecture](#Network-Architecture) | [WiFi Design](#WiFi-Design) | [Address Allocations](#Addressing-Requirements) | [Recommended Equipment](#Recommended-Equipment) | [Plan](./Plan.md) | [Cloud Services](./cloud.md) | [Security](./security.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

## Assumptions

The main central office of the design will be Brisbane, but secondary offices will be set up in Sydney, Brisbane and Perth.


- **Headquarters Location**: The headquarters is based in Melbourne, Australia, where most of the administrative and technical support functions are based.

- **Branch Office Locations**: The central branch office in the design will be Brisbane, but branch offices will be located in Sydney, Brisbane and Perth.

- **Head Office Personnel**: The headquarters also maintains representatives including project management and information technology managers, human resource/payroll managers, and senior management personnel from all the divisions.

- **Branch Office Workforce**: Brisbane office - Approximately 25 employees, including travel advisors, office assistants and administrative staff.

The assumptions are defined as the decision criteria for bandwidth estimates, equipment sizes, wireless coverage and scaling decisions.

## Logical Network Design and Justification

The Brisbane office and HQ is a scaleable, reliable and secure network. The design has the following key components:

## Network Architecture

**Star Topology**: The Brisbane branch office and Melbourne headquarters are both connected in a star topology. In this type of architecture, all devices are isolated from each other through a central device or switch, and the system is pure. This star topology also provides flexibility and allows you to easily extend the network or add additional devices. (Berto, Napoletano and Savi, 2021).


**Headquarters Network**:
 - The network at the headquarters will consist of core switches connected to the distribution devices in this case in every floor. These distribution devices will, in their turn, be tied up to access switches so that the data flow between devices and particular network segments is seamlessly guaranteed.

 - The perimeter routers and firewalls will notice the traffic between internal network and the Internet hence, establishing security barriers at the network boundaries.

 - Sharing and dulled infrastructure can be located on a demilitarized zone (DMZ) so as to separate external-to-the-network servers with those of the inner net, and this offers the drive of an extra security measure.

**Branch Office Network (Brisbane)**:

 - The Brisbane branch office premise will have a simplified network design that has a single edge router, firewall, two access switches, a core switch. The Brisbane site will be connected to headquarters by secure VPN tunnels and will compose of free flowing communication between the two locations.  

 - Virtual Private Network (VPN) connection will ensure that data are securely transmitted and help protect sensitive company data when accessing information remotely or across sites.  

![Network Design Diagram](images/Network-Design.png)

## Subnetting Strategy:

To facilitate management of the network, and separation of inter-department traffic a detailed subnetting scheme will be implemented at every location. One would create distinct sub nets that are assigned to each of the departments and network segments to enhance performance and proper traffic routing.  


## WiFi Design

**WiFi Infrastructure**:

 - Wi-Fi infrastructure at the level of enterprise structure will be implemented at the headquarters as well as the Brisbane office of the branch; and access points (APs) will be placed strategically in order to cover the maximum area.  

 - APs will be mounted on a ceiling per floor and an identical arrangement will be repeated at the Brisbane office.  

**Frequency Bands**:

 - The wireless network will support the 2.4GHz and 5GHz frequency bands which will be exceeded provisionally to a third frequency band to increase capacity. The use of these bands will improve the work of devices, decrease garbage, and guarantee the high-speed connection   (Nguyen and Cheema, 2021).

**Capacity and Performance**:

 - The APs each have a capacity of serving to 250 simultaneous users hence making the network scalable to future expansions.  

 - The authentication of the staff devices will be done using WPA3 Enterprise; at the same time, the guests networks are going to be segregated with the assistance of WPA2 Personal Set (PSK) encryption.  

**SSID Configuration**:

 - TravelAgency-Staff: In order to achieve the high power of security provisions, the staff network will use WPA3 Enterprise with RADIUS authentication.  

 - TravelAgency-Guest: WPA2 PSK will segregate guest access to the corporate network, and will be allowed only to limited access to secure corporate resources.  

 - TravelAgency-IoT: Internet-of-Things (IoT) gadgets, such as sensors and security cameras, will be put on a special VLAN to enhance protection and avoid affecting the other network traffic (Alamleh et al., 2025).

 ![WiFi Design](images/Wifi-Architecture.png)  

**Additional WiFi Settings**:

 - The automatic channel selection will be enabled to reduce the influence of the interference and the optimal use of the channels.  

 - Band steering will be utilized in the channeling of devices to the most appropriate frequency of band that is agreed to their capacities.  

 - The established minimum signal threshold will be -67 dBm to ensure a good connection within all the premises.  

 - Our wireless network will also accommodate 802.11r,802.11k, and 802.11v so that users can enjoy high speed bagging among the APs when moving around the office premises.

## Addressing Requirements

- In this section IP addresses is taken from th student ID number i.e last two digit number of their ID and these number are placed firs octet of each subnet.

- **Student IDs**: 
    - Sahilkumar Bharatbhai Patel - 12313001, Trivedi Alig Jayeshkumar - 12310588

- **Addressing Rule**: 
The last two digit number of ID is used in first octet of IP addresses.


- **Subnet Mask**: Each and every subnet use a/24 subnet mask to configured a devices because is give 254 different IP address which used as host address

IP table according to devices present in headquarter and Brisbane:

| IP Range      | Purpose                                   |
| ------------- | ------------------------------------------|
| 88.10.0.0/24  | HQ Staff LAN(VLAN 10)                     |
| 88.20.0.0/24  | HQ Guest WiFi (VLAN 20)                   |
| 88.30.0.0/24  | HQ IoT WiFi(VLAN 30)                      |
| 88.99.0.0/24  | HQ Management(VLAN 99)                    |
| 88.110.0.0/24 | Brisbane Staff LAN(VLAN 110)              |
| 88.120.0.0/24 | Brisbane Guest WiFi(VLAN 120)             |
| 88.130.0.0/24 | Brisbane IoT WiFi(VLAN 130)               |
| 88.199.0.0/24 | Brisbane Management (VLAN 199)            |



## Recommended Equipment

The following equipment is recomended based on thier performance, security measures, and thier cost effectiveness:




| Component            | Model / Specs                                       | Estimated Cost (AUD) | Notes                              |
| -------------------- | --------------------------------------------------- | -------------------- | ---------------------------------- |
| **Firewall (HQ)**    | Fortinet FortiGate 80F, 10x GE, IPS/IDS, VPN        | \~\$2,100            | Enterprise-grade security device   |
| **Access Point**     | Ubiquiti UniFi 6 Long-Range, WiFi 6, 300 clients    | \~\$400              | Dual-band, high performance        |
| **Core Switch (HQ)** | Cisco CBS250-48T-4G, 48 Gigabit + 4 SFP             | \~\$950              | Core/distribution switch           |
| **Branch Router**    | TP-Link ER7206, Gigabit WAN, VPN, Load Balancing    | \~\$280              | Edge router for remote office      |
| **Server (HQ)**      | Dell PowerEdge T550, Xeon Silver, 32GB RAM, 2TB HDD | \~\$4,200            | Centralized server for HQ services |


## References

Alamleh, H., Estremera, L., Arnob, S.S. and AlQahtani, A.A.S. (2025). Advanced Persistent Threats and Wireless Local Area Network Security: An In-Depth Exploration of Attack Surfaces and Mitigation Techniques. Journal of Cybersecurity and Privacy, [online] 5(2), p.27. doi:https://doi.org/10.3390/jcp5020027.

Berto, R., Napoletano, P. and Savi, M. (2021). A LoRa-Based Mesh Network for Peer-to-Peer Long-Range Communication. Sensors, [online] 21(13), p.4314. doi:https://doi.org/10.3390/s21134314.

Nguyen, C. and Cheema, A.A. (2021). A Deep Neural Network-Based Multi-Frequency Path Loss Prediction Model from 0.8 GHz to 70 GHz. Sensors, [online] 21(15), p.5100. doi:https://doi.org/10.3390/s21155100.