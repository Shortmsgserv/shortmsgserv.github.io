---
id: 470
title: An Overview of the Cyber Kill Chain
date: 2019-02-10T22:11:16+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=470
permalink: /an-overview-of-the-cyber-kill-chain/
image: /wp-content/uploads/2019/02/Kill_Chain_Header.png
categories:
  - Uncategorized
---
Kill chain was originally a term used by the US Military to formally identify the steps involved to neutralise a target. There are a few different models of the kill chain but one of the original military ones is Find, Fix, Track, Target, Engage and finally Assess. The cyber kill chain is an attempt to translate this model into cyberspace, allowing defenders to more effectively neutralise cyber threats to their organisation.

The cyber kill chain was originally <a rel="noreferrer noopener" href="https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html" target="_blank">formalised</a> by aerospace and defence company Lockheed Martin and comprises of seven steps; reconnaissance, weaponisation/staging, delivery, exploitation, installation, command and control, actions on objective. It is emphasised that all attackers must go through all stages in the kill chain in order to perform a successful attack and so in an ideal situation an attacker would be stopped at the earliest stage possible and so it is important for defenders to &#8220;shift left&#8221; and stop an attack at the earliest stages of the kill chain as possible.

## Reconnaissance

Reconnaissance can be a difficult stage at which to properly detect the intention of an adversary due to its broad nature. If an attackers reconnaissance consists of more active activities such as port scanning, an organisation may detect a sudden spike in the number of port scans performed on its network and be able to detect and prevent this threat. A major issue is that reconnaissance may consist of more passive Open Source Intelligence (<a rel="noreferrer noopener" aria-label="OSINT (opens in a new tab)" href="https://en.wikipedia.org/wiki/Open-source_intelligence" target="_blank">OSINT</a>) gathering.

It is impossible for an organisation to control all information published about itself and some of this information may not seem immediately useful. For example, if employees have a LinkedIn profile an attacker may use this profile to find out where they sit in an organisation so they are able to launch a spear phishing attack against them.

While there will be exceptions to this rule, a large, well-resourced organisation will usually have the steps to prevent a broad port scan of their network from providing enough information to be of use. A smaller organisation will be unlikely to have the capability to have the same defensive capability. OSINT represents a significant threat to both organisations. Employees are sometimes far too willing to post information on social networks that could be used in a phishing campaign and, if successful, these phishing campaigns can give an attacker significant system access.

### Defending

In order to defend from this stage it is important to only have systems exposed to the wider internet that need to be, so that out of date services cannot be utilised for an attack and configuration data is less likely to be leaked. In order to prevent sensitive data from being leaked to the wider public, an organisation should carefully think about how much information they divulge to their employees.

## Weaponisation/Staging

With the information gained in the reconnaissance stage an attacker will then move onto weaponising what they&#8217;ve learnt, choosing the payload that will affect the target systems. The payload an attacker uses will depend on variables such as their resources, skills and effort as well as the value of a target.

The large number of ready made tools now available that a wannabe hacker can use to exploit a system mean that very little coding knowledge is needed to gain control of a system; one of the most well known of these tools is <a rel="noreferrer noopener" aria-label="Metasploit (opens in a new tab)" href="https://www.metasploit.com" target="_blank">Metasploit</a>. A malicious group may even <a rel="noreferrer noopener" aria-label="pay  (opens in a new tab)" href="https://en.wikipedia.org/wiki/Market_for_zero-day_exploits" target="_blank">pay</a> for an exploit available that is available to purchase; meaning they don&#8217;t have to put in the work.

### Defending

Directly stopping an attacker at this stage is quite difficult as most of the work an attacker will perform at this stage is out of direct sight and control. The focus for defence at this stage should be on preventing future exploitation by ensuring that systems are patched promptly when security flaws are found and for systems that can&#8217;t be patched (a system relies on the software being at that particular version otherwise it won&#8217;t work), ensure that these systems are sandboxed as much as possible so anything exploiting a weakness is confined to that system.

## Delivery

The most common form of delivery for malware is by far email. It is likely that you&#8217;ve received hundreds, if not thousands of emails in the past year encouraging you to open an attachment containing the latest invoice for something or the sales results for whatever. The reason email remains the most popular form of delivery is because it&#8217;s the most successful; with the sheer volume of emails people receive on a daily basis, for most users it becomes hard to decipher which one is genuine and which one isn&#8217;t. 

However, while email is the easiest way for most attackers to deliver their payload for some determined attackers they will use other methods, Stuxnet for me remains one of the most illustrative examples of the lengths some will go to achieve their aims. <a rel="noreferrer noopener" aria-label="Stuxnet (opens in a new tab)" href="https://en.wikipedia.org/wiki/Stuxnet" target="_blank">Stuxnet</a> is a worm that was discovered on a number of computers throughout the world around 2010. Stuxnet&#8217;s aim was to interfere with the programmable logic controllers that just happened to control the centrifuges that Iran used to enrich uranium.

As Natanz, the facility where the centrifuges were located, operated using an <a rel="noreferrer noopener" aria-label="air-gapped (opens in a new tab)" href="https://en.wikipedia.org/wiki/Air_gap_(networking)" target="_blank">air-gapped</a> network it is thought that Stuxnet was delivered physically using USB memory sticks; carried either by unwitting participants or by double agents. Stuxnet is an extreme example, but how many of an organisations employees would pick up a memory stick they&#8217;ve found and plug it into a computer to find out what&#8217;s on it .

### Defending

Making users more aware of possible outcomes from behaviours such as clicking on any file received without checking the sender, or picking up a memory stick and putting it into a computer will certainly help reduce the successful delivery of a payload, but there also remains technical solutions to help reduce the threat. 

A good spam filter will reduce the amount of email a user will receive that they may mistakenly click on and it may well be a good idea to stop the use of memory sticks and have an online based sharing system that will also scan files uploaded for malicious characteristics. Ensuring network firewalls are a good standard will also prevent issues with attackers using Denial-of-Service attacks to bombard a network with data; paired with good anti-virus software running locally on devices will also provide an extra layer of protection.

## Exploitation

Exploitation represents the step in the kill chain where an attacker takes advantage of a weakness in the targets network to compromise them; exploiting a weakness. The weakness the attacker will take advantage of will depend exactly on the targets configuration but could include a <a rel="noreferrer noopener" aria-label="buffer overflow (opens in a new tab)" href="https://en.wikipedia.org/wiki/Buffer_overflow" target="_blank">buffer overflow</a>, <a rel="noreferrer noopener" aria-label="privilege escalation (opens in a new tab)" href="https://en.wikipedia.org/wiki/Privilege_escalation" target="_blank">privilege escalation</a> or a combination of exploits. For attackers with sufficient resources they may even take advantage of previously unknown <a rel="noreferrer noopener" aria-label="zero-day exploits (opens in a new tab)" href="https://en.wikipedia.org/wiki/Zero-day_(computing)" target="_blank">zero-day exploits</a>, with some speculation being that state actors are <a rel="noreferrer noopener" aria-label="hoarding  (opens in a new tab)" href="https://www.wired.com/2015/06/turns-us-launched-zero-day-policy-feb-2010/" target="_blank">hoarding</a> zero-day exploits in case they need to take advantage of them at a later date. Once an attacker has exploited the vulnerability they can will then be able to move onto the next stage; installation.

### Defending

Techniques for defending against exploitation shares characteristics with previous stages, ensuring that systems are patched regularly and isolating systems that are not able to be patched to contain any threat. Other mitigation techniques also include ensuring systems support <a rel="noreferrer noopener" aria-label="executable space protection (opens in a new tab)" href="https://en.wikipedia.org/wiki/Executable_space_protection" target="_blank">executable space protection</a> measures such as DEP as well as considering the implementation of Host-based Intrusion Detection Systems (<a rel="noreferrer noopener" aria-label="HIDS (opens in a new tab)" href="https://en.wikipedia.org/wiki/Host-based_intrusion_detection_system" target="_blank">HIDS</a>). 

## Installation

If a hacker has managed to take advantage of an exploit and has control of a system there is a chance that this control could be lost, say if the exploited system is rebooted. At the installation stage the attacker will install the software they need to quickly and reliably regain control of a system once more. An attacker may wish to gain control of a system, but <a rel="noreferrer noopener" aria-label="wait (opens in a new tab)" href="https://www.bbc.co.uk/news/technology-25087627" target="_blank">wait</a> for a period of time before actually using the system for a task. 

Techniques malicious software might use to prevent detection include modifying the time stamp of files created, making the software seem older than it is; editing registry keys in Windows to ensure the software is started again after a reboot; DLL Hijacking, replacing DLLs with modified versions so that malicious code is disguised.

### Defending

Aside from implementing a HIDS it is important to have anti-virus software with up-to-date definitions installed along with the latest system updates as this will help to detect current installations of malware and prevent others from being installed.  


## Command and Control (C2)

Once the attackers software is installed and persistence is achieved a hacker will be able to command and control a victim into performing the tasks he wants with little chance of being detected. For an attacker to have breached a network, successfully evade detection and gain control of a victim they would usually be classed as an Advanced Persistent Threat (<a rel="noreferrer noopener" aria-label="APT (opens in a new tab)" href="https://en.wikipedia.org/wiki/Advanced_persistent_threat" target="_blank">APT</a>). An APT was originally thought to be a state actor (<a rel="noreferrer noopener" aria-label="APT 1 (opens in a new tab)" href="https://www.fireeye.com/content/dam/fireeye-www/services/pdfs/mandiant-apt1-report.pdf" target="_blank">APT 1</a> is believed to be directed by the Chinese government), but the capabilities of cyber criminals have increased and it is thought some APT <a rel="noreferrer noopener" aria-label="activity (opens in a new tab)" href="https://www.cybereason.com/blog/advanced-persistent-threat-apt" target="_blank">activity</a> is no longer solely conducted by nation states.

### Defending

Defending against threats at the Command and Control Stage can time consuming as if a threat has progressed to this stage there is an increase in the risk of compromise of data integrity or even complete data loss. A proper audit of this breach would likely need the malware in question to undergo an analysis to detect the techniques used to breach defences as well as find attacker motives. 

Detecting the presence of a threat at this stage will involve the use of a Network Intrusion Detection System (NIDS) as malicious traffic is likely to be disguised on a host. In order to prevent the malware communicating with its owner, Access Control Lists will have to be implemented to ensure firewalls; in combination with Network Intrusion Prevention Systems (NIPS), do not let unwanted traffic through.

Some malware may implement kill-switches in its code that can be taken advantage of to shut down an attack. In 2017 Wannacry affected a large number of organisations around the world; freezing systems, encrypting data and demanding users pay a ransom to restore their data. A computer security researcher named <a rel="noreferrer noopener" aria-label="MalwareTech (opens in a new tab)" href="https://twitter.com/malwaretechblog" target="_blank">MalwareTech</a> analysed Wannacry&#8217;s code and found that Wannacry would check a <a rel="noreferrer noopener" aria-label="particular (opens in a new tab)" href="https://www.theverge.com/2017/5/13/15635050/wannacry-ransomware-kill-switch-protect-nhs-attack" target="_blank">particular</a> web address and, if not registered, would carry on encrypting data and spreading to any machine it could. MalwareTech then quickly registered this domain, preventing the further spread of Wannacry.  


## Actions On Objectives

The most serious stage of the kill chain as once an attack has progressed to this stage they work on completing the exercises ultimate aims. For Stuxnet this meant operating the centrifuges at Natanz outside of their operating guidelines causing them to malfunction; for APT 1, the aim was to extract sensitive data. 

### Defending

Defending at this stage will depend on finding out what the aim of the attacker at this stage. If the threat is similar to that of Stuxnet it would be to ensure no further damage to hardware; if it is closer to that of APT 1 then it would be to ensure no further sensitive data is compromised and also finding out what has already been compromised by auditing log files. In order to slow down but still be able to investigate the threat it may be wise to implement a honeypot to distract while an analysis can be performed.  


## Conclusion

Overall the kill chain is a good way to visualise how an attacker will approach a network so that you can take proactive steps to prevent intrusion by thinking like your attacker. A large criticism however is that the kill chain focuses solely on external intrusions and doesn&#8217;t place much thought to what happens once the attacker is inside a network or insider threats. An alternate approach was created by MITRE with their <a rel="noreferrer noopener" href="https://attack.mitre.org" target="_blank">ATT&CK</a> framework and attempts have been made at combining the best of both frameworks with the <a rel="noreferrer noopener" aria-label="Unified Kill Chain (opens in a new tab)" href="https://www.csacademy.nl/images/scripties/2018/Paul_Pols_-_The_Unified_Kill_Chain_1.pdf" target="_blank">Unified Kill Chain</a>.

My conclusions would be that it is always important to be aware of the shortcomings of doggedly following a framework as this may mean important indicators are missed. It is also to always be aware of the frameworks available as this will likely inform your approach to responding to a threat, even if the framework is not formally followed. When presenting a plan to management the cyber kill chain benefits from being simplistic, as it means people who are not involved with the minutiae of cyber security are able to quickly take on board key information.