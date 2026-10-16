Overview

Configured a DNS server using dnsmasq on a Linux-based server environment through Google Qwiklabs. Set up DNS resolution between a client machine and a receiving server, configured domain name mappings, and verified end-to-end DNS functionality by resolving domain names successfully.

Environment
Component	Details
Platform	Google Qwiklabs (Google IT Support Certificate)
Client Machine	eth_cli
Server Machine	eth_srv
DNS Software	dnsmasq
OS	Linux
Objectives
Configure dnsmasq as a DNS server on the receiving server (eth_srv)
Set up DNS resolution so the client (eth_cli) can resolve domain names
Edit dnsmasq configuration files to define DNS settings
Enable debug logging for troubleshooting
Verify DNS functionality by testing domain name resolution from the client
What is DNS?

DNS (Domain Name System) acts as the internet's phone book, it translates human-readable domain names like www.google.com into IP addresses that computers use to communicate. Without DNS, users would need to memorize IP addresses for every website or service they want to reach. Configuring and troubleshooting DNS is one of the most common tasks in IT support.

What is Dnsmasq?

Dnsmasq is a lightweight DNS and DHCP server commonly used on Linux systems. It is widely used in small office and home network environments to provide local DNS resolution and is a standard tool IT support technicians encounter in Linux server administration.

Steps Taken
1. Accessed the Server (eth_srv)

Connected to the receiving server where dnsmasq would be configured.

2. Edited the Dnsmasq Configuration File

Opened the main dnsmasq configuration file for editing:

bash
sudo nano /etc/dnsmasq.conf

Configured key settings inside the file including:

Defined the DNS domain name
Set the local DNS records mapping domain names to IP addresses
Pointed the server to upstream DNS resolvers
Enabled logging for troubleshooting
3. Configured the Client (eth_cli)

Updated the client machine's DNS settings to point to eth_srv as its DNS server so all domain name resolution requests would be handled by the dnsmasq server.

4. Restarted the Dnsmasq Service

Applied the configuration changes by restarting the service:

bash
sudo service dnsmasq restart

Verified the service was running correctly:

bash
sudo service dnsmasq status
5. Tested DNS Resolution

From the client machine (eth_cli), tested that domain names resolved correctly:

bash
nslookup example.com @localhost
ping example.com @localhost

Successful resolution confirmed the DNS configuration was working end to end. ✅

Problem Encountered- Debug Logging Not Enabled
Issue	Debug logging was not enabled by default
Symptom	Could not view detailed DNS query logs for troubleshooting
Cause	The log-queries option was not set in the dnsmasq configuration file
Solution	Added the following lines to /etc/dnsmasq.conf to enable debug logging
bash
# Enable debug logging in dnsmasq.conf
log-queries
log-facility=/var/log/dnsmasq.log

After restarting the service, DNS query logs were visible and confirmed the server was receiving and resolving requests correctly:

bash
# View live DNS logs
sudo tail -f /var/log/dnsmasq.log

Why this matters in real IT support: Debug logging is one of the first things you enable when troubleshooting a DNS server that isn't working correctly. Being able to read DNS logs lets you see exactly which queries are coming in, which are being resolved, and which are failing, making diagnosis significantly faster.

Key Configuration File

/etc/dnsmasq.conf- the main dnsmasq configuration file where all DNS settings are defined.

Commands Used
bash
sudo nano /etc/dnsmasq.conf        # Edit DNS configuration file
sudo service dnsmasq restart       # Restart dnsmasq to apply changes
sudo service dnsmasq status        # Verify service is running
nslookup <domain>                  # Test DNS resolution
ping <domain>                      # Test connectivity using domain name
sudo tail -f /var/log/dnsmasq.log  # View live DNS query logs

What I Learned
How dnsmasq is configured as a lightweight DNS server on Linux
How to edit Linux configuration files to define DNS settings
How client machines are pointed to a local DNS server for resolution
How to restart and verify Linux services using the service command
How to enable debug logging in dnsmasq for troubleshooting
Why DNS logging is critical for diagnosing real world DNS issues
The relationship between DNS client configuration and server configuration
