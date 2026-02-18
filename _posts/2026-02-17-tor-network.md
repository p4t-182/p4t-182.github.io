---
layout: post
title: How does Tor work?
date: 2026-02-17
---

## What is Tor?

<figure style="text-align:center;">
  <img src="https://upload.wikimedia.org/wikipedia/commons/1/15/Tor-logo-2011-flat.svg" alt="Tor browser" style="display:block; margin:auto;">
  <figcaption style="margin-top:8px; font-size:0.9em; color:#555;">
    Image credit: Wikipedia
  </figcaption>
</figure>


Tor, also known as the 'Onion Router', is a free, open-source network used for anonymous communication. It was [created](https://www.torproject.org/about/history/) in the 90s when online privacy was becoming a concern and the idea was to find a way to hide the identities of users communicating over the internet. 

I've always treated Tor as sort of a black box, however at a fundamental level it's fairly easy to understand and the subsequent sections of this page will be my attempt at breaking it down as simply as possible at a high level. 

<br>





## Onion Routing

The fundamental mechanics of the Tor network are based on a concept called onion routing (hence the 'Onion Router'). Essentially onion routing wraps data in multiple layers of encryption. Your data is passed through several other nodes before reaching its destination, and at each node a layer of encryption is peeled back like an onion. When the data reaches its final destination, all layers of encryption have been peeled back. 

The Tor network uses this type of routing by utilizing a system of Tor relays. Tor relays are just servers operated by volunteers around the world, and when you send a request to a website while using Tor, your traffic is typically passed through 3 of these relays (guard, middle, and exit) before it reaches its final destination. The exit relay is the final relay in the circuit, and it decrypts your traffic and forwards it to the open internet. Each of these relays is designed such that it only knows about the preceding relay and the next relay in the 3-relay circuit. 

<figure style="text-align:center;">
  <img src="https://cdn.arstechnica.net/wp-content/uploads/2014/01/tor-structure.jpg" alt="Tor relay circuit" style="display:block; margin:auto;">
  <figcaption style="margin-top:8px; font-size:0.9em; color:#555;">
    The Tor relay circuit structure
  </figcaption>
</figure>


In this way, data sent to a website over the Tor network remains encrypted until it leaves the final relay into the open internet to its final destination. This provides anonymity to users because the user's IP address is never actually revealed to the destination site, and no single node knows both the source IP and destination of the user's data.

### An analogy
Here's a common analogy: imagine Alice is simply trying to give a letter to Bob in a crowded room. Alice takes the letter, places it in an envelope, and writes Bob's name on it. She then does the following in this order: 

1. Alice puts the envelope in another envelope with Person C's name on it.
2. This envelope then goes into another envelope with Person B's name on it.
3. Finally, the resulting envelope goes into a final envelope with Person A's name on it. 

She then gives the envelope to Person A, who opens the outer envelope. Person A sees Person B's name on the resulting envelope, and so Person A passes it to Person B.

Person B sees Person C's name on the resulting envelope, and so Person B passes it to Person C.

Person C opens the outer envelope and sees Bob's name on the resulting envelope. Finally, person C gives the envelope to Bob and he reads Alice's message. 

In this scenario, Bob doesn't know who wrote the letter, no intermediary person knows both who the recipient is AND who wrote the letter, and each intermediary person opens their respective envelope.


<br>

## Hidden Services

This is where things get a little more interesting. Tor also allows for the use of what are called hidden services. A hidden service is basically a server that operates strictly within the Tor network, and hence can only be accessed using the Tor browser. 


Accessing hidden services using Tor works differently from accessing normal HTTP/HTTPS websites using Tor. Firstly, hidden services generally have long, alphanumeric addresses that are 56 characters long, followed by ".onion". For example, a valid address might look like:


```pg6mmjiyjmcrsslvykfwnntlaru7p5svn6y2ymmju6nubxndf4pscryd.onion```


When a client wants to access this service, they query a Tor hidden service directory (HSDir). This directory acts as a [distributed hash table](https://en.wikipedia.org/wiki/Distributed_hash_table), which returns the queried address' descriptor. The descriptor contains the hidden service's public key and a list of what are called introduction points. You can think of the introduction point as a Tor relay that forwards connection requests from clients to a hidden service without revealing either party’s identity. 

The client then chooses a random Tor relay to act as the rendezvous point. This is the point that will facilitate communication between the client and the hidden service. A 3-hop circuit is then constructed by the client to this point. 

Using the newly constructed circuit, the client can then send the rendezvous point's address along with a one time secret to the hidden service's introduction point. The introduction point forwards this to the hidden service, which creates its own 3-hop circuit to the rendezvous point. The rendezvous point can then verify that the one time secret from the hidden service is correct, and can connect the client's circuit to the hidden service's circuit. It looks something like this:

<figure style="text-align:center;">
  <img src="https://www.axontechnologies.com/images/blog/hidden-services.jpg" alt="Tor relay circuit" style="display:block; margin:auto;">
  <figcaption style="margin-top:8px; font-size:0.9em; color:#555;">
    A very high level representation of a Tor hidden service
  </figcaption>
</figure>

With this system, traffic is anonymized and remains encrypted end-to-end, as the traffic never leaves the Tor network.



## Why is this important?

Privacy is a fundamental human right but in a world that is more connected than ever, it feels as though it is becoming more of a privilege. The Tor project is a light at the end of the tunnel and it is one of the best tools that exists currently to exercise some degree of online privacy. 

Many associate Tor with the use of the dark web and illegal activities, however wanting secrecy does not imply there is something to hide. Tor is relied upon by journalists communicating with sensitive sources, activists organizing under oppressive regimes, whistleblowers exposing corruption, and everyday people who simply want to browse without being tracked, profiled, or surveilled. Through these uses, Tor acts as a safeguard for protecting free expression and online privacy. 

<br> 

## Links 
- [Tor](https://www.torproject.org/)
- [Donate to the Tor Project](https://donate.torproject.org/)