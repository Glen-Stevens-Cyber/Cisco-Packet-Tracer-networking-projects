# Packet Tracer Skills Integration Challenge

## Project overview
This is a Cisco Packet Tracer activity which was assigned to me during my studies at the Open University and was completed during my second year. This project tested a variety of networking skills I was taught but specifically focused on designing a dual-stack network for three subnets and one subnet to be integrated in the future when designing a VLSM addressing scheme for that network.
## Project Scenario: 
The router Central, ISP cluster, and the Web server are completely configured. You must create a new IPv4 addressing scheme that will accommodate 4 subnets using the 192.168.0.0/24 network. The IT department requires 25 hosts. The Sales department needs 50 hosts. The subnet for the rest of the staff requires 100 hosts. A Guest subnet will be added in the future to accommodate 25 hosts. You must also finish the basic security settings and interface configurations on R1. Then, you will configure the SVI interface and basic security settings on switches S1, S2, and S3.
## Project requirements:
	Subnet the 192.168.0.0/24 network using VLSM and provide sufficient IPv4 addresses for: 
	100 Staff hosts 
	50 Sales hosts 
	25 IT hosts 
	25 future Guest hosts 
	Configure SSH on R1 with the following requirements:
	Set the domain name to CCNA-lab.com
	Generate a 1024-bit RSA key.
	Configure the VTY lines for SSH access.
	Use the local user profiles for authentication.
	Create a user Admin1 with a privilege level of 15 and use an encrypted password value specified by the university which I can’t disclose publicly
	Assign IPv4 addresses, subnet masks and default gateways to the departmental workstations. 
	Configure IPv6 global unicast addresses, link-local addresses and default gateways. 
	Configure and enable R1’s Gigabit Ethernet interfaces. 
	Configure management SVIs and default gateways on switches S1, S2 and S3. 
	Apply basic security settings to the router and switches. 
	Enforce a minimum password length and encrypt stored plaintext passwords. 
	Configure an unauthorised-access warning banner on R1.
	Block login attempts temporarily following repeated authentication failures. 
	Configure five-minute inactivity timeouts on console and VTY lines. 
	Verify communication between the internal and external devices. 
	Confirm access to IPv4 and IPv6 web services using DNS names.

## Network Topology: 
Image: ‘Network Topology.png’ 
This image contains a screenshot of the completed topology containing the three departmental networks connected through its own switch to R1. R1 was connected through the supplied Central and ISP infrastructure to external DNS and web services.

## VLSM addressing scheme for 192.168.0.0/24
Image: ‘VLSM Addressing Scheme.png’
Inside of the repository there will be a VLSM addressing scheme table I used to divide the departments to ensure there were sufficient IP addresses for each department. 
When calculating how many host bits were required for ensuring there were enough usable IP addresses for each subnet, I used the formula 2^h-2. H would represent the amount of host bits I’d have remaining from the host portion because the rest would be added to the network prefix. The – 2 also takes into consideration that the network and broadcast addresses are reserved and cannot be assigned.
For example, the Staff subnet requires 100 hosts, and we currently have a prefix of /24 which are the network bits and eight bits remaining for the host addresses. I used my formula 2^7-2 to give me 126 usable host addresses. In conclusion, I borrowed one host bit, so I was left with a network prefix of /25.
The Guest subnet will be added in the future in the project scenario, but the subnet’s details are also filled out for when it’s ready to be added to the network.
## Dual-Stack Configuration: 
Image: ‘Dual Stack Configuration.png’
Following on from the previous section, the screenshot shows that the Staff, Sales and IT workstations were configured with the following:
	IPv4 addresses and subnet masks. 
	IPv4 default gateways. 
	IPv6 global unicast addresses. 
	IPv6 link-local addresses. 
	IPv6 default gateways.

The screenshot also highlights the implementation of my IPv4 VLSM addressing scheme and all required interfaces are in an up/up state confirming the physical connection and line protocols are operational.

## Router and Switch Security Configuration: 
Image: ‘R1 Security Configuration.png’
This image highlights the security configurations implemented on R1 to meet the activity’s requirements.
The configurations in the image include: 
	Password encryption. 
	A minimum password length of ten characters. 
	A Hostname matching the addressing table
	An encrypted privileged EXEC password. 
	Local user authentication. 
	Login blocking after four failed attempts within 120 seconds. 
	A 180-second blocking period. 
	An unauthorised-access warning banner. 
	Five-minute console and VTY inactivity timeouts. 
	SSH-only remote access. 
	DNS lookup disabled. 
	A domain name for SSH configuration. 
I also configured device names, password protection, management interfaces, default gateways and inactivity timeouts on switches S1, S2 and S3.
Credential values and password hashes have been excluded from the image but are still available in the Packet Tracer activity.
## SSH configuration and testing:
Image: ‘Successful SSH Connection.png’
This screenshot highlights the successful implementation of SSH on R1. The Staff subnet was able to successfully reach a different interface located in a different subnet also highlighting that the subnets are able to communicate with each other and verifies the successful SSH connection through using the show ip ssh command.
The activity required me to implement:
	Set the domain name to CCNA-lab.com
	Generate a 1024-bit RSA key as specified by the activity
	Configure the VTY lines for SSH access.
	Use the local user profiles for authentication.
	Create a user Admin1 with a privilege level of 15 and a specific encrypted password.

## Dual-Stack connectivity verification:
Image: ‘Dual Stack Website Access.png’
This screenshot proves that the departments are able to communicate outside of their subnet and reach both the IPv4 and the IPv6 websites www.cisco.srv and www.cisco6.srv.
These tests also demonstrated that the following components were operating together successfully:
	Workstation addressing. 
	Default gateways. 
	IPv4 and IPv6 routing. 
	DNS name resolution. 
	External server connectivity. 
	Web services.

## Detailed assessment feedback:
Image: ‘Assessment Results.png’
This screenshot shows the feedback received upon completion of the activity and shows that a score of 128/128 was achieved.
## What I learned:
This was a really useful activity at the end of my second year of studying Cisco and networking materials because it allowed me to implement a lot of skills that I had learned throughout the year such as implementing SSH and access control measures to protect privileged EXEC and global configuration modes. 
The most valuable experience I gained through this activity was planning and implementing network segmentation to fulfil the company’s specific set of requirements. By using VLSM in this activity, I was able to create a more efficient way to utilise the company’s IP addresses and only assign what each subnet required which also prevents IP addresses from being wasted and allows for scalability later for when they implement the Guest subnet. 
This activity also allowed for me to test troubleshooting and verification skills. Each time I entered a configuration on to a router or switch, I would use verification commands such as show running-config or show ip interface brief for example to see if everything was correct. If something was failing, I’d use troubleshooting methodologies and commands like ping or traceroute to go through a step-by-step process to highlight the issue, potential causes of the issue and once found, implement the solution and verify that the issue was resolved.

## Note on this activity:
The Packet Tracer activity was not included in the repository because this was a university assignment and to prevent exposing answers or credentials. The screenshots are to verify completed configurations and verify everything is functional.

