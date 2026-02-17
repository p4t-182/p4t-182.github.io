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


## Onion Routing

The fundamental mechanics of the Tor network are based on a concept called onion routing (hence the 'Onion Router'). Essentially onion routing wraps data in multiple layers of encryption. Your data is passed through several other nodes before reaching its destination, and at each node a layer of encryption is peeled back like an onion. When the data reaches its final destination, all layers of encryption have been peeled back. 

The Tor network uses this type of routing by utilizing a system of Tor relays. 




## Hidden Services













## Resources 
- https://www.torproject.org/about/history/