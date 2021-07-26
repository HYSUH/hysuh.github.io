---
layout: post
title: "Wireshark"
author: YS
tags: Networking
---

One of the courses I enjoyed the most during my computer science engineering degree (2001-2005) was computer networking. This was when I learnt the OSI and tcp layers models and was first introduced to the various networking protocols. I wasnt aware of [wireshark](https://www.wireshark.org/) which is an amazing packet analyzer tool that would have made learning and understanding the various networking protocols and concepts much easier. For example we could use the cli tool [tcpdump] (https://www.tcpdump.org/) to capture https traffic on port 443 and then open the file created using wireshark for further analysis to learn more about the https protocol as shown below:

1. The following command captures traffic on port 443 on all interfaces and saves the packet capture in a file called packetcapture.pcap
```
 sudo tcpdump -X -s0 port 443 -i all -w packetcapture.pcap
 ```

2. We can then open the file using wireshark

``` 
 wireshark packetcapture.pcap 
```
3. The next step is to find the SSL handshake you want to analyze. The very first step in the SSL handshake is the `Client Hello`. We can use the filter `tls.handshake.type==1` to filter out all the client hellos

![Client hello]({{ site.url }}/assets/clienthello.png)

4. We can then select one of the filtered client hello, right click and select "Follow TLS Stream" to view the entire SSL handshake and encypted communication.

![follow ssl stream]({{ site.url }}/assets/followsslstream.png)

5. If we want to analyze the tcp three way handshake instead(SYN, SYN-ACK, ACK), we can right click and select "Follow TCP Stream". 

6. We can easy add filters by choosing what we want to filter on. In the below example we can select a packet select the SYN flag and then we can choose to filter based on this value.
![follow ssl stream]({{ site.url }}/assets/addfilter.png)
This technique is really useful to debug issues with connections. For example when we had issues reported of connections dropping, a packet capture revealed that there was a device in the  network that was sending a RST packet which was terminating the tcp connections. Filtering the RST packets using the technique mentioned above helped us figure out and diagnose the issue very quickly.