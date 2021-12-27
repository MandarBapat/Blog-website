---
title: "Botnets"
date: 2021-12-27T16:20:24+05:30
draft: false
toc: true
tags: ["malware", "botnets", "cybersecurity", "DDoS"]
---

## Introduction
This is an introductory article on botnets. I intend to just 'skim' over the topic: explain what botnets are, how they work, the different attacks that they can carry out and prevention and detection methods. My purpose is that the reader becomes aware about botnets. The subtopics being vast in themselves, cannot be covered here and deserve an article of their own.

## Pre-requisites
1. A basic understanding of how devices communicate in **client-server** and **peer-to-peer** forms of communication. This will enable you to imagine how the bots are communicating amongst themselves and also help you to form a mental picture of the bot network.
2. What a **malware** is and its different types. Knowledge about various types of malware and how they spread will help you to understand how new bots are recruited in the botnet.
3. **Denial of Service(DoS)** attacks. If you know how DoS attacks are carried out, you will be able to appreciate why botnets are the weapon of choice for attackers for carrying out DoS attacks.

## So, what are botnets?

### Description
A **botnet** is a network of devices, all infected with some form of malware, that are under the control of a **botmaster**, also called a **bot-herder**. The botmaster issues commands to the bots which in turn carry out the specific task on behalf of the botmaster. The botmaster can be a single person or an organization. As you can see, with millions of bots, botnets provide the botmaster with huge computational power and IP diversity. Its like having an army of computers by your side. Botnets can be used to launch a variety of attacks like **Distributed Denial of Service(DDoS)**, email spamming, key logging and password cracking to name a few.

Does the network of bots consist of some specific devices? Not necessarily. Your device may be a bot too, and you may not even know it! This is why bots are sometimes called as **zombies**. A zombie is a living being, infected with a virus, who is not in control of its own body. Similarly, the owner of the bots do not recognize that their device is being used to carry out malicious tasks.

Botnets are huge in size. They do not contain just hundreds or thousands of devices, but millions of them. The botnet Zeus had about 3.6 million PCs in its network.

Not all botnets are malicious per se. The **Hajime** botnet is a P2P structured botnet. In contrast to other botnets spreading their virus to vulnerable devices, Hajime actually attempts to secure devices by patching their security holes.

### Types
Botnets are classified based on the structure of their network, into 2 categories:

#### Centralized botnets
{{< figureCupper
img="cc_botnet.jpg" 
caption="A centralized botnet. Each bot is connected to some server from where it receives its commands. [Credits](http://www.cs.ucf.edu/~czou/research/P2PBotnets-bookChapter.pdf)." 
command="Resize" 
options="700x" >}}

As you can see from the image, in a centralized botnet, each bot is connected to one or more **Command and Control(C&C)** servers. Such botnets are extremely efficient for the botmasters to issue commands to the bots. The bots take their commands from the C&C servers and carry out the attack. But at the same time, the servers act as a single point of failure, as shutting down the servers will essentially break the botnet.

#### P2P botnets

{{< figureCupper
img="p2p_botnet.jpg" 
caption="A P2P botnet. Each bot is connected to some other bot in the network. Every bot can act as a client or a server. [Credits](http://www.cs.ucf.edu/~czou/research/P2PBotnets-bookChapter.pdf)." 
command="Resize" 
options="700x" >}}

Peer-to-peer networks are generally decentralized, i.e., there is no single central server where the clients request for services. Each node in a P2P network (imagine each device as a node of a graph) is a client as well as a server, depending on the scenario. If node **N** wants a file stored on node **M**, N becomes a client and M acts as a server.

In a P2P botnet, the botmaster can insert the commands at any node of the network. These types of botnets are resilient to the single point of failure defense attacks, as there are no central servers.


## How botnets work and how do they expand in size?

### Working
There are 2 ways in which the botmaster issues commands to the bots:
1. **Pull-based** mechanism - In this mechanism, the botmaster periodically posts commands on a particular location on the network from where the bots retrieve them.
2. **Push-based** mechanism - In this mechanism, the botmaster sends the commands to a certain section of bots. These bots then transfer the commands to other bots.

These mechanisms take a slightly different form in P2P botnets, but the mechanism essentially remains the same.


### Spreading of the infection
This is a high level overview of how botnet expands:
1. A bot in the botnet scans for vulnerable devices on the internet.
2. When it finds one, it tries to inject malware into the vulnerable device. Common methods like **adwares** or **Trojan horses** can come handy.
3. The device becomes infected and becomes a bot.
4. The new device now follows the same procedure from step 1.



## The Attacks
As I mentioned in the first section of this article, the botmaster has several bots at his/her disposal. With many devices, the attacks can be:
1. A **DDoS attack** on a server. - A DDoS attack consists of flooding a server with several malicious or useless requests to such an extent that it becomes unable to respond to requests from genuine users or can even shutdown completely. Bots can come very handy in this attack procedure. Just imagine the amount of traffic you can generate from millions of devices! No wonder botnets are able to bring down the best of the servers!
2. **Cryptocurrency mining** through botnets - You can acquire cryptocurrency by 2 methods: directly **investing** in it like stocks or through **mining**. Mining involves solving complex mathematical problems. The one who is the first to solve it receives a certain amount of cryptocurrency. But mining requires massive computational power. Generally, only people who have access to special hardware and have the necessary resources, engage in mining. With the computational power of a million computers, malicious hackers build botnets to carry out mining of cryptocurrencies.
3. **Generating income through Advertisements** - Most tech giants and other companies earn their revenue through advertisements posted on their websites. The advertising agencies pay these tech companies for bringing users to them and based on the model of payment(like pay-per-click), the companies receive payment from these ad agencies. A botmaster can exploit this. He/she can direct the bots to go and click on the advertisements posted on his/her website and generate revenue.
4. **Brute-force attacks** - A brute force attack from a single computer or a device is often not feasible. But put together a million devices and you can launch a brute-force attack with good success probability. Atleast the vulnerable systems can be breached by such attacks!

There are many more varients of attacks that are possible apart from these.

## Prevention, Detection and Mitigation
It goes without saying that the usual prevention tips like not clicking on suspicious links, having a good antivirus software, installing firewalls and so on, are also useful here. This is because the most basic way to stop the botnet is to stop it from acquiring more vulnerable machines. But are there any sophisticated mitigation methods? If not, can we atleast detect bots in a botnet?

### Detection
Detection of bots in a network works essentially by analyzing network traffic. Once bots are identified, mitigation methods can be used to take down the botnet. Many of the detection methods have now started incorporating **Machine Learning(ML)** and **Deep Learning(DL)** to build intelligent systems that identify bots from network data. It is difficult to describe the methods in full detail here. Hence, I will just describe how some of the detection methods work:
1. Remember the push based mechanism of issuing commands? It is easier to detect bots in this scenario. This is because when the botmaster is issuing commands, a large amount of network traffic is generated which can be easily detected as compared to the pull based mechanism where commands are issued periodically and it is difficult to distinguish normal network traffic from the botnet traffic.
2. ML and DL systems can be trained on normal network traffic. These can be then used to identify deviations from normal data which can point out which devices look suspicious. Similar to how an antivirus is built to detect known **malware signatures** in applications, the detection systems can analyze packets to detect for known botnet signatures.
3. Specifically for P2P botnets, various network traffic parameters can be analyzed to detect malicious hosts. Like **host-living time**. Benign P2P hosts usually have a shorter connection time while a bot in a P2P botnet needs to be connected to atleast one other peer to remain in the botnet and hence their peer connection time is usually long. Similarly, P2P bots have **large number of peers** as compared to normal P2P hosts. Such parameters can be used to point out the bots from benign hosts.

There are several other complex detection methods which are proposed but mostly all of them rely on network traffic analysis.

### Mitigation
Mitigation methods are much more complex to carry out and are also specific. I will list some of the methods with a short description for each:
1. **Index poisoning technique** for mitigating P2P botnets - A number of false entries are fed into the index records. The bots either download a wrong file or not able to search for the required file.
2. **Anti-botnet** - As mentioned in the first section, botnets like Hajime can be used to fix vulnerable systems or break down malicious ones. Methods have been proposed to use a malicious botnets' mechanisms to instead spread an anti-botnet.
3. **Honeypots** - Honeypots are basically devices that are set up so that the botmaster is tricked into acquiring them. The botmaster thinks it is a normal machine and continues its malicious activities through the device while the defenders observe the botnet's attributes. This helps in characterizing the botnet. We can also use these honeypot devices to set up Sybil attacks in P2P botnets.
4. **Sybil attack** on P2P botnets

While these mitigation methods are useful, attackers have also devised counter measures against them. For example, botnets today can detect honeypots.

## References
These are some online articles and research papers that I used:

1. http://www.cs.ucf.edu/~czou/research/P2PBotnets-bookChapter.pdf
2. https://www.mdpi.com/1999-5903/13/8/198/htm
3. https://enterprise.comodo.com/blog/tag/latest-malware-attacks/
4. https://www.pandasecurity.com/en/mediacenter/security/what-is-a-botnet/
5. https://usa.kaspersky.com/resource-center/threats/botnet-attacks
