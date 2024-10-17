# DIG
(Domain Information Groper) is a command-line tool for querying DNS name servers.
  ### DIG Bind Check 
  Will check the bind version and hostname of server.
      
      $ dig @<Target_IP> version.bind txt chaos 

  ### DIG Name Servers
      
      $ dig <Target_Domain> -t ns

  Will find the IP address of the primary Name server of the Target Domain.
  
      $ dig NS <Target_Domain> @<Target_IP>

  ### DIG Domain Zone Transfer 
  Will attempt Domain Zone Transfer.

    $ dig @<Target_IP> <Target_Domain> -t AXFR


  ### DIG Mail Servers 
  Will find how many Mail servers are in the domain.

    $ dig MX <Target_Domain> @<Target_IP>

  ### DIG Search for A Records & Subdomains 
  Will search for how many A records and subdomains.
   
    $ dig axfr <Target_Domain> @<Target IP>

  Will display DNS Key ID of the Key signing for the Domain.

    $ dig DNSKEY <Target_Domain>=multiline @<Target_IP>
https://www.kali.org/tools/bind9/#dig
 
# DNS Enumeration (Metasploit) 

    > use auxillary/gather/enum_dns
    > set DOMAIN <Target_Domain>
 
# Dnsenum 
DNSEnum is a command-line tool that automatically identifies basic DNS records such as MX, mail exchange servers, NS, domain name servers, or A—the address record for a domain.

    $ dnsenum <Target_Domain> 

https://tools.kali.org/tools/dnsenum 

# Dnstracer
Dnstracer determines where a given Domain Name Server (DNS) gets its information from for a given hostname, and follows the chain of DNS servers back to the authoritative answer.

    $ dnstracer -r 3 -v <Target_Domain> 

https://tools.kali.org/tools/dnstracer 

# Dnsrecon
Scan a domain (-d example.com), use a dictionary to brute force hostnames (-D /usr/share/wordlists/dnsmap.txt), do a standard scan (-t std), and save the output to a file (–xml dnsrecon.xml).

    $ dnsrecon -d <Target_Domain> -t axfr

https://www.kali.org/tools/dnsrecon/

# Host
DNS utility lookup tool.

    root@kali:~# host -h
    Usage: host [-aCdilrTvVw] [-c class] [-N ndots] [-t type] [-W time] [-R number] [-m flag] [-p port] hostname [server]
           -a is equivalent to -v -t ANY
           -A is like -a but omits RRSIG, NSEC, NSEC3
           -c specifies query class for non-IN data
           -C compares SOA records on authoritative nameservers
           -d is equivalent to -v
           -l lists all hosts in a domain, using AXFR
           -m set memory debugging flag (trace|record|usage)
           -N changes the number of dots allowed before root lookup is done
           -p specifies the port on the server to query
           -r disables recursive processing
           -R specifies number of retries for UDP packets
           -s a SERVFAIL response should stop query
           -t specifies the query type
           -T enables TCP/IP mode
           -U enables UDP mode
           -v enables verbose output
           -V print version number and exit
           -w specifies to wait forever for a reply
           -W specifies how long to wait for a reply
           -4 use IPv4 query transport only
           -6 use IPv6 query transport only
           
   Examples:
   
          $ host -T axfr <Target_Domain>
          $ host -t ns <Target_Domain>
          $ host -l <Target_Domain> <DNS Server>
          $ host –l <DNS Zone to transfer to> <Target_Domain>
https://www.kali.org/tools/bind9/#host
 
# Dnsmap 
  Subdomain bruteforcing, it reads an already created file with nmap commands and send those commands to each client connected to it. 
    
    $ dnsmap <Target_Domain> -w usr/share/wordlists/gvit_subdomain_wordlist.txt -r results.txt
    
    $ dnsmap_client -h
    
    $ dnsmap_server -h 

  https://tools.kali.org/information-gathering/dnsmap 

# Nslookup - DNS Query 
  Nslookup is a program to query Internet domain name servers. Nslookup has two modes: interactive and non-interactive.

    $ nslookup <Target_IP>
    
  Ex: $ nslookup [-option] [name | -] [server] 
    
    $ nslookup -q=txt -class=CHAOS version.bind <Target_IP>
    
    $ nslookup -q=txt -class=CHAOS hostname.bind <Target_IP>

Now that we've retrieved a list of DNS servers associated with the target from Whois lookups, we want to query those servers to gain an inventory of potential target machines associated with the given target domains.  

  Using nslookup interactively 

    1. Resolve an individual name or IP address  > (Name or IP)
    2. Use Different DNS server  > server (Server IP or Name)
    3. Say that were interested in all types of records   > set type=any
    4. Perform a zone transfer of all records  > ls -d  <Target_Domain>
    5. Store zone transfer output in a file  > ls -d <Target_Domain> > (Filename)
    6. View File  > view (Filename) 

  https://linux.die.net/man/1/nslookup 

# Sublist3r
  Sublist3r is a python tool designed to enumerate subdomains of websites using OSINT.
    
    $ sublist3r -d <Target_Domain>
    $ sublist3r -d <Target_Domain> -b -p <ports>
    $ sublist3r --v -d <Target_Domain> -p 80,443
    $ sublist3r --v -d <Target_Domain> (Verbose)
https://www.kali.org/tools/sublist3r/
