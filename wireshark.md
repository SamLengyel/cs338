# Getting started with Wireshark
Sam Lengyel

## DAYTIME
1. TCP Handshake Frames:
```
1	10.150.255.57	132.163.96.1	TCP	38570 → 13 [SYN] Seq=0 Win=32160 Len=0 MSS=1340 SACK_PERM TSval=2847968711 TSecr=0 WS=128
2	132.163.96.1	10.150.255.57	TCP	13 → 38570 [SYN, ACK] Seq=0 Ack=1 Win=65535 Len=0 MSS=1340 WS=64 SACK_PERM TSval=3993172954 TSecr=28479687113	
3   10.150.255.57	132.163.96.1	TCP	38570 → 13 [ACK] Seq=1 Ack=1 Win=32256 Len=0 TSval=2847968752 TSecr=3993172954
```
2. The client uses port 38570 for this interaction.
3. The client needs a port to have a specific location to receive the network communication on and to allow multiple different connections at once, rather than just using the one IP address.
4. Frame 4 - the data in the packet window of Wireshark agrees:

```
4	132.163.96.1	10.150.255.57	DAYTIME	DAYTIME Response
```

5. [SYN] means Synchronize, [SYN, ACK] means Synchronize-Acknowledge, and [ACK] means acknowledge. The client sends a synchronize request to the server, the server confirms that it received the synchronize request, and then the client acknowledges the response of the server.
6. The daytime server initiated the closing of the TCP connection because Frame 6, the first frame with [FIN, ACK] has a source IP of 13.163.96.1 and a source port of 13, which are both the source IP and port of the daytime server.

`6	132.163.96.1	10.150.255.57	TCP	13 → 38570 [FIN, ACK] Seq=52 Ack=1 Win=65664 Len=0 TSval=3993172995 TSecr=2847968752`

## HTTP
1. 3 TCP connections were opened; there are three cases of [SYN] followed by [SYN, ACK].

```
1	10.150.255.57	172.233.221.124	TCP	33788 → 80 [SYN] Seq=0 Win=32160 Len=0 MSS=1340 SACK_PERM TSval=651045119 TSecr=0 WS=128
2	172.233.221.124	10.150.255.57	TCP	80 → 33788 [SYN, ACK] Seq=0 Ack=1 Win=65160 Len=0 MSS=1340 SACK_PERM TSval=51553899 TSecr=651045119 WS=128
9	10.150.255.57	172.233.221.124	TCP	33792 → 80 [SYN] Seq=0 Win=32160 Len=0 MSS=1340 SACK_PERM TSval=651045281 TSecr=0 WS=128
22	172.233.221.124	10.150.255.57	TCP	80 → 33792 [SYN, ACK] Seq=0 Ack=1 Win=65160 Len=0 MSS=1340 SACK_PERM TSval=51554061 TSecr=651045281 WS=128
358	10.150.255.57	172.233.221.124	TCP	33804 → 80 [SYN] Seq=0 Win=32160 Len=0 MSS=1340 SACK_PERM TSval=651045482 TSecr=0 WS=128
382	172.233.221.124	10.150.255.57	TCP	80 → 33804 [SYN, ACK] Seq=0 Ack=1 Win=65160 Len=0 MSS=1340 SACK_PERM TSval=51554263 TSecr=651045482 WS=128
```

2. Yes; Frame 4 is a HTTP GET request for index.html.

```
4	10.150.255.57	172.233.221.124	HTTP	GET /index.html HTTP/1.1
```

3. Yes; Frame 8 is a HTTP GET request for jeff-square-colorado.jpg.
```
8	10.150.255.57	172.233.221.124	HTTP	GET /jeff-square-colorado.jpg HTTP/1.1
```


## Questions 
- Which aspects of a connection are encrypted with HTTPS? Just the packets themeselves, or the metadata too?
- Is there any way to interpret the data sent in the [SYN], [SYN, ACK], and [ACK] and if you know some of it, is it usable in some way?
- Wireshark also has a packet length column for the data - is that useful at all when analyzing data sent back and forth?
- Is there a way to view non-text data in a readable format from the GET requests, for example? Does Wireshark have a way to display packets/pages that aren't just pure HTML?
- How would a Tor connection appear to Wireshark? Which IP address would it see, the final one, the guard node, all of the above? Is a Tor connection just like a multi-hop VPN in this respect?
- How can the other parts of the info be interpreted? Is there documentation available somewhere for what each part means? Stuff like [PSH] is mostly interpretable, but there are still mysterious parts of the output like TSval, TSecr, WS? Why does the TCP connection include window scaling? Is this the reason for letterboxing and other anonymizing options? 
- What are some useful filters to apply in Wireshark to narrow down output, especially when sites send **so** many requests that it's hard to tell which is which?
