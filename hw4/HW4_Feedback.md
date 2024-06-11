# Homework 4 Feedback Sheet

### Student

**ODIN: ncallon**

## Grade (100/100)

#### TryHackMe - What is Networking Room
- [x] Completed

#### TryHackMe - Passive Network Recon Room
- [x] Completed

#### TryHackMe - Active Network Recon Room
- [x] Completed

#### TryHackMe - nmap Room
- [x] Completed

#### tcpdump tasks
- [x] Perform a tcpdump capture where you only capture DNS packets
- [x] Perform a tcpdump capture where you capture TCP packets that are destined for either port 443 or 8080, and originate from your computer.
- [x] Perform a tcpdump capture where traffic is either UDP or TCP, is inbound to your computer, and destined for a port between 20000 and 35000.

#### Packet Analysis Tasks
##### Part One
- [x] Find Statistics on TCP and UDP Services Most interesting user protocols run on TCP although a few run on UDP.
- [x] Extend your script’s statistics gathering to count the use of all well-known destination port numbers for TCP and UDP (ports 1-1024)
- [x] Based on this information, characterize the main functions on each network. What kind of network is it? (e.g., work, home, data center, ISP)
- [x] Add to your script an option called --countip which creates list of distinct IP addresses with their usage counts. Sort the list by the usage count, not by the IP address.
- [x] Run your countip script on R and O data. Does this inform your answer in [2]?
- [x] Attempt to determine the network number (network prefix) that seems to dominate the traffic.
- [x] Generate sorted output from --countip for the IP protocols to identify all the IP addresses that use GRE, IPSEC, OSPF
- [x] Find another network prefix that also seems to be associated with this traffic.
- [x] Does the OSPF information inform your answer to question 2 above?
##### Part Two
- [x] Add an option to your script --connto, which counts the number of packets sent to each service (ports 1-1024) on the network.
- [x] Sort the output by the number of distinct source IP address – source port combinations, so that servers which serve a lot of different connections all cluster at one end of the output.
- [x] For output, generate a summary line that shows, for each destination IP address, how many distinct source IP addresses accessed it, and what ports were referenced


## Comments
Excellent work! Thank you for your thorough documentation and great analysis.


Correct tcpdump commands to get expected output:
```
sudo tcpdump -i eth0 -n -s 0 -X -tt 'port 53' -c 10

sudo tcpdump -i eth0 -n -s 0 -X -tt 'src host 172.22.71.191 and (dst port 443 or dst port 8080) and tcp' -c 10

sudo tcpdump -i eth0 -n -s 0 -X -tt '(src host 172.22.64.0 or src net 172.22.64.0/20) and (dst portrange 20000-35000) and (tcp or udp)' -c 10
```