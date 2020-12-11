# packetcap
Lightweight Packet Capture with filtering option 

PacketCap allows microsecond packets in Layer 2, 3 and 4 to be dump to terminal, operates in promiscuous mode to capture packet length up to 1600 bytes. Supports filtering option to look at specific packets. The filtering syntax is implemented using <a href="https://linux.die.net/man/7/pcap-filter"> Linux pcap-filter </a>. PacketCap is lightweight and useful when wireshark or tcpdump is not available. Implemented using <a href="https://github.com/google/gopacket/blob/master/pcap/pcap_unix.go"> gopacket </a> that does the heavy lifting.


Usage: pcap [options...] [device]
Options: 
  -d list all available network devices on machine
  -f pcap filter string to be used
  -h help menu
  
  device - the local device or interface to enable packet capture
  


## To filter ICMP traffic
sudo ./pcapfilter -f "icmp" en0

## To filter DNS traffic (udp53 and tcp53)
sudo ./pcapfilter -f "ip and udp port 53 or tcp port 53" en0

## To filter telnet traffic
sudo ./pcapfilter -f "ip and port telnet" en0

## To filter all traffic
sudo ./pcapfilter en0

