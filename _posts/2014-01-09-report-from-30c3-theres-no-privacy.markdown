---
title: "Report from 30C3: There's no privacy"
date: 2014-01-09 00:39
comments: true
categories: blog
tags: geek
---

Chaos Communication Congress is the oldest hacker conference in the world and the largest of its kind in Europe. It takes place at the end of each year in Hamburg and brings current research in the field of security, networking and increasingly also politics and other topics related to “hacking” - the unconventional use of ideas, technologies and things around us.

For the past few years, I was always left with the similar impression after coming back from the conference: Our “paranoia " is not paranoid enough; technologies are vulnerable and (rich, big) states increasingly breach our privacy and other rights. This year was no exception, on the contrary: Jacob Appelbaum presented new documents leaked by Edward Snowden, along with technological analysis. In his talk [To Protect and Infect (Part 2)](https://www.youtube.com/watch?v=b0w36GAyZIA), he revealed among other things an NSA-internal “Catalogue of spying technologies and products” they use against their targets. I had a feeling that I was in a dystopian spy novel - that all the conspiracy theories about what the NSA can do are true, and conspiracy theorists lacked the imagination to describe what is actually happening. 

<img src="/images/posts/2014-01-09-report-from-30c3-theres-no-privacy-ccc_by_blinkenarea.org.small.jpg" alt="30C3 entrance, photo by Blinkenarea.org"/>
Photo credit: Blinkenarea.org CC-BY-SA-3.0

Sooner last year, we learned that the NSA is intercepting most of the major Internet services and companies such as Gmail, Yahoo, Microsoft and so on. Some of these parties clearly cooperated with the NSA, in some cases they easily intercepted Internet traffic or traffic between data centers of the company. Many mobile operators had to abandon any hope for the privacy of its customers under a court order, issued by a secret court, which is not under public scrutiny.

]Jacob Appelbaum presented other documents leaked by Snowden) that describe, among other things that the NSA can install malware in the BIOS or in the firmware of your hard drive (such malware survives a full reinstallation of the operating system). In cooperation with the U.S. National Institute of Standards and Technology (NIST), they influenced standardization process and approved a random number generator algorithm that had a NSA backdoor built in. Anyone who wants to sell products that comply with FIPS (a federal security standard) had to implement this algorithm. Some companies, such as RSA used it for several months as a default random number generator in some of their products. RSA was blamed that they were “bribed” by the NSA to have this default setting, which caused several security researchers to boycott the RSA Security Conference and withdraw their papers. The backdoor means that there’s a secret to this algorithm, which allows NSA to predict the numbers generated by the algorithm and guess private encryption keys that were generated using this algorithm. Aris Adamantiadis showed a [proof of concept how this backdoor can be used](http://blog.0xbadc0de.be/archives/155). 

A lot of people thought that NSA is passive during their mass surveillance operation. Although the majority of interception points probably cannot really change the data, another of the NSA program called Quantum Insert “solves” this problem. The NSA controls an unspecified number of routers around the world (including home routers) which allows them to “insert" data into an existing TCP connection. This tool is used to infect the computers with their “uninstallable” spying malware. They can infect a software package you are downloading from the Internet. It is time to start verifying digital signatures of software downloads (and use [HTTPS everywhere](https://www.eff.org/Https-everywhere))...

The NSA also has a special program for installation of hardware "backdoors", which are installed into notebooks and servers between the time they leave the factory and come to you. They are intercepted during transport and modified to include a hardware backdoor. Of course,  I would suspect the NSA to use this technique for really interesting targets, not as a general surveillance tool, but still: This really seems like a story from a bad spy novel, but it seems it’s a reality.

**ATMs, beware!**

NSA is not the only bad guy in the world. Researchers [described a special kind of malware that has been found in several infected ATMs](https://www.youtube.com/watch?v=0c08EYv4N5A). The criminal organization that created it used it to steal bank notes. The method of installation was relatively simple – the thieves cut out a hole in plastic and inserted their own USB key. Then they forced the ATM to reboot from the USB key. When the machine has been infected, they could gain access to a special menu by entering a short secret code on the keypad. This enabled them to see the number of bank notes in each cassette inside the ATM. 

When they wanted to steal the content of one or more cassettes, they had to call “the headquarters” of the organization and say a unique challenge code displayed on the ATM screen. Using a challenge-response algorithm, the HQ told them a unique answer code for withdrawal. This made sure that the headquarters knew who steals from the ATMs and how much. 

The malware is actively developed and reminds me of a bitter taste of the old joke about the pickaxe hackers who “hack” the ATMs.

<img src="/images/posts/2014-01-09-report-from-30c3-theres-no-privacy-30c3lounge_Moritz_Petersen.small.jpg" alt="30C3 lounge, photo by Moritz Petersen"/>
30C3 Lounge, photo credit: Moritz Petersen CC-BY-SA-3.0



**The Year In Crypto**


A [follow up to the last year's talk on developments in cryptography](https://www.youtube.com/watch?v=HJB1mYEZPPA) suggests that Dan J. Bernstein, Nadia Heninger and Tanja Lange started another tradition. And I like it. In “The Year in Crypto” they describe what happened in the field of cryptography. In addition to backdoors in algorithms, they mentioned problems with TLS, random number generators, etc. We learned about the upcoming “cryptocalypse”, which is very likely to be caused by the arrival of quantum computers. At least NSA is trying to build one, and its goal is to break ciphers. What ciphers should be used after some of us upgrade our old Pentiums to quantum computers? Check the recording of this talk online.

We must also praise Google for introducing Perfect Forward Secrecy in their HTTPS configuration and the introduction of encryption between their data centers. We do not know if Google willingly cooperated with the NSA, what we do know is that they are trying to make it more and more difficult for others to spy on the traffic between their servers and their users. 

Perfect Forward Secrecy ensures that even if HTTPS private keys of servers are compromised, this does not allow the attacker to decrypt previously recorded sessions. The keys are used to verify the identity, and the exchange of encryption keys is done by separate instance of asymmetric key exchange algorithm (ECDSA or DSA). In practice, this means that if anyone gets the private key and also has a huge worldwide interception network, they must actively attack each connection (using the so-called  man in the middle attack), passive listening is not enough. Do you think that such an organization does not exist? According to the available information, an e-mail provider Lavabit was forced to disclose their server’s private keys by a secret court order. And coincidentally, the NSA has a worldwide eavesdropping network. I believe that perfect forward secrecy will make it difficult to do untargeted mass interception of innocent people...

**Knock, knock, internet!**

For a couple of geeks like me, it is important to know how many computers on the Internet are live, whether they use encryption and whether they have up to date software. And some of us have dreamed of doing an internet-wide scan to seek answers to their weird geeky questions. Zakir Durumeric of the University of Michigan and his team are the ones who woke up and made their dream a reality. They wrote a  scanner that can do an internet-wide scan in a matter of hours. In this way,  they were able to collect SSL certificates used online and evaluate how many of them use compromised keys. Also, they were able to determine how many computers have vulnerable implementations of UPnP or IPMI. The results can be found in [this talk](https://www.youtube.com/watch?v=2_qQ6mhGNSU), or on [zmap.io](http://zmap.io/), but if you have any illusions about Internet security, I recommend breathing deeply before watching the lecture...

**Journalists & whistleblowers**


In addition to technical issues, freedom and politics were main issues. The [keynote was presented by Glen Greenwald](https://www.youtube.com/watch?v=gyA6NZ9C9pM), an independent journalist who publishes Edward Snowden leaks. He talked about the right to privacy and huge impact of the surveillance state. From WikiLeaks,  we could hear Julian Assange (who unfortunately had a crappy video connection – he still cannot leave the Ecuadorian embassy in London) and Sarah Harrison, who according to WikiLeaks saved the life of Edward Snowden when he had to leave Hong Kong suddenly. 

**Malware in your SIM card**


Karsten Nohl [presented new attacks that target SIM cards](https://www.youtube.com/watch?v=pK0ef7iWOuA). The GSM mobile phones have many more processors than most of us think. The main ones are the baseband chip, which handles communication with the mobile network (and attacks on it were presented in [another talk](https://www.youtube.com/watch?v=sD-EXDOoZs4)), application chip (that’s the one that runs the applications and the operating system with which users interact) and SIM card – yes, the SIM card itself can also run stored programs. SIM card can detect your location, turn on your microphone, send data and SMS, etc…

Karsten Nohl presented another attack, which can be used to install spyware (or any other code) to the SIM card. It can, for example, turn on the microphone and call a toll-free number or regularly send your physical location to the attacker.  

By saying “presented” I mean that he showed the attack live on stage using fake GSM network and a phone which he infected on stage.  So this is not a weird academic paper, but a very practical reality. This type of attack is undetectable by the user. Enforcing encryption can prevent the attack. For this reason, Karsten released [GSM Map](http://gsmmap.org/) which maps various security parameters of GSM operators around the world. 

It's no surprise that this "new" attack that was presented at the conference was already being used by the NSA at least since 2008. However, just in case the NSA does not have direct access to the mobile operator, their mercenary hackers simply break in, as one Belgian GSM operator experienced on their own. Who knows what other networks are hacked by the NSA (or other countries, which have no Edward Snowden yet, but still have huge spying and hacking programs).

**Satellite antenna in the backyard**

Travis Godspeed [presented a project of a satellite antenna](https://www.youtube.com/watch?v=ktnQ7nBCuqU), which he built in his backyard. He can track satellites in low earth orbit and record what they transmit. Unlike the satellites in geostationary orbit, these are moving around and the antenna has to be rotated to follow the satellite. At first we envied the amount of free time Travis had, but I have to admit I would love to play with such a thing that not many people can have hands-on experience with. 

**Bitcoin Trezor**


In 2013,  Bitcoin – a decentralized alternative currency – gained even more popularity, the exchange rate (or value) increased, and more general acceptance followed. Unfortunately, the Congress did not follow this trend – you could not buy tickets with Bitcoins, pay for food or T-Shirts. Some hackerspaces accepted it, and you could use it to pay for some nerdy stuff like electronics kits, etc.  

The [only Bitcoin-related talk](https://www.youtube.com/watch?v=CgaBKNus1n0) was by my friend Pavol Rusnák, who presented his project [Bitcoin Trezor](http://www.bitcointrezor.com/). It allows secure storage of Bitcoins even when your computer can be infected with malware. If you have any Bitcoins, I recommend looking at this project. Many people got infected or hacked, and their Bitcoins were stolen.

**Ztohoven**


Czech art group Ztohoven (with my help) presented its three projects - Media Reality (atomic mushroom in a live broadcast of Czech public television), Citizen K. (exchange of identities) and Moral Reform - drama for parliament, government, the president and journalists. Watch it, it’s cool!

<iframe width="560" height="315" src="//www.youtube-nocookie.com/embed/hBxeSmBBdfg?rel=0" frameborder="0" allowfullscreen></iframe>

**The Venue**

Hacking is not just playing with computers or soldering iron. The lounge presented bands that are close to the hacker culture. On the top floor,  there were several places where you could prepare coffee in different ways (for example you could use the bike-powered grinder). If you wanted to communicate with someone, it was possible to use the internal telephone network. However, if by communication you rather mean a message in a bottle, you could use pneumatic tube mail that was all in and around the building. 

Check it out: 
<iframe width="560" height="315" src="//www.youtube-nocookie.com/embed/vfIq_XId490?rel=0" frameborder="0" allowfullscreen></iframe>

**Conclusion**

Chaos Communication Congress has traditionally been the place to meet hackers, artists, cryptology and security experts and developers. All lectures are streamed live, so in addition to the direct participants, there were hundreds of people watching around the world, mainly from hackerspaces that organized viewing parties. If you missed the opportunity to see the presentations live, [recordings are available](http://media.ccc.de/browse/congress/2013/). I hope you could join us next year, it’s a remarkable experience.

