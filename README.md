# TTL

TTL(Time To Live) and TCP Window Sizes

Hacker can know what OS in the sender or router based on the finger print. -> Time to live and TCP Window Size

Some firewall drops ICMP.
Why routers/servers disable echo replies? -> One reason: to decrease Ping, Security reason: hacker can use echo replies map the network (Ping of Death)


# Project discussion:

## Part1: Simulating Network Compression Point-to-Point Links

### Compression link:
  Compressibility and Data Entropy:
    Entropy: Measuring redundancy in data ( Repeated pattern in the data)

  Example of data with low entropy: 101010101010101010101010101010101010101010101010

  Example of data with high entropy: 11010010110111011010000110101 (No obivious pattern)

  point to point link: evey packet go through the link will be compress, and decompress in the end point

  Compression algorithm: Lengel-Ziv-Stac (stac LZ)

### Motivation: 
  Simulation Verification
  Performance: Some app do compression in application layer -> battery drain faster if you do it in the client side
  Security?: Everything has been encrypt is not easy to be compressed (HTTPS for example), to compress those data, router need to decrypt
    the packet and compress (NOKIA)

### Method:
  Send the low entropy data and send the high entropy data and compare the time

  if no compression in between, the time should be the same
  If there is a compression in between, the low entropy data should be faster than high entropy data

### Deadline: 3/7   
  after you submmit, you will be graded, and you have 2 weeks to resubmit your project   
  Implementation   
  Coding style   
  User manual (Installation and usage) e.g. man page   
  (target audience: basic familinity with ns-3)   

  Presentation/demo   (5/9)
  Final Project  (Final's week)

  Check pont #1 2/14
  
Imple

Part2: A Base Class for Differentiated Services 


# 2019/2/5

Exam: 3/21/2019 2:40 - 4:25 pm

# Traceroute
* Traceroute repurposes TTL and ICMP functionality

  * Sends probe packets increasin TTL starting from 1
  * ICMP errors identify routers on the path

# Round Trip Time (RTT)

$ traceroute

example:

```shell
traceroute www.mit.edu

traceroute to e9566.dscb.akamaiedge.net (23.9.36.126), 64 hops max, 52 byte packets
 1  10.1.0.3 (10.1.0.3)  2.308 ms  1.229 ms  1.172 ms
 2  inet-fwsm1-vlan601.usfca.edu (172.16.64.228)  1.747 ms  1.679 ms  1.877 ms
 3  138.202.128.203 (138.202.128.203)  1.845 ms  1.648 ms  1.682 ms
 4  xe-8-0-1.bar1.sanfrancisco1.level3.net (4.7.13.213)  4.340 ms  4.479 ms  4.449 ms
 5  ae-3-19.edge2.sanjose3.level3.net (4.69.209.189)  5.926 ms  6.283 ms  6.125 ms
 6  et-0-0-71-1.cr6-sjc1.ip4.gtt.net (77.67.69.97)  6.437 ms
 * *
 7  * * * // -> some router do not response before traceroute time out
 // 
 8  * * *
```


# ICMP 

The Internet Control Message Protocol (ICMP) is a supporting protocol in the Internet protocol suite. It is used by network devices, including routers, to send error messages and operational information indicating, for example, that a requested service is not available or that a host or router could not be reached.[1] ICMP differs from transport protocols such as TCP and UDP in that it is not typically used to exchange data between systems, nor is it regularly employed by end-user network applications (with the exception of some diagnostic tools like ping and traceroute).

# TTL 

Time to live (TTL) or hop limit is a mechanism that limits the lifespan or lifetime of data in a computer or network. TTL may be implemented as a counter or timestamp attached to or embedded in the data. Once the prescribed event count or timespan has elapsed, data is discarded or revalidated. In computer networking, TTL prevents a data packet from circulating indefinitely. In computing applications, TTL is commonly used to improve the performance and manage the caching of data.

# RTT

In telecommunications, the round-trip delay time (RTD) or round-trip time (RTT) is the length of time it takes for a signal to be sent plus the length of time it takes for an acknowledgement of that signal to be received. This time delay includes the propagation times for the paths between the two communication endpoints.

# 30 hops

Maximum number of hops: 30 hops

# MTU

In computer networking, the maximum transmission unit (MTU) is the size of the largest protocol data unit (PDU) that can be communicated in a single network layer transaction. The MTU relates to, but is not identical to the maximum frame size that can be transported on the data link layer, e.g. Ethernet frame.

# Path MTU Discovery:

# Transport Layer Services
Provide different kinds of data delivery across the network

TCP is full-featured, UDP is a glorified packet

|TCP(Stream) | UDP |
--------------------
|Connections| Datagrams|
|Arbitrary length content| Limited message size|
|Flow control matches sender to receiver | Can send regardless of receiver state|
|Congestion control matches sender |


# Port

Application process is identified by the tuple IP address, protocol, and port.

* Ports are 16-bit integers representing local "mailboxes" that a process leases

Servers often bind to "well-known ports"

* <1024, require administrative privileges

Clients often assigned "ephemeral" 

# UDP Header

* Uses ports to identify sending and receivig application processes
* Checksum (16 bits) for reliability // Maximum number of port

UDP length (Source port) -> UDP checksum (Destination port)

checksum = some IP header fields + UDP header + Data -> (src-address, destination address, protocol) -> so call IP pseudo header

Why transport layer interests 

# IPv6

* motivation: initial motivation: 32-bit address space soon to be completely allocated.

* IPv6: 128 bit different ip address

* additional motivation:
  * header format helps speed processing/forwarding
  * header changes to facilitate QoS

* IPv6 datagram format:
  * fixed-length 40 byte header
  * no fragmentation allowed

  * priority: identify priority among datagrams in flow
  * flow Label: identify datagrams in same "flow." (concept of "flow" not well defined).
  * next header: identify upper layer protocol for data
  * checksum

# Transition from IPv4 to IPv6
  
  * not all routers can be upgraded simultaneously
    * no "flag days"
    * how will network operate with mixed IPv4 and IPv6 routers?
  
  * Tunneling: IPv6 datagram carried as payload in IPv4 datagram among IPv4 routers


# 02/12/2019

# TCP

# To make packet in order:
## 1. Simple case: One message at a time is Stop-and-Wait (Normal case below)
  Limitation: Not efficient:
  e.g.:
    R = 1 Mbps, D = 50 ms
      RTT (Round Trip Time) = 2D = 100 ms
      How many packets/sec?
    What if R = 10 Mbps

## 2. Sliding window: 
    1. Piplining and reliability
    Generailzation of stop-and-wait
      Allows W packets to be outstanding
      Can send W packets per RTT (=2D)
    What W will use the network capacity?
      e.g: R = 1Mbps, D = 50 ms

# Sliding Window Protocol
## Go-Back-N
  Sender buffers up to W segments until they are acknowledged
  LFS=LAST FRAME SENT, LAR=LAST ACK REC'D
  Sends while LFS - LAR <= W

  Receiver keeps only a single packet buffer for the nextsegment

  Go-back-N sinderuses a single timer tp detect packet loss
### Sequence Numbers
  Need nore than 0/1 for Stop-and-Wait
  For Go-Back-N, need W+1 Sequence Number

## TCP Flow Control

  Adding flow control to the sliding window algorithm

  Problem: what if the receiver is overload?

  Receiver with W buffers:
    App pulls inorder data
  
  Avoid loss at reveiver by telling sender the available buffer space

## TCP-style example
  SEQ/ACK sliding window
  Flow control with WIN
  SEQ + length < ACK + WIN
  4KB buffer at receiver
  Circular buffer of bytes

Always discard out of order packets.

# Project

UDP IP header p2p

node - node(compress) - node(decompress) - node

Point to Point Protocol (PPP) 
 PPP header | protocol | Data (information) (include the ip header etc.) | trailer


ppp

rfc (Remote Function Call)

LZS Compressor
-> Two router already decide to use LZS compressor not the following

ccp -No implementing
negotication phease -No implementing
Standard: -No implementing
Compressed date builder on x3.241_1994

Only compress the data that allowed to be compress

file with protocol number to allow compression

## Simulation Validation:

Delta H (introphy) - Delta L (introphy)

Run UDP application with 10 times:

X = 1, 2, 3, ..., 10 Mbps 

Get the val, (10 points)

Build a continuous graph(as following).

Delta H (introphy) - Delta L (introphy)
|
|
|
|
|
|-------------------- Mpbs

CLI: 1. Compression Link Capacity (Required)
      2. Keep config in CLI (suggested)

# Feburary 19th

# Wireshark
key word
ns-3 : .pcap
tcpdump: only command line tool

# TCP timeout

How to set the timeout for sending a retransmission: Adapting to the network path.

Timeout should be "Just right"
* Too long wastes network capacity.
* Too short leads to spurious resends.
What is just right? (A round trip time sounds to be valid)

Easy to set on a LAN (Link)
* Short, fixed, predicable RTT

Adaptive Timeout (Best solution)
* Keep smoothed estimates of the RTT(1) and variance in RTT(2)

# TCP feature

# Reliable Bytestream

Bidirectional data transfer
* Control information (e.g., ACK) piggybacks on data segments in reverse direction.

# TCP Sliding Window - Sender
## Cumulative ACK

# Window size for flow control

# Other TCP Details

# TCP ACK generation

# Quality of Service

# Over-Provisioning

# QoS
Classifier -> queues -> Scheduler ->

Strict Priority Queuing 
Classifier: decides whether a packet goes to high priority queue or low priority queue.

# Sharing bandwidth between flows
Fair Queuing
FIFO Queuing
Round-Robin Queuing
Fair Queuing -> approximate by computing virtual finish time

WFQ (Weighted Fair Queue)

# Shaping traffic to constrain bursts
* Token buckets
* Key building block for QOS

# Project 2

# 2/16/2019
QoS Mechanisms Continued

# Deficit Round Robin (DRR)
A Base Class to Simulate Differentiated Services

# Project2
## Base Class Design
+: public, -: private, #: protected
<>->: composition, (has a relationship: A class that contains other classes as members)
->: Inheritance: is a relationship, a class drived from another class
: bool : function return a bool

Important classes:
nc-3::Queue, ns-3::DrpTailQueue

TrafficClass<Filter <FilterElements>>
An packet comes in -> checkFilterElements(All match) -> Filter (If can not match existing filterElement, create new filterElement) -> TrafficClass

## Project 2 Components
Part 1) Implementation of DiffServ Class.
Part 2) Using your implementation of DiffServ, implement (simulate) SPQ and DRR QoS mechanisms.
Part 3) Verify and validate your simulated SPQ and DRR.

### CLI Argument:

#### SPQ:
  spq: one config file: -> 1) # of queues, 2) Priority level

  Example: 1, 2; 2, 2; 3, 1; Json format for instance

#### DRR: one config file
1) # of queues
2) Corresponding quantums
3) Verify and validate your simulated SPQ and DRR

#### Extra credit:
1. make config file more interesting: Takes sequence of commands to configure SPQ on a Cisco Carahst 3750
(1 or 0) 

#### Simulation Validation: DRR
Client/server applications can be found in ns-3

#### Deadline:

Two checkpoints for project2
  * Checkpoint #1: March 28th in class
  * Checkpoint #2: Week of April 15th

Code and technical manual: Wed May 1st

Demo/Presentation: May 9th in Class
  8 min for each team, 4 min for project1, 4 min for project2 (Part of your grade of presentation)
  Focus your presentation is your design
    e.g. Which ns-3 class did your design modlify, how and why?
      Design issues/challenges/limitations
      Suggest to improve DiffServ class
      Do not recommand demo during presentation

Final Report: May 15th
  * Your design and everything above
  * Implementation Detail
  * Simulation Validation
  * API usage -> instruct user to use your api
  * Alternative design/implementation
  * References (e.g. lzs library)

Format:
  * ACM Latex template
  Max 5 pages

# Grading Session for Project 1
-> has pcap file after you correctly run your program

sender [sender.pcap] -> compressor [compressor.pcap] -> [] decompress [decompressor.pcap] -> [receiver.pcap] reciever

udp sender.pcap // sender sent
udp receicer.pcap // 
compressor.pcap // after data be compressed
decompressor.pcap // 
plot

Resubmission for regrade is due March 25th

# Grading Session for Project 2

S -> [pre] ROUTER [pst] -> R

pre_spq.pcap
pst_spq.pcap
pre_drr.pcap
pst_drr.pcap

simulation pit SPQ 

# 3/5/2019

# How to use debugger
Should be really skilled in debugging
First two: for debugger in cs621 website

# /dev/urandom vs /dev/random
urandom is more random, but non-blocking. random is blocking

# Weifhted Round Robin

- Approximales GPS (Generalized Processor Sharing) Model
- We need to calculate the "nomalize weight" of each queue i.
- Wi * = wi (assigned weight of queue i) / li (mean packet size in queue i)
- Find smallest normalized weight, W min *
- Number of packet sent from queues i each round: ceil( Wi * / W min *)

# Routing versus Forwarding

Forwarding is the process of sending a packet on its way.
Routing is to figure out which way to send

# Delivery Models

Different routing used for different delivery models
1. Unicast: send info to one node
2. Broadcast: send to every nodes
3. Multicast: send to more than one nodes
4. Anycaset: send info to the cloest neighbor 

# Goals of Routing Algorithms

We want serveral properties of any routing scheme:
1. Correctness
2. Efficient paths
3. Fair paths: Doesn't starve any nodes
4. Fast convergence: Recovers quickly after changes
5. Scalability: Works well as network grows large

# Rules of Routing Algoritjms

Decentralized, distributed setting
1. All nodes are alike; no controller
2. Nodes only know what they learn from exchanging to their neighbor
3. concurrently
4. maybe failures

# Shortest Path

What are "Best" paths anyhow?

Many possibilities:
1. Latency, avoid circuitous paths
2. Bandwidth, avoid slow links
3. Money, avoid expensive links
4. Hops, to reduce switching

But only consider topology
1. Inore workload, e.g., hotspots

We'll approximate "best" by a coust function that captures the factors
1. Assign each link a cost
...

Find the shortest path A -> E
All links are bidirectional 

# Dijkstra's Algorithm
Initialization
We'll compute shortest paths from A

```
function Dijkstra(Graph, source)
  create vertex set Q
  // Init
  for each v in G
    dist[v] = infite
    prev[v] = undifined
    add V to Q
  
  dist[source] = 0
  while Q is not empty
    u = v in Q with min dist[u]
    remove u from Q
    for each neighbor v of u:
      alt = dist[u] + length(u, v)
      if alt < dist[v]
        dist[v] = alt
        prev[v] = u
  return dist[], prev[]

```
Run time: - Depends on implementation and data structure used
- If we use heap implementation of priority queue: T(n) = O(E lg V)

Distance Vector Algorithm
Each node maintains a vector of distances, (and next hops) to all destinations

# Distance Vector Dynamics

1. Adding routes:
  News travels one hop per exchange
2. Removing routes
  When a node fails, no more exchanges, other nodes forget
3. But partitions (unreachable nodes in divided)

Good news travels quicjly, bad news slowly
Desired convergence
"Count to infinity" scenario

Varous heuristics to address
  e.g., "Split horizon, poison reverse" (Don't send route back to where you learned it from.)
But none are very effective
  Link state now favored in practice

# RIP (Routing Information Protocol)

DV protocol with
TODO
Routers send vectors every 30 sec
TODO
RIPv1 specified in RFC1058 (1988)
TODO

# Flooding

How to broadcast a message to all nodes in the network in general

Rule used at each node
Inefficient

Remember message using...

# Flooding Details

Remember message (to stop flood) using source and sequence number
So next message (with higher sequence number) will go through
To make flooding reliable, use Automatic Repeat Request (ARQ)

# Every in assignment3 is in exam

# Link stack rendering

# How to compute shortest paths in a distributed network

# Link-State Routing

One of two approaches to routing
Widely used in practice

# Link-State Algorithm

# Topology Dissemination

Each node floods link state packet (LSP) that describes their portion of the topology.

# Route Computation

Each node has full topology

# Forwarding Table

Source Tree for E (from Dijkstra) E's Forwarding Table

# Hanling Changes

On changes, flood updated LSPs, and re-compute routes (E.g., nodes adjacent to failed link or node initiate)

# Handling Changes

Link failure: Both nodes notice, send updates LSPs. Link is removed from topology.
Node failure: All neighbors notice a link has failed. Failed node can't update its own LSP. But it is OK: all links to node removed.

How neighbor figure out a node is down? 

# Link-State Complication

Things that can go wrong: 
1. Seq. number reaches max, or is corrupted
2. Node crashes and loses seq. number
3. Network partitions the heals

Strategy
Include age on LSPs and forget old information that is not refreshed

Much of the complexity is due to handling corner cases

# DV/LS Comparison

Distance Vector
Link State

# IS-IS and OSPF Protocols

Widely used in large enterprise and ISP networks.

# Compromised Router

Direct tracffic yo a 3rd party
Man in the middle attack
Packet Alteration
Hijack traffic
Passive Evesedropping
Drop
Delay
out of order delivering
Forged control packets

# Exam

Concise anwser

# Structure of the Internet

# Internet-wide Routing Issues

# Effects of Indepemdent Parties

# Routing Policies

# ISP Internet service provider

# AS (Autonomous Systems)

# BGP Border Gateway Protocol

# NAT

# Middleboxes

# Net (Network Address Translation) box

# Private address

# 4 / 9 / 2019 

# Delay Discrimination
Some middleboxes influence traffic flows by imposing discriminatory delays on different network flows;

Pa: A packet with a predefined A properly and size l.
Pb: A packet with a predefined properly B and size l.
td(p): Departure time (time to transmit the last bit of packet p into the wire).
ta(p): Arrival time of packet p to the middlebox.
dMB := td(p) - ta(p), total delay imposed by middlebox on packet p.
tT: transmission time.
cP: The path capacity between sender R receiver.
nI: initial packettrain: min number of packets you need to saturate the queue.

loss rate = 1 - SA/X >= 1 - SA / CP >= T = 20 %

# Delay Discriminator

# Simulation

# Wireshark plot
To make plot

# Network Security
Threat model: The dangers and attacker's abilities
Can not assess risk otherwise

# Some example threats
It's not all about encrypting messages

Attacker: Eavedropper, Intruder, Impersonator, Extortionist

# Security is hard as a negative goal
Try to ensure security properties that do not let anything bad happen!
Only as secure as the weakest link
Could be design flaw or bug in code, But often the weak link is elsewhere

# Risk Management
WEP: Cryptography was flawed; can run cracking software to read WIFI traffic

Today, WPA2/802.11i security
Computationally infeasible to break!

# Cryptology / Cryptanalysis

# Encrypting information is useful for more than deterring eavesdroppers
# Designing a secure cryptographic scheme is full of pitfalls!

# Goal and Threat Model

# TLS

# Encryption/Decryption Model

* Encryption is a reversible mapping
* Assume attacker knows algorithm
* Algorithm is parameterized by keys

# Encryption/Decryption Model
Two main kinds of encryption:
Symmetric key encryption, e.g., AES
Alice and Bob share secret key
Encryption is a bit mangling box

# Symmetric (Secret Key) Encryption

# Key Distribution
This is a big problem on a network! Often want to talk to new paries.
Symmetric encryption problematic: Have to first set up shared secret.
public key idea has own difficulties: Need trusted directory service.

#  Symmetric vs Public Key
Have complementary properties. Want the best of both.

# Winning Combination
Alice uses public key encryption to send Bob a small private message. (It's a key)
Alice and Bob send large messages with symmetric encryption. Using the key they now share.
The key is called a session key. Generated for short-term use.

Encryption information to provide authenticity (= correct sender) and integrity.

# 
Goal is to let Bob verify yhe message came from Alice and is unchanged

# Digital Signature

Kind of public key operation - public/private key parts
-> Autenticity and integrety in this case.

# Speeding up Signatures

# Message Digest or Cryptographic Hash
* Digest/Hash is a secure checksum
  * Deterministically mangles bits to pseudo-random output (like CRC)
  * Can not find messages with same hash
  * Acts as a fixed-length descriptor of message - very useful!

# Preventing Replays
We normally want more than confidentiality, integrity, and authenticity for secure messages!
Do not want to mistake old message for a new one - a replay. Acting on it again may cause trouble.

To prevent replays, we use "nounce" (one time approach).

# TLS
How tls actually works: https://lasr.ucla.edu/vahab/resources/notes_on_tls.pdf

# Network Discriminator
Detection Framework:
For MB to be normally detectable it is sufficient to show:

# Strict Priority Queuing
SPQ is a network discriminator.

# Detecting SPQ on Internet
SND: the sending host
RCV: the receiving host
PH: The packet that is being p
PL: The packet that is being de privitized
TXQMB: Transmission queue of the middlebox
CP: The path capacity from SND to RCV
tT: transmission time
r: The sending rate of the probe packets as received MB.
N: Patter
M: Num of repeating pattern

|SND| (r) - X - |SPQ|TxQMB| - Z - |RCV|
Z = Cp (path capacity)

All possible scenerios: 
1) Z < r <=  X 
2) r <= X <= Z (Do not consider this case)
3) r <= Z <= X  (Do not consider this case)

Goal 1: Send Li's so that H queue never buid up.
Goal 2: Make sure high priority queue always busy. Smin >= Theta = 1 ms

Delta i = transmision time of All H' packets and Lx prior to Li
L: size of all packets
Si = tT(H') * (N'*(M - 1)) + SUM(tT(Lj)) for j = 0; j < i
tT = L / Z 

--- 
Exist a case that: ...

What is an optimal value for N'?
In High priority pahse, Hi are sent at the r / (N' + 1)
So as long as < Z, the Goal 1: r / (N' + 1) < Z
In low priority phase, Hi are sent at the: r * N' / (N' + 1) 

Z < r * N' / (N' + 1)  

---
Find lower bound:
From 1 & 2
r / (N' + 1) < Z < N' / (N' + 1) * r  

N' > (r - Z) / Z
N' > Z / (r - Z)

Take the max above
