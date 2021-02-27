# SDN
Software Defined Networking and POX programming

servers = array of IPAddr(ip of each server)
ip = IPAddr object of LB ip addres

proto.arp_responder - util to learn and proxy ARPs
Objects/Classes providing API register on core, and then can be called with that name by others.
core.registerNew(iplb, event.connection, IPAddr(ip), servers)
# this registers iplb class, and passes the following 3 as parameters to class constructor.
LB remembers dpid of first switch to connect, and then provides LB on only that in future events, ignoring other switches. Attaches event listeners on the iplb object. Done.
do_expire :: to expire probes and memorized flows
do_probe :: sends an ARP to a server to see if it still alive
get a server to ping from `servers` list
make a new arp type ethernet packet by setting all required attributes. 	
add a timeout to the probe, store in dict of ip->timeout in `outstanding_probes`
https://openflow.stanford.edu/display/ONL/POX+Wiki#POXWiki-proto.arp_responder

Learning Switch Application
The learning switch learns the source mac address and the port of hosts from the packets it receive. Following is a naive algorithm for simple learning switch application:
if (source mac address is new)
    record the source mac and input port mapping
if (destination mac address is known)
    install a flow table rule
    forward the packet to the destination
else
    FLOOD the packet

To Learn about the POX Programming refer to Pox Programming for project pdf file.
