---
layout: post
title: Living Off The Land - Enumeration
date: 2019-05-18
excerpt: "Enumerating a Target or Network with Living Off The Land Techniques."
tags: [windows, cmd, penetration testing, emulation]
comments: true
---

## The Point

* As a Penetration Tester or Red Team Member and even a Defender, it’s essential that you understand how to use the various capabilities of a system that you’ve gained access to. You may be thinking, I’ll just find a way to get a meterpreter shell on the target. Well I hate to burst your bubble but often times you won’t have that option. If your goal is to remain as quiet as possible then your best bet it to use what’s already available. It may be that you have limited access to the windows command line or an instance of PowerShell. If you’re lucky it will be PowerShell, but once again that’s in a perfect world. Personally, I want to be able to move throughout a system or target environment without getting caught. Often times you won’t have the option to load your tool set on the compromised host.

## In this post I'll be covering various techniques that you can use to conduct Enumeration

* Utilizing various Living Off The Land Techniques, we’re going to learn how to enumerate
as much information as possible about the host we’ve landed on and the target environment.
Enumeration is a key phase in every engagement. As a Pentester, Red Teamer, and
Defender you should be able get the lay of the land.

## Commands for Account Enumeration:

| What we want to find out | Commands |
|:--------|:-------:|
| Who we’re logged in as?  | Whoami |
| What permissions do we have?  | Whoami /priv |
| Can we find out more information about the account?   | Whoami /all or net user "username" |
| What Groups do we belong to?   | Net user "username" |
| What other accounts exist?   | Net users or Net users /domain |
| What users are in certain groups? | net group Administrators or net localgroup Administrators |
|:--------|:-------:|

## Video Walkthrough 

<iframe width="560" height="315" src="https://www.youtube.com/embed/wCd1_2gpZrE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
