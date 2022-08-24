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
* CNAME records that are served by DNAME records may cause recursive loops in older resolvers.
* Domains that are used in the SMTP MAIL and RCPT commands may not have a CNAME record.[4] In practice this may work, but can have different behavior with different mail servers, and can have undesired effects.

### MX record
MX record is just simply mail exchanger record.
It specifies the server reponsible for accepting email messages on behalf of a domain name.

All an MX record is is the DNS setting for your email.

It's possble to configure several MX records, typically pointing to an array of mail servers for load balancing and redundancy.


#### How it works...
* when an email is sent via the internet, the sending MTA(mail transfer agent) queries the domain name system for the 
MX records of each recipients domain name.
* This query returns a list of host names of mail exchange servers accespting incoming mail for that domain and their
preferences.
* The sending agent then attempts to establish an SMTP connection, trying the host with the lowest "Priority" value first.
* The system then allows high availability clusters of mail gateways to be built for one domain if neccessary.

~ The MX mechanism doesn't grant the ability to provide mail
service on alternative port numbers, or the ability to diistribute mail delivery accross a set of unequal-priority mail servers by assigning a weighting value to each one.

### TXT record
These are a type of DNS records that contain tect information for sources outside of your domain.

#### How you can use TXT records:
* To verify domain ownership
* To ensure email security:
* * prevent phishing, spamming and other malicious activity


# Monitoring
Software monitoring will watch a computers metrics, record them and emit an alert if something is unusual.

Famous quote in the tech industry: 
"You cannot fix or improve what you cannot measure"

There are two categories of monitoring:
* Application monitoring: getting data about running software and making sure it is behaving as expected.
* Server monitoring: getting data about your vitual or physical sever and making sure they are not overloaded.
(An overload could occur in th CPU, memory, disk or network)


#### Monitoring tools:
There is special software used to help monitor software.
### What do software monitoring tools do.
* CPU: the percentage of CPU should be peaking to its max only rarely, and the peaks should be short.
* Memory: If the indicator is aproaching it's limit it means that it's important to scale your severs horizontally or adding more RAM.
* Storage: its important to be ware of disk utilization in order to avoid crashes.
* Network: Monitoring the network helps to see how traffic is being delivered to your server.  


##### Examples of software monitoring tools:
Here are some examples of monitoring tools:
* NewRelic
* DataDog
* Uptime Robot
* Nagios
* WaveFront

# Web Server
A web server is a software and hardware that uses HTTP(Hyper Text Transfer Protocol) and other protocol to respond to 
client requests made over the world wide web.

A web server displays website content through storing, processing and delivering webpages to users.

Besides HTTP, web servers also support SMTP(Simple Mail Transfer Protocol) and FTP(File Transfer Protocol), used for 
email, file transfer and storage.

# Dynamic vs static web-servers
A static website is one with stable content, where every user 
sees the exact same thing on each individual page.

A dynamic site is one where content is pulled on-the-fly, 
allowing its content to change with the user.

A web server can be used to serve either static or dynamic content.
A static web server will consist of a computer and HTTP 
software. It's concidered static because the server will send 
hosted files as is to a browser.

Dynamic web browsers consist of a web server and other 
software such as an application server and a database . It's 
considered dynamic because the application server can be used 
to update any hosted files before they are sent to a browser.

The web server can generate content when it's requested from 
the database. Though thid process is  more flexible, it's also
more complicated.

### Some uses of web servers
* sending and receiving emails;
* downloading files requested for through FTP.
* Building and publishing webpages.

### Here are some common web servers...
* Apache HTTP sever - free and Open source web server for 
all common OS's and others still 
* Microsoft Internet Information Services (IIS) - for Microsoft/ Not open source
* Nginx - Popular coz of its light resource utlization and 
scalability. Can handle many concurrent sessions due to it's 
event-driven architecture. it can also be used as a proxy 
sever and load server. 
* Lighttpd - comes with FreeBSD OS. Fast and secure consuming low CPU power.
* Sun Java System Web Server - for Sun Microsystems that can 
run on windows, linux and unix. Can handle medium to large websites

#### Choosing a web server
* how well it works with the operating system and other servers; 
* Its ability to handle server-side programming; 
* Security characteristics; 
* Publishing, search engine and site-building tools that come with it.

* Web servers may also have different configurations and set 
default values. To create high performance, a web server, 
high throughput and low latency will help.

# Network Basics


# Load Balancer


# Server


# what is a database


# Difference between a web server and an app server.
### web-servers
* Process HTTP requests by responding with html pages
* Serves static content(html, images, etc)
* No server side programming.
* No database or dynamic generation of html.

### application servers
* Serves business logic to application programs through various protocals.
* Handles all applications operations between users and an organization's backend business
* Deploys applications
#### Parts of Applications server
* web container
* Application client
* EJB container
 - examples of app servers:
    * Apache tomcat
    * Jboss
    * Weblogic
    * WebSphere


# DNS RECORD TYPES
<!-- Done -->

# Single point of failure


# how to avoid downtime when deploying new code 


# High availability cluster (active-active/active passive)


# what is HTTPS
Hyper Text Transfer Protocal Secure.
Its a secure way to send data between a web server and a web browser.
HTTPS is encrypted to increase security of data transefer.
This helps especially when transfering sensitive user data like bank login details, email service etc..

### How HTTPS works
HTTPS uses an encrtption protocol called Transport Layer Security (TLS) formerly Secure Sockets Layer (SSL).
It secures communication by using asymmetric public key infrastructure which uses two different keys to encrypt communications between two parties:
* Private Key: Controlled by the owner of a website. It lives 
on a web server and is used to decrypt information encrypted by the public key.
* Public Key: Available to everyone who wants to interact with the server in a way that's secure. Information that's 
encrypted by the public key can only be decrypted by the private key.

# what is firewall
A firewall is a network security device that monitors 
incoming and outgoing network traffic and permits or blocks 
data packets based on a set security rules.

Its purpose is to establish a barrier between your internal 
network and incoming traffic from external sources (like the 
internet) in order to block malicious traffic like viruses and hackers.

### Types of firewalls
* Packet-filtering firewalls.
* Next-generation firewalls (NGFW).
* Proxy Firewalls.
* Network address translation (NAT) firewall.
* Statefull multiplayer inspection (SMLI) firewalls.

##### links:
* <a href="https://github.com/Iano-theDev/dev-ops/tree/main/web_infr_design">Github README</a>
* <a href="https://twitter.com/Ian_Kamande_W">Twitter</a>
* <a href="https://www.linkedin.com/in/ian-w-kamande/">Linked-in</a>
* <a href="https://medium.com/@sinceianmike">Medium</a>
