---
layout: post
title: Recon with Me !!!
date: 2020-02-06
summary: This blog is about automating the process of continuous reconnaissance.
categories: Bug Bounty
tags: [Reconnaissance, Intelligent Automation, Bug Bounty]
---

Hi Everyone 

In this blog , i will cover automating the enumeration part of reconnaissance and finding bugs using it with the following set of tools.

  * Subfinder
  * Chaos
  * Nuclei
  * Httpx
  * Notify
  * Anew
  
<p align="center">
  <img src="/images/recon/logo.png">
</p>

<p align="center">
  <strong>Subfinder</strong>
</p>

<p align="center">
  <img src="/images/recon/sub1.png">
</p>

* Download and install subfinder using the following command

`GO111MODULE=on go get -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder`

Note: Make sure go1.14+ is installed in your system.

* To run the tool on any of the Target website , use the following command

`subfinder -d google.com`

<p align="center">
  <img src="/images/recon/sub2.png">
</p>

* It was able to fetch more than 50246+ subdomains in a short amount of time.

* Then i noticed that we can use `-v` flag to see the verbose output of the sources that are used to enumerate the subdomains.

`subfinder -d google.com -v`

<p align="center">
  <img src="/images/recon/sub3.png">
</p>

* Sources like chaos,threatminer,sublist3r,alienvault ,etc,. are being used to enumerate the subdomains of the target. 

* In the Subfinder Github Repository it was mentioned that some of the services will not work until you set it up.

<p align="center">
  <img src="/images/recon/sub4.png">
</p>

* So i started looking into it to set-up the **config-file** with the API Keys that are mentioned to see what is the **major difference in the results of subdomain**

* Navigate to the following directory

`cd .config/subfinder/`

<p align="center">
  <img src="/images/recon/sub5.png">
</p>

`cat config.yaml` to see the config file

<p align="center">
  <img src="/images/recon/sub6.png">
</p>

* We can see many of the API Key services are **Empty** , so now are going to fill the necessary API Keys as source for Subdomain Enumeration.

**Note** The below following API Keys are **Free Of Cost** and has a Limited number of request in it.

  * binaryedge
  * censys
  * certspotter
  * chaos
  * dnsdb
  * github
  * intelx
  * passivetotal
  * robtex
  * securitytrails
  * shodan
  * spyse
  * urlscan
  * virustotal
  * zoomeye

**Binaryedge** 

**1 :** [Sign up](https://app.binaryedge.io/sign-up) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://app.binaryedge.io/account/api> and give a name to the **TOKEN** and Click on Generate Token.

<p align="center">
  <img src="/images/recon/sub7.png">
</p>

**Censys**

**1 :** [Sign up](https://censys.io/register) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://censys.io/account/api>  and you will be able to get **API ID** and **Secret**

<p align="center">
  <img src="/images/recon/sub8.png">
</p>

**Certspotter** 

**1 :** [Sign up](https://sslmate.com/signup?for=certspotter_api) for a free account.

**2 :** Login into the account and Navigate to this URL <https://sslmate.com/account/api_credentials> and you will be able to get the **API Key**

Note : 100 queries an hour is **free**.

<p align="center">
  <img src="/images/recon/sub9.png">
</p>

**Chaos**

**1 :** Navigate to this URL <https://chaos.projectdiscovery.io/#/> 

**2 :** Early access is provided basis on signup and queue and Invite are send out Weekly basis.

**3 :** Contributor access is Provided on the basis of **PR** that is done under `github.com/projectdiscovery/*`.

<p align="center">
  <img src="/images/recon/sub10.png">
</p>

**DNSdb**

**1 :** [Sign up](https://www.farsightsecurity.com/dnsdb-community-edition/) for a free community account.

**2 :** It will ask for Company Email , use [Temp Email](https://temp-mail.org/).

**3 :** Create an account and verify the email and get the **API Key**. 

Note : It has 30-day renewal (with valid email confirmation)

<p align="center">
  <img src="/images/recon/sub11.png">
</p>

**Github** 

**1 :** [Sign up](https://github.com/join) for a free account, verify the account.

**2 :** Navigate to this URL <https://github.com/settings/tokens> and generate a **Personal access tokens**.

<p align="center">
  <img src="/images/recon/sub12.png">
</p>

**Intelx**

**1 :** [Sign up](https://github.com/join) for a free account, verify the account.

**2 :** Navigate to this URL <https://intelx.io/account?tab=developer> and you will get the **API details**.

Note: Trial 1 week for Free

<p align="center">
  <img src="/images/recon/sub13.png">
</p>

**Passivetotal** 

**1 :** [Sign up](https://community.riskiq.com/home) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://community.riskiq.com/settings>  and you will be able to get **KEY** and **Secret** .

<p align="center">
  <img src="/images/recon/sub14.png">
</p>

**Robtex**

**1 :** Sign in using the google **Gmail Account**

**2 :** Navigate to this URL <https://www.robtex.com/dashboard/> , you will get the **API-Key** details.

<p align="center">
  <img src="/images/recon/sub15.png">
</p>

**Security Trails** 

**1 :** [Sign up](https://securitytrails.com/app/signup) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://securitytrails.com/app/account/credentials>  and you will be able to get **API Key** .

Note : Monthly Quoto is 50 API Requests.

<p align="center">
  <img src="/images/recon/sub16.png">
</p>

**Shodan**

**1 :** [Register](https://account.shodan.io/login) for a shodan account.

**2 :** Login into the account and navigate to this URL <https://account.shodan.io/> , you will get the **API Key** details.

<p align="center">
  <img src="/images/recon/sub17.png">
</p>

**Spyse**

**1 :** [Register](https://spyse.com/user/registration) for a Spyse account and verify it.

**2 :** Login into the account and navigate to this URL <https://spyse.com/user> , you will get the **API Token** details.

Note : It has 100 API Token valid for 5 days during the Trail Period.

<p align="center">
  <img src="/images/recon/sub18.png">
</p>

**UrlScan** 

**1 :** [Sign up](https://urlscan.io/user/signup) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://urlscan.io/user/profile/>  and click on Create new **API Key**.

<p align="center">
  <img src="/images/recon/sub19.png">
</p>

**Virustotal**

**1 :** [Register](https://www.virustotal.com/gui/join-us) for a Virustotal account and verify it.

**2 :** Login into the account and navigate to this URL <https://www.virustotal.com/gui/user/username/apikey> , you will get the **API Key** details.

<p align="center">
  <img src="/images/recon/sub20.png">
</p>

**Zoom Eye**

**1 :** [Register](https://sso.telnet404.com/accounts/register/) for a ZoomEye account and verify it.

**2 :** Login into the account and navigate to this URL <https://www.zoomeye.org/profile> , you will get the **API Key** details.

<p align="center">
  <img src="/images/recon/sub21.png">
</p>

<p align="center">
  <strong>Now the Final Config File Looks Full!!!</strong>
</p>

<p align="center">
  <img src="/images/recon/sub22.png">
</p>

<p align="center">Now Let us compare the Results **Before** and **After** Adding API Keys.</p>

<p align="center">
  <strong>Before API Key</strong>
</p>

<p align="center">
  <img src="/images/recon/sub24.png">
</p>

<p align="center">
  <strong>After API Key</strong>
</p>

<p align="center">
  <img src="/images/recon/sub23.png">
</p>

* From this we can see we got **114817** Addtional subdomains after using **Free** API Keys.

* Only difference is the duration that is taken during the API scan is **slow** than the normal one.

<p align="center">
  <strong>Httpx</strong>
</p>

<p align="center">
  <img src="/images/recon/httpx1.png">
</p>

* Download and install httpx using the following command

`GO111MODULE=on go get -v github.com/projectdiscovery/httpx/cmd/httpx`

Note: Make sure go1.14+ is installed in your system.

* To run this tool against all the hosts and subdomains in hosts.txt and returns URLs running HTTP webserver, use the following command

`cat hosts.txt | httpx`

<p align="center">
  <img src="/images/recon/httpx2.png">
</p>

<p align="center">
  <strong>Nuclei</strong>
</p>

<p align="center">
  <img src="/images/recon/nuclei1.png">
</p>

* Download and install nuclei using the following command

`GO111MODULE=on go get -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei`

Note: Make sure go1.14+ is installed in your system.

* Scanning for misconfiguration on given list of URLs.

`nuclei -l target_urls.txt -t misconfigured-docker.yaml`

<p align="center">
  <img src="/images/recon/nuclei2.png">
</p>

More **Nuclei Templates** can be found here <https://github.com/projectdiscovery/nuclei-templates>.

<p align="center">
  <strong>Notify</strong>
</p>

<p align="center">
  <img src="/images/recon/notify1.png">
</p>

* Download and install nuclei using the following command

`GO111MODULE=on go get -v github.com/projectdiscovery/notify/cmd/notify`

Note: Make sure go1.14+ is installed in your system.

* Notify also supports piping output of any tool and send it over discord/slack channel as notification.

Scan for subdomains, check alive domains and send slack notifications use the following command.

`subfinder -d hackerone.com | httpx | notify`

<p align="center">
  <img src="/images/recon/notify2.png">
</p>

<p align="center">
  <strong>Anew</strong>
</p>

* Download and install this Tool using the following command

`go get -u github.com/tomnomnom/anew`
 
* This tool is used to compare the output with old file and give us what is newly added in the file

For example `domain.txt` contains a set of sub-domains and now `subs.txt` same set of subdomains but included few additional extra new subdomains.

* Using the following command we can compare both the files and get what is newly added.

`cat subs.txt | anew domain.txt`

<p align="center">
  <img src="/images/recon/anew.png">
</p>

<p align="center">
  <strong>Security Through Intelligent Automation</strong>
</p>

* Now by using the above all tools we are going to create a **One Linear** which can find new subdomains , check wheather it is alive or not then scan it with nuclei and send us a slack Notification of the output.

**First Run** 

`subfinder -silent -dL domains.txt | anew subs.txt`

Note : `-dL` - File containing list of domains to enumerate.

**Second Run** 

`while true; do subfinder -dL domains.txt -all | anew subs.txt | httpx | nuclei -t nuclei-templates/ | notify ; sleep 3600; done`

* The **First Run** is madatory for this process so that it will do subdomain enumeration for the list of domains that you give and save it in a `.txt` file.

* The **Second Run** is used to find new subdomains , check alive status , scan it with nuclei templates and notify us the output.

Note : i highly suggest to run these one linear on VPS system like Digital Ocean or AWS instance.

<p align="center">
  <img src="/images/recon/automation.png">
</p>

<p align="center">
  <strong>Why Automation is needed in reconnaissance ?</strong>
</p>

* The chances of getting **duplicates** is **very less** and you will be focusing more on **NEW subdomains**

**For Example**

**Real Scenario**

* I got an alert at 3:54 PM Feb 05, 2020

<p align="center">
  <img src="/images/recon/slack1.png">
</p>

* I reported the vulnerability to the program at 3:59 PM Feb 05, 2020

<p align="center">
  <img src="/images/recon/slack2.png">
</p>

* Reported got Triaged and Valid !!!

Huge Shout out to **[Project Discovery Team](https://projectdiscovery.io/)** for creating Amazing Tools

<p align="center">
  <img src="https://media.giphy.com/media/YVGeZszGz4eC4/giphy.gif">
</p>

Kudos to [tomnomnom](https://github.com/tomnomnom) for anew tool and [pry0cc](https://twitter.com/pry0cc) for the Onelinear.

Thanks a lot for reading !!!.
