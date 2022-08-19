# Web infrustructure & design
# DNS
## DNS -> DOMAIN NAME SYSTEM
### What is DNS??
DNs is the technology that translates human-adapted, text-based domain names into machine adapted, numerical-based IP(addresses).
### How does DNS work?!
### DNS Process from a humans web search perspective:
* a person searches for a wesite with the domain name eg. "address.com"

* the browser checks for stored chache about the domain name in its storage. if none... proceeds to the OS.

* the OS also checks for the domain name "address.com" in its storage to see if there is cached memory about the domain... if none... procees to call the resolver to resolve this situation.

* The resolver is usually an ISP. Resolvers also know where to locate the root server. so the resolver first checks its cache ... when nothing is found the resolver makes a request to the root sever.

* Root servers are DNS namemservers that operate in the root zone. They can directly answer queries for records cached within the root zone. after serching... if none is found it refers the resolver to the (in this case '.com') TLD(top level domain). The resolver also stores the .com TLD address so it doesn't need to ask root again the next time a .com address is requested.

* A TLD represents the first stop after the zone(..where the root was) a tld is simply anything that follows the final dot '.' in the domain name ... in this case 'address.com' -> a '.com' TLD. The TLD responds with the doamin name's ip address or the name servers for the domain name. The name servers are basically sub-domains of the main domain. eg: 'ns1.adddress.com', 'ns2.address.com', 'ns3.address.com', 'ns4.address.com'. ... in this situiation the resolver gets directed to the authoritative servers.

* An Authoritative server is the authority for its zone. It queries and is queried by other name-servers in the DNS. Authoritative servers are the ultimate authority and provide the real ip address to the resolver. for the authoritative sever this ip address is not a cached value. 

* The resolver saves the ip address given by the authoritative server and takes it back to the OS. The OS saves the ip address for the next time such a query/request is made. The resolvers work is done.

* The IP address is then relayed to the browser, which makes a connection to the Computer(server) with the IP adderss, and maes a request for files on that computer. for exaple, the HTML content.

* The user can now browse on this address. 

#### The following were involved in the process above:
* The browser.
* The OS (Operating System).
* The Resolver (ususally ISP).
* The Root server.
* The TLD (Top Level Domain).
* The Authoritative server.


# DNS RECORD TYPES
## A & AAAA Records
### THE A RECORD
The A in 'A records' stands for Address & are the simplest 
types of DNS records. They are one of the primary records used in DNS servers.

#### Exmple of an A-record:
* Domain: address.com
* Host-name: mail
* IP-address: 104.31.2.164

An A record maps a domain name to the IP address (VERSION 4) of the computer hosting the domain. It uses a domain name to find the IP address of a computer connected to the internet.

When you want to visit a site or send an email, you get it...

In order to access a certain website e.g. 'address.com'. At 
the address.com name severs, there's an A record that points 
to the ip address [104.31.2.164] i.e. the request from your 
browser to address.com is re-directed to the servers [104.31.2.164] 
and is able to connect.

#### what can you do with A records

* use multiple A-records for the same domain to provide redundancy and fallbacks.
* In a case where multiple names point to the same address, each would have its own A-record pointing to the same ip address.

#### Querying A-records
* use `dig` to determine the A record associated to a domain name:
e.g. `dig A address.com`


### THE AAAA-record
They are also reffered to as quad-A records.

The AAAA record is used to map a domain name to the IP address
(Version 6 i.e IPv6) of the computer hosing the domain. It is similar t the A-record.

AAAA record are used to find the IP address of a computer 
connected to the internet from a name.

###### some interesting thing's about IPv6:
An IPv6 address would look something like: [2001:0db8:85a3:0000:0000:8a2e:0370:7334]

* They were developed after realizing that the world would eventually run out of IPv4 addresses.
* They are long and are made up of astronomical number of unique addresses. 
* Due to their complexity, there won't be a shortage of supply for a long time.
* The development of this new address type is what brought forth a new record type to support it hence the AAAA-records(quad-A records).

### CNAME record
CNAME is an abbriviation for Canonical Name records.
They are also Known as alias records.
CNAME recods point a hostname to another hostname or FQDN (Fully qualified Domain Name).

* These records are typically used to point multiple hosts to a single location, without having to specifically assign an
A record to each hostname.
e.g: If you moved your blog from `blog.example.com` to `news.example.com` you would use a CNAME record. 

* The can also be used to point a hostname to another domanin or external hostname.

When a namserver looks up a name and finds a CNAME record, it replaces the name with the canonical name i.e the target of
the CNAME, and looks up the new name.

##### Limitations of the CNAME record:
* Only use a CNAME if there are no other records for that hostname.
* CNAME records cannot be used for a root record.















# Monitoring


# Web Server


# Network Basics


# Load Balancer


# Server


# what is a database


# Difference between a web server and an app server.


# DNS RECORD TYPES
<!-- Done -->

# Single point of failure


# how to avoid downtime when deploying new code 


# High availability cluster (active-active/active passive)


# what is HTTPS


# what is firewall






##### links:
* <a href="https://github.com/Iano-theDev/dev-ops/tree/main/web_infr_design">Github README</a>
* <a href="https://twitter.com/Ian_Kamande_W">Twitter</a>
* <a href="https://www.linkedin.com/in/ian-w-kamande/">Linked-in</a>
* <a href="https://medium.com/@sinceianmike">Medium</a>
