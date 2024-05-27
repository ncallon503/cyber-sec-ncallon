# Homework 4 Feedback Sheet

### Student

**ODIN: <FMI>**

## Grade (<FMI>/100)

#### TryHackMe - What is Networking Room
- [] Completed

#### TryHackMe - Passive Network Recon Room
- [] Completed

#### TryHackMe - Active Network Recon Room
- [] Completed

#### TryHackMe - nmap Room
- [] Completed

#### tcpdump tasks
- [] Perform a tcpdump capture where you only capture DNS packets
- [] Perform a tcpdump capture where you capture TCP packets that are destined for either port 443 or 8080, and originate from your computer.
- [] Perform a tcpdump capture where traffic is either UDP or TCP, is inbound to your computer, and destined for a port between 20000 and 35000.

#### Packet Analysis Tasks
##### Part One
- [] Find Statistics on TCP and UDP Services Most interesting user protocols run on TCP although a few run on UDP.
- [] Extend your script’s statistics gathering to count the use of all well-known destination port numbers for TCP and UDP (ports 1-1024)
- [] Based on this information, characterize the main functions on each network. What kind of network is it? (e.g., work, home, data center, ISP)
- [] Add to your script an option called --countip which creates list of distinct IP addresses with their usage counts. Sort the list by the usage count, not by the IP address.
- [] Run your countip script on R and O data. Does this inform your answer in [2]?
- [] Attempt to determine the network number (network prefix) that seems to dominate the traffic.
- [] Generate sorted output from --countip for the IP protocols to identify all the IP addresses that use GRE, IPSEC, OSPF
- [] Find another network prefix that also seems to be associated with this traffic.
- [] Does the OSPF information inform your answer to question 2 above?
##### Part Two
- [] Add an option to your script --connto, which counts the number of packets sent to each service (ports 1-1024) on the network.
- [] Sort the output by the number of distinct source IP address – source port combinations, so that servers which serve a lot of different connections all cluster at one end of the output.
- [] For output, generate a summary line that shows, for each destination IP address, how many distinct source IP addresses accessed it, and what ports were referenced





## Comments

<FMI>