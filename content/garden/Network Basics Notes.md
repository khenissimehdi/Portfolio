---
title: "Network Basics"
date: 2020-01-01
lastmod: 2024-02-04
draft: false
garden_tags: ["Network"]
summary: " "
status: "seeding"
---


# Network Basics

## OSI Model

Application → Deals with applications, people still can read this  ( http, ftp ) 

Prestation (translation ) → Here the data is being converted into a form that can be sent over network ( compression, deCompression , encryption, decryption ) 

Session → Controls dialog during communication ( establish, manage, and terminate ) communications 

Transport  → Transfer data between  end users responsible of resending any packets that do not receive an acknowledgment ( can guaranteed that data is received )

Network → Routing the data packet based on the IP

DataLink → Send Data to thee physical layer ( data packets are encoded or decoded into bits  and got two parts MAC Media access  Control and LLC Logical Link Control ) 

Physical → Define the topology of a network

## IP

Consist of Two Parts  

1 - Network address 

2 - Host address 

### IPv4

32 bits means 4 octets of 8 bits 

1 octet → 8 bits 

### IPv6

128-bit hexadécimal adress

to convert you to go 4 bits by 4 bits 

## SubNetMask

get how many bits in the network are used for the network by masking the network part of the ip 

A → 255.0.0.0 ( 1 - 128 ) →  / 8

B → 255.255.0.0 ( 128 - 191 ) →  / 16 

C → 255.255.255.0 ( 192 - 223 )  → /24

### Usefull formulas

To find the number of possible network ids use 

2^numbeOfNetworkBits - 2 

To find the number of possible host ids use 

2^numberOfHostsBits - 2 

### UseFull Video

[How to calculate the total number of the usable host IDs?](https://www.youtube.com/watch?v=9uC-6lV1xT4)

## SubNet

Useful Links : 

[PDF](http://www4.northampton.edu/kmanna/Cisco_Student_Web/SG/How-to-Subnet%2010.pdf)

[https://www.youtube.com/watch?v=S_EfcLo2Wv0](https://www.youtube.com/watch?v=S_EfcLo2Wv0)

# Dynamic IP Adress

they come from DHCP SERVER ( Dynamic Host Configuration Protocol ) 

if the pc can’t reach thee server or the server goes down it will assign it self an address 

## Static IP

Manual IP assigning 

DHCP gives ip addresses as lease mean that they will change 

if the dhcp server and the machine are not in the same subnet ( means they have different  ip settings ) the dhcp server will not get the request cause broadcast doesn’t go outside of their subnets. 

that why we use a dhcp relay enable option that way the request will be forwarded to the the  dhcp server

## TCP/UPD

tcp → transmission control protocol  



udp → user datagram protocol

is connectionless mean that there is no 3 way handshake and it just spam data as fast as possible 

## FTP

ftp → File transport protocol 

download and upload files between users 

its a connection oriented protocol that uses TCP for file transfer 

### TFTP

tftp → trivial file transport protocol 

used to transfer file inside the network and not the internet 

and use udp 

### SFTP

sftp → secure file transfer protocol 

its like ftp and it uses another layer of security means data is encrypted during data transfer using secure shell 

## SMTP

smtp → simple mail transfer protocol 

sends mails and uses tcp protocol 

### Pop3

is used to receive  emails you an only use it download mails on your computer but it doesn’t sync your data and when you do that the email is removed from your mail server unless you say you want to keep a copy

### IMA4P

ima4p → internet message access protocol  ver 4 

it gives you power over your mail server mean you will be able to read and manage your mails and it will also create a copy of your mail automatically and it will also syncs email and folders between the mail server and your computer 

# HTTP

http → hypertext transfer protocol 

used in webserver to load webpages 

### https

is a secure version of http it will just encrypt the data

# Telnet

used to access devices but its not secure that way it used only in local network devices 

### SSH

ssh → secure shell 

cause it encrypt data while sending it create like shell around the connection to to protect the data 

# ARP

arp → address resolution protocol 

used to resolve ip address to mac address

that what is used by computers to communicate with each other 

by checking the cache arp the computer will go look for the matching ip address if not found it will send a request  looking for the one with that same address if its found the computer will inform the sender of it presence 

### RARP

reverse ARP convert mac to IP

## SCP

scp → secure copy protocol 

uses secure shell protocol to safeguard data as it being transferred over a network 

## SNMP

snmp → simple network management protocol 

used to collect data from network devices 

# Ports

got two protocols TCP/UDP

logical connection that is used by programs to exchange informations 

port are identified by unique numbers 

0 → 65535



# DNS

dns → domain name system

resolve domain name to ip adresses 

there is also WINS but it resolves computer names to ip address

# NAT

nat → network address translation

translate a set of ip addresses to another set of ip addresses 

for example form private to public or from public to private 

## PAT

pat → port address translation

like nat but it also use the port number 

## SNAT

static nat 

it give computers a permanent public ip addresses 

this used for example for mail servers 

Proxy 

used for cashing data from the internet one use example of this is when a company use this techno to store webpages visited by employees so that the next time an employee visit that page again it load that cached page a proxy can be used also for other things 

Benefits 

Speed 

Bandwidth : 

***The maximum amount of data transmitted over an internet connection in a given amount of time**.*

Security 

## RDP

rdp → remote desktop protocol

## CSMA/CD

 csma/cd = Carrier Sense Multiple Access with Collision Detection

allow computer to sense if the wire is free before sending if not it waits 

mostly used on wireless networks 

it will first send aa small packet of data to check if everything is free before sending 

## Loopback interface

[localhost](http://localhost) 

## Routing table

contains information about what path the data takes to reach it destination 



## Routing protocols

collect information about the network and map the best path to transfer data 

there is 3 types 

Distance vector  : factor distance based on how many hops 

when of the those protocols is called rip ( routing information protocol ) routers that use it broadcast their information every 30 sec 

but ripv2 is better cause it solve the problem of broadcast problem

there is also bgp  ( border gateaway protocol )  and its the standard routing protocol of the internet 

it determines path direction based on paths and policies 

LinkState  : 

routing protocol that is used  by routers to share information and independently map out the best path on the network .

OSPF → open shortest path first  

a routing protocol that is used to determine the correct rout for data packet to take for their destination 

it collect information from other routers using IP and create a topology map of the network 

IS-IS → intermediate system to intermediate system 

Routers are organized into a domain means groups and IS-IS functions inside those domains but this service use clns ( connectionless network service ) to communicate with other routers 

Hybrid : 

EIGRP → Enhanced interior gate-away routing protocol and as the name say it 

it’s combination of Distance vector  and LinkState and only runs on cisco routers 

fast, less overhead can support many network layer protocols 

## SIP

sip → session initiation protocol 

Establishes communication session over the internet.

example : 

VoiP ( voice over IP)

term that used for voice communication over ip networks 

also used for instant messaging and conferencing services 

## RTP

rtp → real time transport protocol

the internet standard for transporting real-time data such as streaming audio and video 

it used over udp so it doesn’t guarnte data delivery

used also with RTCP → real time transport protocol and that enable you to monitor the quality of the data being delivered 

uses both unicast and multicast

## ISDN

isdn → integrated service digital network

International standard foor digital transmission over odinary telephone lines 

## T1 ( europe is E1)

t1 → T carrier level one 

commonly used internet service for business today 

carries data or voice 

## T3

t3 → T carrier level three

mainly used by ISP ( internet service providers ) and they are connected directly to the internet 

## OCx

OCx → optical carrier 

Describes the speed of networks that can be carried on SONET ( Synchronous Optical Network ) 

## DSL

dsl → digital subscribier line 

it can carriers voice and data at the same time 

### ADSL

adsl → asymmetric  digital subscribier line 

download speed > upload speed 

### SDSL

sdsl → symmetric  digital subscribier line 

download speed == upload speed 

### VDSL

vdsl → very high bit dsl

# Remote access services

## RAS

ras → remote access service 

service that enable you to connect to a computer from a remote location 

## SLIP

slip → serial line internet protocol 

Designed so data can transmit over serial ports and modem connections 

Doesn’t support encryption or authentication 

all information are sent in clear text 

does not provide and error checking limited to using only tcp/ip

## PPP

ppp → point-to-point protocol 

the standard remote access used today 

support encryption or authentication 

is secure 

## PPPoE

pppoe →   point-to-point protocol over ethernet

uses PPP over ethernet 

used to encapsulate PPP frames in ehternet frames 

Developed for DSL, cable modem, or wireless connection to the internet 

used also to connect multiple users on  LAN to a remote site sharing  a common device 

## PPTP

pptp → point to point tunnelling protocol 

used for creating vpns 

ensure that data transfer is secure by creating a secure tunnel 

## GRE

gre → generic route encapsulation 

used with pptp in creation of a VPN network 

create the tunnel in PPTP 

Encapsulates the data in secure manner 

## VPN

vpn → virtual private network 

a private communication network that uses public network to establish a remote connection 

encrypt data when sending decrypt data when receiving 

provide a link btw two points over the internet 

 vpn concentrator a device that create the vpn connection and manages the delivery of the messages btw the vpn computer devices 

authentiate users encrypt the data and assign tunnel/ip adresses to users 

not always needed only in cases of managing a lot of vpn connections 

### VPN TYPES

- SITE TO SITE → connection between two organisations
- HOST TO SITE → connection between simple computer and organisations
- HOST TO HOST → connection between two computers

 

# Authentication

## PAP

pap → password authentication protocol 

not safe everything is sent in clear text 

## CHAP

chap → challenge hand shake protocol 

Encrypt username and password 

uses 3 way handshake 

the server send a challenge to the client the client will use the hash it got  and send a response back then the server will check using his hash and if the value matchs its all good 

## MS-CHAP

ms-chap is also CHAP but by microsoft 

ms-chap 2 both client  and server are authenticated means they challenge each other 

## Radius

radius  → remote authentication dial-in service 

enable a single server such as domain controller to handle all authentications 

enable an organisation to store all user related to data to one place 

a radius server makes the request on the user’s behalf after authentication 

## Kerberos

Developed by mit and it give users tickets that makes them able to access devices on the network  

## EAP

eap → extensible authentication protocol 

is an extension to PPP support many methods of authentication 

commonly associated with smart cards 

# Security protocol

## IPSec

Ipsec → internet protocol security 

Encrypt  data  

there is key that locks and unlocks the data while it travel through a network

it got two modes : 

- Transport mode → message portion is encrypted
- Tunnel Mode → entire packet is encrypted

# L2TP

l2tp → layer 2 tunneling protocol 

Combination of Cisco’s layer 2 forwarding and PPTP

it authenticate both the computer and the user using a digital certificate to insure that the data wasn’t  change during the process 

to prevent man in middle attacks 

## SSL

ssl → secure socket layer

It’s a protocol that provide security on the internet 

Provides security in 3 ways : 

- Authenticate the server
- Authenticate the client
- Encrypt the data

## TLS

tls → the latest industry standard SSL protocol  it authenticate the server and the client and encrypt the data 

Made up of 2 layers :

- TLS Record Protocol  → Makes the connection is private and reliable
- TLS Handshake Protocol → Server and client can negotiate encryption algorithm and cryptography keys before the data is sent

[https://www.indusface.com/blog/ssl-vs-tls-know-your-security-protocols-for-2020/#:~:text=The main reason why SSL,of messages%2C and encryption strengths](https://www.indusface.com/blog/ssl-vs-tls-know-your-security-protocols-for-2020/#:~:text=The%20main%20reason%20why%20SSL,of%20messages%2C%20and%20encryption%20strengths).

## 802.1x

Used for both wired and wireless networks 

Control network access by word 

Port based authentication 

[Network Utils ](https://www.notion.so/Network-Utils-5c76bf9225f349c39cebacaf47eb93bf?pvs=21)

[Troubleshooting ](https://www.notion.so/Troubleshooting-c42a45d7f69546d5a6a314059b576e23?pvs=21)

[Routing](https://www.notion.so/Routing-082dbf9800ae41bbaf19a68cecce7705?pvs=21)