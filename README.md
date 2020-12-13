# packetcap
Lightweight Packet Capture with filtering option 

PacketCap allows microsecond packets in Layer 2, 3 and 4 to be dumped to terminal, operates in promiscuous mode to capture packet length up to 1600 bytes. Supports filtering option to look at specific packets. The filtering syntax is implemented using <a href="https://linux.die.net/man/7/pcap-filter"> Linux pcap-filter </a>. PacketCap is lightweight and useful when wireshark or tcpdump is not available. Implemented using <a href="https://github.com/google/gopacket"> gopacket </a> library that does the heavy lifting for BPF byte code filtering and pcap-filter string to BPF byte code.

```
Usage: pcap [options...] [device]
Options: 
  -d list all available network devices on machine
  -f pcap filter string to be used
  -w write packet filter to filename specified
  -h help menu
  
  device - the local device or interface to enable packet capture
  ```

## Example

### To filter ICMP traffic
sudo ./pcapfilter -f "icmp" en0

### To filter DNS traffic (udp53 and tcp53)
sudo ./pcapfilter -f "ip and udp port 53 or tcp port 53" en0

### To filter telnet traffic
sudo ./pcapfilter -f "ip and port telnet" en0

### To filter all traffic
sudo ./pcapfilter en0

### To save output to local pcap file
sudo ./pcapfilter -f "ip and udp port 53" -w test.pcap en0

## How to Install
1. Download the binaries from <a href="https://github.com/maxng07/packetcap/releases"> Release </a> Page.
2. For Windows
* You will need winpcap, you can download it from <a href="https://www.winpcap.org"> here </a>
* To determine the device in Windows System, you can run pcapfilter -d which lists all the devices on the machine. Then use the GUID listed and appending with `\\device\\NPF_{GUID}` as the device.

`pcapfilter -f "ip" \\device\\NPF_{GUID}`

## Changes:
Added Version 2 - allows the abillity to write packet capture output to local file. 
