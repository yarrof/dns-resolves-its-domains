# A DNS Server Always Resolves Its Domains

## Story

Your professor started to host an _amazing_ website, but he always forgets the IP address to his machine where he stores the files.

He asked you to help him because he just couldn't memorize that IP address even if his life depended on it.

To solve this problem he went out to register a funny domain name for his website, but he could not do it alone, because he knows next to nothing about DNS and registrars and whatnot... so _again_ he came to you.

Help him to get his own domain name and make his website available over the Internet.

## What are you going to learn?

* How DNS works
* What a domain name registrar is
* How to register a (sub-)domain name for yourself
* What's the different between domains and a subdomains
* What DNS records are
* What kind of DNS records there are
* What A, AAAA and CNAME records are
* What's the result of setting a private vs. a public IP for an A record
* How to verify DNS propagation with online and command-line tools
* How to port forward one or more ports in a router
* Learn about dynamic DNS
* Learn about how to make dynamic DNS work with automated scripts

## Tasks

1. Start and configure a VM with a NAT network adapter.
    - Started a VM loaded and configured with a web- and SSH server (either an existing one or a fresh one using [this image](https://github.com/CodecoolBase/short-admin-vms/releases/latest/download/ubuntu-18.04-www.ova))
    - The VM's Network settings are configured with a single _NAT_ adapter
    - Entering `http://localhost` in a browser on the host machine displays a _nice_ website

2. Register a (sub)domain anywhere you like and configure and make it always point to the local computer.

`<domain>` below should be replaced with the domain you've registered.
    - Registered a (sub)domain at a registrar/service and created an A record for `127.0.0.1`
    - The domain name should contain `local` or something similar (as opposed to `global` or `public`), e.g. <pre>cc<strong>local</strong>test123.example.com</pre>
    - Visiting `https://toolbox.googleapps.com/apps/dig/#A/<domain>` contains `127.0.0.1` in the tool's answer section (below `;ANSWER`) (`nslookup` or `dig` can also be used for verification via the command-line)
    - Visiting `http://<domain>` in a browser on the host machines loads the _nice_ website hosted in the guest VM

3. Register another (sub)domain and set its A record to your public IP address to make the _nice_ website available for everyone on the Internet.

**Note**: only possible to make this work if your ISP assigned you a public IP address.
    - Registered a new (sub)domain and created an A record with your public IP address
    - The domain name should contain `public` or `global` or something similar (as opposed to `local`), e.g. <pre>cc<strong>public</strong>test123.example.com</pre>
    - Visiting `http://<domain>` in a browser _anywhere around the globe_ loads the _nice_ website hosted in the guest VM

4. Since your ISP could frequently change the public IP address it's assigned to you your DNS records could become invalid (meaninig pointing to an IP address which doesn't belong to you anymore). To this end DNS providers most of the time allow you to update the DNS records you've registered with them via scripts/automated tools. This practice is called dynamic DNS.

**Note**: only possible to make this work if your ISP assigned you a public IP address.
    - Created an automation via scripts, `cron` or any other means to dynamically update your public DNS records with your _current_ public IP address

## General requirements

None

## Hints

* You can register free subdomains over at following services (starting with simplest and ending with the most compplex):
  * https://duckdns.org/ - you can register sub-domains under `duckdns.org`
  * https://freedns.afraid.org/ - register sub-domains under various domains
  * https://noip.com/ - they refer to sub-domains as _hostnames_ here, you can register them under various domains
  * https://www.cloudns.net/ - register a new DNS zone under `cloudns.cl` or `cloudns.asia`
* You can use domain name services like the above ones even if you're behind a Carrier-grade NAT, but then use only local IP addresses for A records, like `127.0.0.1` or `192.168.100.23` for example

## Background materials

* <i class="far fa-exclamation"></i> [Introduction to DNS](project/curriculum/materials/pages/networks/introduction-to-dns.md)
* [Dynamic DNS](https://www.youtube.com/watch?v=rOLGvZagdC0)
* [What is `127.0.0.1` or the _loopback_ interface?](https://www.lifewire.com/network-computer-special-ip-address-818385)
