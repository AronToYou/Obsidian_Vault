# Hierarchy
`www.example.com[.]`
- Root servers
	- responsible for omitted `.` domain
	- Can be asked: Who knows about `.com`?
	- only 1 root zone database
- TLD servers
	- responsible for `.com` domain Registry
	- Can be asked: Who knows about`example.com`?
	- 1 authoritative Registry Operator per domain
		- manages multiple TLD servers
			- all of which maintain the Registry
		- `.com` -> Verisign
		- `.org` -> Public Interest Registry
		- `.de` -> DENIC
- Authoritative servers
	- responsible for `example.com`
- Recursive Resolvers
	- DNS server
		- no permission, authority, etc.
			- could lie, but DNSSEC protects
		- You can run your own
			- BIND
			- PowerDNS
			- Knot DNS
			- Unbound
	- Standard Guidelines by IETF
		- (Internet Engineering Task Force)
	- Operated independently
		- Google Public DNS `8.8.8.8`
		- Cloudflare `1.1.1.1`
		- Quad9 `9.9.9.9`
	- Maintain cache
		- could be outdated
- Registrar
	- authorized to interact with registry for a TLD
		- can submit change requests for domain it manages
	- multiple may exist per TLD Registry
	- Required to have
		- ability to handle WHOIS/RDAP obligations
		- ICANN Accreditation
		- Contracts with relevant Registry operators
- Registry Operator
	- `.com` registry operated by Verisign
## DNS root zone
- Historically coordinated by ICANN
	- (Internet Corporation for Assigned Names and Numbers)
- Technical standards by IETF
	- (Internet Engineering Task Force)
		- DNS protocol
		- DNSSEC validation
		- record & response formats
		- IPv6 DNS records
		- zone transfers
		- caching rules
		- TTL behavior
		- recursive behavior
- Maintained under policies involving
	- ICANN
	- IANA (Internet Assigned Number Authority)
	- root server operators (worldwide)
- 13 root server identities
	- A-root through M-root
	- replicated using anycast routing (hundreds of physical servers worldwide)
## TLD Domains
```
                Verisign
                    │
        Registry Database (.com)
                    │
     ┌──────────────┼──────────────┐
     │              │              │
 TLD Server A   TLD Server B   TLD Server C
     │              │              │
     └──── same authoritative data ┘
```

# Security
- DNSSEC
	- protects against malicious DNS servers who lie
	- signed certificates from Authorities accompany responses

# Registering a Domain
- Purchase domain `{json}myawesomecompany.com` on GoDaddy
- Registrar (GoDaddy) submits registration request to `{json}.com` registry operator (Verisign)
```json
Domain: myawesomecompany.com  
  
Owner: You  
Registrar: GoDaddy  
  
Nameservers:  
	ns1.godaddy.com  
	ns2.godaddy.com
```
- TLD servers are updated
	- "which DNS servers to ask"
```json
myawesomecompany.com
	-> use ns1.godaddy.com  
	-> use ns2.godaddy.com
```
- Authoritative servers are updated (owned by GoDaddy)
	- this creates a DNS zone
```json
myawesomecompany.com. A 203.0.113.15  
www.myawesomecompany.com. A 203.0.113.15  
mail.myawesomecompany.com A 203.0.113.20
```
- Contracts exist between
	- You & Registrar
	- Registrar & Registry
- Trademarks may prevent registering
	- TLDs subject to UDNDRP
		- (Uniform Domain-Name Dispute-Resolution Policy)
# Physical
- Modem
	- mediates connection to WAN
		- translates ISP signals therefrom
		- allows only one connection
- Router
	- creates LAN given an internet connection
	- uses DHCP
## ISP
- often maintain their own Recursive Resolvers
```
Customers
    │
    ▼
Access Network
    │
    ▼
Regional Routers
    │
    ▼
ISP Backbone
    │
 ┌──┴───────┐
 │          │
DNS      Internet
Servers   Peering
 │          │
 ▼          ▼
Resolvers  Other Networks
```
### Path
```
 Browser  
	│  
 OS Cache  
	│  
ISP Resolver  or Google DNS Resolver
	│  
  Root  
	│  
   TLD  
	│  
Authoritative
```

# Fragen
- What is a default gateway
- How many different types of IP addresses can be associated with a device
	- DDNS
		- (Dynamic DNS)
		- links changing IP address to a fixed domain name
		- No-IP or DynDNS