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

The Tor network uses this type of routing by utilizing a system of Tor relays. Tor relays are just servers operated by volunteers around the world, and when you send a request to a website while using Tor, your traffic is typically passed through 3 of these relays (guard, middle, and exit) before it reaches its final destination. Each of these relays is designed such that it only knows about the preceding relay and the next relay in the 3-relay circuit. 

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

In this scenario, Bob doesn't know who wrote the letter, and no intermediary person knows both who the recipient is AND who wrote the letter.


<br>

## Hidden Services












<br> 

## Resources 
- [Tor History](https://www.torproject.org/about/history/)