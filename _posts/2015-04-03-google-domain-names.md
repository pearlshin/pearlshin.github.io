---
title: IP Addresses, Host/Domain Names, and Fixing the 'www' Prefix Issue
layout: post
---

Building my <a href="http://www.pearlsshin.com">personal site</a> was the first time I've dealt with IP addresses, host names, and setting up a domain name. I came across various terms that I didn't understand and needed to learn in order to fix a particular problem I was facing, which is that typing "pearlsshin.com" into the address bar of any browser gave me a "This webpage is not available" error. I needed to add the "www" prefix before the domain in order to reach the address.

I went over a step-by-step process of setting up a Digital Ocean account <a href="http://pearlshin.github.io/2015/03/27/digital-oceans-nginx-devops.html">here</a>. I've purchased my domain name through Google Domain Names so this post will go over some of the basics of some devops through Google Domains and Digital Ocean as well as fixing the prefix issue that I ran into.

Every computer that is connected to the internet has an identity called and <strong>IP Address (Internet Protocol)</strong>. It is comprised of four numbers between 1 and 255 seperated by periods. The first number signifies the main network and the rest of the numbers specify what machine it is. For example, the 22 in "22.231.113.64" specifies what network it is. 

As you can probably imagine, remembering an IP address can be pretty difficult to remember. This is why we have <strong>host names</strong>, which consists of the machine name and the domain name. For example, en.wikipedia.org consists of a local hostname (en) and the domain name (wikipedia.org). When you visit a host name, it is connected to a specific IP address that you are visiting. 

The way we are able to visit a host name as opposed to keeping up with individual machines, apps, or changes in IP addresses and host names is through the <strong>DNS (Domain Name Service)</strong>. What it does is translate IP addresses into hostnames and vice versa. There are various DNS servers around the world ("name servers" that keep track of the mapping between host names and IP addresses. 

For example, if you are visiting www.wikipedia.com, the program is actually contacting your local DNS machine first to get the IP adress that matches the hostname that you provided. 


When you are building a site, you must connect a nameserver to your domain name. Because I bought my domain name through Google and use Digital Ocean as my domain server, I went to my Google Domain registrar and went to the DNS. Then I pointed my name servers to Digital Oceans. You can use their easy-to-follow instructions on how to do that <a href="https://www.digitalocean.com/community/tutorials/how-to-set-up-a-host-name-with-digitalocean">here</a> or skip to the <a href="https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars">Google Domains beta section</a>.

The rest of this post will go over how to fix the prefix issue, or in other words, how to point "www.domainname.com" at "domainname.com" and vice versa. 

**Because Digital Ocean is my name server, the DNS must be configured in Digital Ocean.**

The first thing you must do is set up a <strong>host record</strong> or <strong>A record</strong> for the root example.com domain. Then create a <strong>CNAME record</strong> or <strong>alias</strong> that points to www.example.com at the host record.

A <strong>host record</strong> or <strong>A record</strong> allows you to associates a host with an IPV4 address. For example, you may have the host record for www pointed to 207.46.130.14

The <strong>CNAME (alias)</strong> record is used to associate a host with another host. It works as an alias of the A record that points to a subdomain of an A recod. If the IP address of an A Record changes, the CNAME will follow to that new address. 

Follow the steps bellow to set up a "naked" domain (a domain without the 'www' prefix):<br>


1. Go to the DNS section at the top of the D.O. dashboard.<br>
2. Under 'Domains', click on the magnifying class icon for the domain you want to select.<br>
3. Click 'Add a record'<br>
4. Add 'A' - @ - your IP address<br>
5. Add 'CNAME' - www - yourdomainname.com (must add a trailing period for this to work).


It could take up to 48 hours for the change to take place. 
