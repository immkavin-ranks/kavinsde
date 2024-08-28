# Sniffers, Session Hijacking and Denial of Service

1. **Sniffers** attack the confidentiality of information in transit. Sniffing gives the attacker a way to capture data and intercept passwords.
2. **Session hijacking** is an attack method used to attack the confidentiality and integrity of an organization. If the attacker can successfully use session hijacking tools, he can literally steal someone else’s authenticated session. He will be logged in with the same rights and privileges as the user from whom he stole the session. He is free to view, erase, change, or modify information at that point.
3. **Denial of service** targets availability, enabling attackers to prevent authorized users to access information and services that they have the right to use. DoS can be considered an easy attack to launch and can be devastating. Although a DoS attack doesn’t give the attacker access, it does prevent other legitimate users from continuing normal operations.
# Sniffers

>Sniffing is the process of monitoring and capturing data. Sniffers are powerful pieces of software that can place a host system’s network card into promiscuous (easy or loose) mode.

* A network card in promiscuous mode can receive all the data it can see, not just packets addressed to it.
* If you are on a hub, a lot of traffic can potentially be affected. Hubs see all the traffic in that particular collision domain. Sniffing performed on a hub is known as **passive sniffing**. However, hubs are outdated, so you are not going to find hubs in most network environments.
* Most modern networks use switches. When sniffing is performed on a switched network, it is known as **active sniffing**. Because switches segment traffic, it is no longer possible to monitor all the traffic by attaching a promiscuous mode device to a single port. To get around this limitation, switch manufactures have developed a solution known as port mirroring or **spanning** Switched Port Analyzer (SPAN).
* Spanning a port allows the user to see traffic destined for their specific ports as well as all traffic being forwarded by the switch. This feature allows the switch to be configured so that when data is forwarded to any port on the switch, it is also forwarded to the SPAN port.
* Sniffers operate at the **data link layer** of the OSI model. This means that they do not have to play by the same rules as applications and services that reside further up the stack. Sniffers can grab whatever they see on the wire and record it for later review. They allow the user to see all the data contained in the packet, even information that you may not want others to see. Many of the protocols and applications originally developed as part of the TCP/IP stack send data via clear text. Examples: FTP, HTTP, Telnet, SMTP, DNS
## Active Sniffing

>To use sniffers successfully, the attacker must be on your local network or on a prominent intermediary point, such as a border router, through which traffic passes. The attacker must also know how to perform active sniffing, which means he must redirect the traffic so that he can see it.
### Address Resolution Protocol (ARP) poisoning

>ARP is how network devices associate a specific MAC address with an IP address so that devices on the local network can find each other.

![[Pasted image 20240826194736.png]]

* The method involves sending fake ARP requests or replies to the switch and other devices to attempt to steer traffic to the sniffing system. Fake ARP packets will be stored by the switch and by the other devices that receive the packets. The switch and these devices will place this information into the ARP cache and now map the attacker to the spoofed device. The MAC address being spoofed is usually the router so that the attacker can capture all outbound traffic.
* The hacker can pull off many types of man-in-the-middle attacks. This includes passing on the packets to their true destination, scanning them for useful information, or recording the packets for a session replay later. IP forwarding is a critical step in this process. Without it, the attack will turn into DoS.

![[Pasted image 20240826204507.png]]
### MAC flooding

>MAC flooding is the second primary way hackers can overcome the functionality of a switch. MAC flooding is the act of attempting to overload the switch’s content-addressable memory (CAM) table. 

* All switches build a lookup table that maps MAC addresses to the switch port numbers. This enables the switch to know what port to forward each specific packet out of. The problem is that in older or low-end switches, the amount of memory is limited. If the CAM table fills up and the switch can hold no more entries, some might divert to a fail-open state.
* Flooding overloads the switch with random MAC addresses and allows the attacker to then sniff traffic that might not otherwise be visible. The drawback to this form of attack is that the attacker is now injecting a large amount of traffic into the network. This can draw attention to the attacker. 
* With this type of attack, the sniffer should be placed on a second system because the one doing the flooding will be generating so many packets that it might be unable to perform a suitable capture.
### Sniffing and Spoofing Countermeasures

* Port security can be accomplished by programming each switch and telling it which MAC addresses are allowed to send/receive and be connected to each port.
* If you are using Cisco devices, this technology is known as **Dynamic ARP Inspection** (DAI). DAI is a Cisco security feature that validates ARP traffic. DAI can intercept, record, and discard ARP packets with invalid IP-to-MAC address bindings. This capability protects the network from some man-in-the-middle attacks.
* Programs such as Arpwatch keep track of Ethernet/IP address pairings and can report unusual changes. You can also use static ARP entries, migrate to IPv6, use encryption, or even use an IDS (intrusion Detection System) to alert on the MAC addresses of certain devices changing.
# Session Hijacking

Session hijacking takes sniffing to the next level. Hijacking is an active process that exploits the weaknesses in TCP/IP and in network communication. 

>Hijacking contains a sniffing component but goes further as the attacker actively injects packets into the network in an attempt to take over an authenticated connection.

There are two areas of attack when considering a session hijacking attack: 
* OSI transport layer (TCP) attacks: Focus on the interception of packets during data transmission
* OSI application layer attacks: Focus on obtaining or calculating session IDs
## Transport Layer Hijacking

>Session hijacking provides the attacker with an authenticated session to which he can then execute commands. The problem is that the attacker must identify and find a session.

For transport layer (TCP) hijacking to be successful, several things must be accomplished: 
1. Identify and find an active session. 
2. Predict the sequence number. 
3. Take one of the parties offline. 
4. Take control of the session.
### Identify and Find an Active Session

* When the attacker and the victim are on the same segment of the network. The attacker can sniff (passive or active sniffing) the sequence and acknowledgment numbers.
* If the attacker and the victim are not on the same segment of the network, blind sequence number prediction must be performed. 
* With blind session hijacking, the session numbers must be guessed, or the attacker may send several packets to the server to sample sequence numbers. If this activity is blocked at the firewall, the probe will fail.
### Predict the Sequence Number

* A fundamental design of TCP is that every byte of data transmitted must have a sequence number. The sequence number is used to keep track of the data and to provide reliability.
* The difficulty in predicting sequence numbers depends on the OS: Some do a better job at being random than others.

>So, at what point do attackers want to start injecting packets into the network after they have determined the proper sequence?

Obviously, the hacker will need to do this before the session ends, or there will be no connection left to hijack.

But just as obviously, the attacker does not want to do this at the beginning of the session. If the hacker jumps in too early, the user will not have authenticated yet, and the connection will do little good. 

The hacker needs to wait until the user has provided a password and authenticated. This allows the hacker to steal trust. The trust doesn’t exist before the authentication has occurred.
### Take One of the Parties Offline

With a sequence number in hand, the attacker is now ready to take the user connected to the server offline. The attacker can use a denial of service, use source routing, or even send a reset to the user.

>The objective is to get the user out of the communication path and trick the server into believing that the hacker is a legitimate client.
### Take Control of the Session

Now the hacker can take control of the session. As long as the hacker maintains the session, the hacker has an authenticated connection to the server. This connection can be used to execute commands on the server in an attempt to further leverage the hacker’s position.
## Application Layer Hijacking

>The whole point of session layer hijacking is to be able to steal or predict a session token. 

There are several ways in which these attacks can be carried out, which include session sniffing, predictable session token ID, man-in-the-middle attacks, man-in-the-browser attacks, client-side attacks, session replay attacks, and various session fixation attacks.
### Session Sniffing

The attacker may simply use a sniffer or other tool to capture the session token and look for the token called session ID. After this value has been sniffed, the attacker simply attempts to use this valid token to gain unauthorized access.
### Predictable Session Token ID

>Many web servers use a custom algorithm or predefined pattern to generate session IDs. The greater the predictability of a session token, the weaker it is and the easier it is to predict. 

If the attacker can capture several IDs and analyze the pattern, he may be able to predict the session token ID. For example, suppose you were able to capture one ID and it was as follows:`JSESSIONID =jBEXMZF20137XeM9756`

This may look somewhat secure and sufficiently long. However, if you can capture several session tokens, patterns in their value may become evident, as shown here:

`JSESSIONID =jBEXMZE20137XeM9756;
`JSESSIONID =jBEXMZE20137XeM9757;`
`JSESSIONID =jBEXMZE20137XeM9758;
`JSESSIONID =jBEXMZE20137XeM9759;`
`JSESSIONID =jBEXMZE20137XeM9760;`

Upon discovering this sequence, all an attacker needs to do to steal a user’s accounts is base his attack on the subsequent session tokens as they are created when the user logs in.
### Man-in-the-Middle Attacks

A man-in-the-middle attack occurs when the attacker can get in between the client and server and intercept data being exchanged. This allows the attacker to actively inject packets into the network in an attempt to take over an authenticated connection.
### Client-Side Attacks

* Client-side attacks target the vulnerability of the end users and the exposure of their system. Many websites supply code that the web browser must process. Client￾side attacks can include cross-site scripting (XSS), cross￾site request forgery (CSRF), Trojans, and malicious JavaScript codes.
* XSS enables attackers to inject malicious client-side scripts into the web pages accessed by others. CSRF occurs when the victim is logged in to a legitimate site and a malicious site at the same time. It allows the attacker to exploit the active session the victim has with a trusted site.
### Man-in-the-Browser Attacks

* A man-in-the-browser attack is similar to the previously discussed man-in-the-middle attack. However, the attacker must first infect the victim’s computer with a Trojan. The attacker usually gets the malware onto the victim’s computer through some form of trickery or deceit.
* Because the requests are initiated from the victim’s computer, it is very difficult for the web service to detect that the requests are fake
### Session Replay Attacks

* Session replay attacks allow an attacker to pretend to be an authorized user on an interactive website. The attack is made possible by stealing the user’s session ID; the intruder gains access and the ability to do anything the authorized user can do on the website. 
* The attacker must capture the authentication token and then replay it back to the server so unauthorized access is granted
### Session Fixation Attacks

The session fixation attack works by assigning a fixed session number that the victim is tricked into accepting. The first step is to steal a valid session ID. The attacker then tries to trick the user into authenticating with this ID. Once authenticated, the attacker now has access.
## Preventing Session Hijacking

>There are two main mechanisms for dealing with hijacking problems: **prevention and detection** 

* The main way to protect against hijacking is *encryption*. 
* Preventive measures include limiting connections that can come into the network. Configure your network to reject packets from the Internet that claim to originate from a local address. 
* Using more secure protocols can also be a big help. FTP and Telnet are vulnerable if remote access is required; at least move to SSH or some secure form of Telnet.
# Denial of Service and Distributed Denial of Service

#TODO

/comm