---
layout: post
title: Demystifying Insecure Deserialisation on JSF Application
date: 2021-05-08
summary: JSF Viewstate Deserialisation
categories: Web Security
tags: [Bugs, Write-Ups, Web Security]
---

Hi Everyone,

In this blog, we will see about one of the interesting vulnerability **Insecure Deserialisation on JSF Application** which occurs due to the **misconfigured viewstate**

<p align="center">
  <img src="/images/deserialisation/desc1.png">
</p>

<p align="center"> <strong>Difference between Serialization & Deserialization:</strong></p>

* Serialization is the process of taking an object and translating it into plaintext. This plaintext can then be encrypted or signed, as well as simply used the way it is.

* The **reverse** process is called **deserialization**, i.e. when the plaintext is converted back to an object.

<p align="center">
  <img src="/images/deserialisation/desc2.png">
</p>

<p align="center"> <strong>ViewState</strong></p>

* The purpose of “ViewState” is to memorize the state of the user, even after numerous HTTP queries (stateless protocol).
* Different Types of View-state
  1. .Net - ``___Viewstate``
  2. JSF - ``javax.faces.Viewstate``    

<p align="center"> <strong>Flow of JSF ViewState</strong></p>

* The "ViewState" of a page is by default, stored in a hidden form field in the web page named **javax.faces.ViewState**.
* ViewState starts with **H4sIAAAA**, which represent the Base64Gzip.

<p align="center">
  <img src="/images/deserialisation/desc3.png">
</p>

<p align="center">
  <img src="/images/deserialisation/desc4.png">
</p>

<p align="center"> <strong>Layers in JSF Viewstate</strong></p>

<p align="center">
  <img src="/images/deserialisation/desc5.png">
</p>

<p align="center"><strong>Environment Setup</strong></p>

Step 1: Create a Docker Compose file using the following command 

`docker-compose.yml`

```bash
version: '2'
services:
  web:
    image: vulhub/mojarra:2.1.28
    ports:
      - "8080:8080"
```

Step 2: Execute the following command to start a JSF application which using JDK7u21 and Mojarra 2.1.28

```bash
docker-compose up -d
```
<p align="center">
  <img src="/images/deserialisation/desc6.png">
</p>

Step 3: After the application is started, visit http://127.0.0.1:8080 to see the demo page.

<p align="center">
  <img src="/images/deserialisation/desc7.png">
</p>

<p align="center"><strong>Decoding JSF Viewstate</strong></p>

Step 1: Open the Demo URL http://127.0.0.1:8080 , give a sample input and intercept the request using Client-Side Proxy such as Burpsuite as shown below.

<p align="center">
  <img src="/images/deserialisation/desc8.png">
</p>

Step 2: In the request body, it can be observed that the application uses JSF Viewstate format.

<p align="center">
  <img src="/images/deserialisation/desc9.png">
</p>

Step 3: Select the **javax.faces.ViewState** values , right click & send it to **Decoder** as shown below.

<p align="center">
  <img src="/images/deserialisation/desc10.png">
</p>

Step 4: First do a **URL Decode** -> **Base64 Decode** -> **GZip Decode**.

<p align="center">
  <img src="/images/deserialisation/desc11.png">
</p>

Step 5: The final output gives some information about the java utils and components used in the application.

<p align="center">
  <img src="/images/deserialisation/desc12.png">
</p>
