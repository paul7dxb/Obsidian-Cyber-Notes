[Wireshark THM tutorial](https://tryhackme.com/room/wiresharktrafficanalysis)


ip.src
Show all packets that originate from the specified IP address
`ip.src == 192.168.1.1`

ip.dst
Show all packets that are destined to the specified IP address
`ip.dst == 192.168.1.1`

tcp/udp.port
Show all packets that are sent via the protocol and port specified
`tcp.port == 22 / udp.port == 67`

protocol.request.method
Show all packets that use a specific method of the protocol given. For example, HTTP allows for both a `GET` and `POST` to retrieve and submit data accordingly.
`http.request.method == GET / POST`

==
!=
&&

### Export files
File -> Export files -> choose protocol

# tshark
https://www.wireshark.org/docs/man-pages/tshark.html

https://jsur.in/post/2020-02-19-tshark-cheatsheet
