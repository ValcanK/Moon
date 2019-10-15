---
layout: post
title: A Red Teamer's Review of OpenSOC CTF
date: 2019-10-14
excerpt: "As a Red Teamer/Penetration Tester it’s not often that I get the opportunity to participate in a Network Defense Simulation style CTF. Typically I’d be the one conducting the network attacks or adversary simulations."
tags: [blue teaming, CTF, incident response, penetration testing, threat hunting, red teaming]
comments: true
---

## The OpenSOC CTF

As a Red Teamer/Penetration Tester it’s not often that I get the opportunity to participate in a Network Defense Simulation style CTF. Typically I’d be the one conducting the network attacks or adversary simulations.

So, what is OpenSOC all about? 
Straight from the [opensoc.io](https://opensoc.io/index.html) website:

> OpenSOC is a challenge meant to teach infosec professionals practical incident response skills in an environment that very closely resembles a real enterprise network. The virtual environment is a scaled down version of almost everything you would find in an enterprise network including workstations, servers, firewalls, email, web browsing, user activity, etc. Simulated users are actually browsing the Internet, downloading files, watching videos, and accessing LAN resources. This creates a high fidelity training environment for unleashing real-world attacks and testing a responder’s ability to filter out the noise and find malicious activity on the network.
The Challenge: 
> 1.	Find the hostile activities 
> 2.	Identify key components of the threats on the network’

As you can see OpenSOC focuses on training and testing the Defender.

So where did I get to play OpenSOC CTF? It’s funny that I even ended up participating in the CTF, I was originally going to the [Texas Cyber Summit](https://www.texascybersummit.org/) to give a talk about [Red Teaming](https://github.com/ValcanK/Presentations/blob/master/Red-Team-Tactics-For-Pentesters_SamuelKimmons.pdf). Typically, when I’m at a conference to give a presentation, I don’t usually take part in any CTFs simply because I like to focus on the upcoming speaking engagement. And to be honest, I’m usually super nervous and am continuously looking over my slides. However, this time around it just so happened that the friends I went to the conference with were Threat Hunters. Once they saw that OpenSOC was going to be there, that became their primary goal. Being curious about the CTF’s style and format I decided to join up.

The CTF ended up consuming 3 days of our lives, we were in the CTF room from 830 AM – 6 PM every day. I have a feeling if the challenges were open over night, I doubt we would’ve slept much. 

OpenSOC’s CTF style was definitely interesting, and deviated from the normal jeopardy CTFs that you’d typically encounter. Instead of presenting all of the possible questions at the beginning, you had to answer a question before moving on to the next one. This way you were forced to put the pieces of the puzzle together, or rather follow the bread crumbs.

I’ll go ahead and say it, I was extremely lucky to be on a team with incredibly talented Threat Hunters ([@josh_murchie](https://twitter.com/josh_murchie), [@onfvp](https://twitter.com/onfvp), [@iHighjynx](https://twitter.com/iHighjynx), [@_WillyMammoth](https://twitter.com/_WillyMammoth)). They were flying through the challenges like they’ve encountered these intrusion sets before. I’m pretty sure most of us on the team had minimal experience with the available tools. As you’ve probably experienced before, if you understand how a similar tool works you can most likely pick up another one pretty quickly.
Here’s a quick look at most of the tools that were available (minus metasploit):
<figure>
    <a href="/assets/img/opensoctools.png"><img src="/assets/img/opensoctools.png"></a>
</figure>

#
Performing investigative analysis wasn’t a foreign concept to me, I was just a bit rusty. After having spent the better part of the last 3 years focusing on primarily Offensive Security, you can probably understand why I’d be a bit out of practice with the defensive aspect. Although I will say that having done multiple Purple Team engagements over the last year definitely helped out.

Ok, back to more information about the CTF. At the beginning there were 3 or 4 intrusion sets/investigations to get through. Each team was presented with a large set of data and a live network. The OpenSOC team did a great job creating what seemed like a real enterprise network. The network consisted of various endpoints, servers, security devices, etc. Not only were there live systems but each endpoint had simulated users generating traffic, which definitely made analyzing network traffic difficult. 

At various points during the investigation we were presented with questions like “Identify the IP and Port being used for C2”. Now looking at that from a Red Team perspective my first thought is to look at commonly used ports for inbound/outbound traffic, i.e. (80, 443, etc.). Of course, finding that data was easier said than done. We ended up having to trace it back to the actual C2 method that the Threat Actor was using. Which brings up one of the other questions 
> “What was the Threat Actor using for Persistence and C2?”. 

Immediately I began thinking 

> “How would I establish persistence and setup C2?”. 

Ideally when setting up persistence you’d want to utilize a function of the target system that is commonly used to execute binaries or scripts when certain actions occur. These actions could be either the system starting up or an action taken by a user. So, if you’re on the other end and attempting to hunt for persistence I would narrow my scope to: Run Keys, startup items, scheduled tasks, and so on. There’re several ways to go about it, but we ended up finding the various persistence and C2 methods by looking at common locations.

When hunting for C2, consider looking at binaries or other things that shouldn’t be making connections outside of the network, such as Rundll32, PowerShell (although there are PowerShell-isms that do occur), MHSTA.exe, and various other LOLbins. 

In addition to hunting for persistence and C2, we had to find various occurrences of lateral movement. Without giving too much information away, just think about what ports and protocols are commonly used in a windows environment. In theory this should be easy to find, because endpoints don’t typically talk to one another. 

After working our way through malicious traffic analysis, SQL injections, lateral movement, persistence, PowerShell Script analysis, and memory forensics we finally completed all 8 intrusion investigations and even reverse engineered a Ransomware attack to decrypt targeted files. Once the dust settled we emerged victorious!
<figure>
    <a href="/assets/img/all.png"><img src="/assets/img/all.png"></a>
</figure>
Overall, I can say that this year’s Texas Cyber Summit was a success!

Some final thoughts: 

OpenSOC was truly an eye-opening event, having the opportunity to work hand-in-hand with Blue Teamers/Threat Hunters really was the most rewarding part. Another big take away for me as a Red Teamer, was the fact that a lot of common attack vectors or TTPs are extremely obvious and leave behind a ton of forensic data. The real lesson here is that you should be monitoring endpoint data for anomalies. Regardless if you’re on the Red or Blue side of security, this training is invaluable!

Once again, I wanted to give a big shout out to my teammates ([@josh_murchie](https://twitter.com/josh_murchie), [@onfvp](https://twitter.com/onfvp), [@iHighjynx](https://twitter.com/iHighjynx), [@_WillyMammoth](https://twitter.com/_WillyMammoth)) and the [OpenSOC](https://twitter.com/Recon_InfoSec) team.


Oh and we walked away with a Texas Cyber Summit Black Badge!
<figure>
    <a href="/assets/img/20191013_140357.jpg"><img src="/assets/img/20191013_140357.jpg"></a>
</figure>
