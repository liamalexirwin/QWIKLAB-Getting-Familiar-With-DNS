(OVERVIEW)
Setting up and understanding DNS with dnsmasq in a Linux environment 

(OBJECTIVES)
 To modify existing dnsmasq configuration to adapt it to the DNS needs of your organization and then proceed to verify that it works as expected

(ENVIROMENT)
QWICKLABS | Linux Virtual Machine | Local DNS configuration 

(WHAT I BUILT)
I built a DNS configuration through dnsmasq to conform to the needs of a simulated organization


(COMMANDS)
-ip address show eth_srv
-cat /etc/dnsmasq.d/mycompany.conf
-sudo service dnsmasq status
-sudo service dnsmasq stop
-sudo nano /etc/dnsmasq.d/mycompany.conf
-sudo dnsmasq --test -C /etc/dnsmasq.d/mycompany.conf
-sudo service dnsmasq start
-dig example.com @localhost
-sudo tail /var/log/dnsmasq.log


(PROBLEMS I ENCOUNTERD AND HOW I FIXED THEM)
| Problem with debug logging not being enabled  | didn't stop the dnsmasq service to edit the configuration files in dnsmasq | Stopped the dnsmasq service do i could edit the dnsamasq configuration files to allow debug logging to function |

(WHAT I LEARNED) 
How to configure DNS for a server and client on LInux with dnsmasq
how to run and change configuration files in dnsmasq
The importance of testing setting up DNS for an organization in a virtual instance before making changes in production
