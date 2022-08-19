# Web infrustructure & design
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

<a href="https://github.com/Iano-theDev/dev-ops/tree/main/web_infr_design">Github README</a>