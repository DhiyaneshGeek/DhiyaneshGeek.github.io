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


