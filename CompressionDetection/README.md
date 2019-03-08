# CompressionDetection

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

## Part2: A Base Class for Differentiated Services 

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

