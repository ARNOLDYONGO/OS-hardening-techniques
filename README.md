# OS-hardening-techniques

## Network Protocol involved in the incident
Internet Protocol (IP), Transmission Control Protocol (TCP) and Domain Name System (DNS)

## Documentation of the incident
The DNS & HTTP traffic log file shows the source computer (your.machine.52444) using port 52444 sent a DNS resolution request to the DNS server (dns.google.domain) for the destination URL (yummyrecipesforme.com). Then the reply came back from the DNS server to the source computer with the IP address of the destination URL (203.0.113.22).
The source computer sent a connection request (Flags [S]) from the source computer (your.machine.36086) using port 36086 directly to the destination
(yummyrecipesforme.com.http). The .http suffix is the port number; http is commonly associated with port 80. The reply shows the destination acknowledging it received the connection request (Flags [S.]). The communication between the source and the intended destination continues for about 2 minutes, according to the timestamps between this block
(14:18) and the next DNS resolution request (see below for the 14:20 timestamp).

### TCP Flag codes include:
1) Flags [S] - Connection Start
2) Flags [F] - Connection Finish
3) Flags [P] - Data Push
4) Flags [R] - Connection Reset
5) Flags [.] - Acknowledgment

Then, a sudden change happens in the logs. The traffic is routed from the source computer to the DNS server again using port .52444 (your.machine.52444 > dns.google.domain) to make
another DNS resolution request. This time, the DNS server routes the traffic to a new IP address (192.0.2.172) and its associated URL (greatrecipesforme.com.http). The traffic changes to a route between the source computer and the spoofed website (outgoing traffic: IP your.machine.56378 > greatrecipesforme.com.http and incoming traffic: greatrecipesforme.com.http > IP your.machine.56378). Note that the port number (.56378) on the source computer has changed again when redirected to a new website.

### Remediation for Brute Force Attacks.
1) Requiring strong passwords
2) Enforcing two-factor authentication (2FA)
3) Monitoring login attempts
4) Requiring more frequent password changes
5) Disallowing previous passwords from being used
6) Limiting the number of login attempts

### Resources for more information
1) [An introduction to using tcpdump at the Linux command line](https://opensource.com/article/18/10/introduction-tcpdump): Lists several tcpdump commands with example output. The article describes the data in the output and explains why it is useful.
2) [tcpdump Cheat Sheet](https://www.comparitech.com/net-admin/tcpdump-cheat-sheet/): Lists tcpdump commands, packet capturing options, output options, protocol codes, and filter options.
3) [What is a computer port? | Ports in networking](https://www.cloudflare.com/learning/network-layer/what-is-a-computer-port/): Provides a short list of the most common ports for network traffic and their associated protocols. The article also provides information about ports in general and using firewalls to block ports.
4) [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml): Provides a database of port numbers with their service names, transport protocols, and descriptions.
5) [How to Capture and Analyze Network Traffic with tcpdump](https://geekflare.com/cloud/tcpdump-examples/): Provides several tcpdump commands with example output. Then, the article describes each data element in examples of tcpdump output.
6) [Masterclass – Tcpdump – Interpreting Output](https://packetpushers.net/blog/masterclass-tcpdump-interpreting-output/): Provides a color-coded reference guide to tcpdump output.

*Refer to document*: [tcpdump traffic log](https://docs.google.com/document/d/1cl4kjN-5SsAhld2WgplqeJPSMpToj9ZilHvjmrn3EOY/edit?tab=t.0)
