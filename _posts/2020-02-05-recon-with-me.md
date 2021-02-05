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
  
<p align="center">
  <img src="/images/recon/logo.png">
</p>

<p align="center">
  <strong>Subfinder</strong>
</p>

<p align="center">
  <img src="/images/recon/sub1.png">
</p>

Download and install subfinder using the following command

`GO111MODULE=on go get -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder`

Note: Make sure go1.14+ is installed in your system.

To run the tool on any of the Target website , use the following command

`subfinder -d google.com`

<p align="center">
  <img src="/images/recon/sub2.png">
</p>

It was able to fetch more than 50246+ subdomains in a short amount of time.

Then i noticed that we can use `-v` flag to see the verbose output of the sources that are used to enumerate the subdomains.

`subfinder -d google.com -v`

<p align="center">
  <img src="/images/recon/sub3.png">
</p>

Sources like chaos,threatminer,sublist3r,alienvault ,etc,. are being used to enumerate the subdomains of the target. 

In the Subfinder Github Repository it was mentioned that some of the services will not work until you set it up.

<p align="center">
  <img src="/images/recon/sub4.png">
</p>

So i started looking into it to set-up the **config-file** with the API Keys that are mentioned to see what is the **major difference in the results of subdomain**

Navigate to the following directory

`cd .config/subfinder/`

<p align="center">
  <img src="/images/recon/sub5.png">
</p>

`cat config.yaml` to see the config file

<p align="center">
  <img src="/images/recon/sub6.png">
</p>

We can see many of the API Key services are **Empty** , so now are going to fill the necessary API Keys as source for Subdomain Enumeration.

**Note** The below following API Keys are **Free Of Cost** and has a Limited number of request in it.

  * binaryedge
  * censys
  * certspotter
  * chaos
  * dnsdb
  * github
  * passivetotal
  * securitytrails
  * shodan
  * urlscan
  * virustotal
  * zoomeye

**binaryedge** 

**1 :** [Sign up](https://app.binaryedge.io/sign-up) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://app.binaryedge.io/account/api> and give a name to the **TOKEN** and Click on Generate Token.

<p align="center">
  <img src="/images/recon/sub7.png">
</p>

**censys**

**1 :** [Sign up](https://censys.io/register) for a free account, verify the account.

**2 :** Login into the account and Navigate to this URL <https://censys.io/account/api>  and you will be able to get **API ID** and **Secret**

<p align="center">
  <img src="/images/recon/sub8.png">
</p>

**certspotter** 

**1 :** [Sign up](https://sslmate.com/signup?for=certspotter_api) for a free account.

**2 :** Login into the account and Navigate to this URL <https://sslmate.com/account/api_credentials> and you will be able to get the **API Key**

<p align="center">
  <img src="/images/recon/sub9.png">
</p>

**chaos**

**1 :** Navigate to this URL <https://chaos.projectdiscovery.io/#/> 

**2 :** Early access is provided basis on signup and queue and Invite are send out Weekly basis.

**3 :** Contributor access is Provided on the basis of **PR** that is done under `github.com/projectdiscovery/*`.

<p align="center">
  <img src="/images/recon/sub10.png">
</p>
