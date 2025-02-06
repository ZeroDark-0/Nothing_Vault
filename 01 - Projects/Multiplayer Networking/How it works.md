---
links: https://youtu.be/KBBJqPL5-eU?si=zwvtacChmW8YAH6B
date: 2025-02-05T13:00:00
cssclasses:
  - pen-teal
  - center-images
  - center-titles
---
```embed
title: "How Multiplayer Games Work"
image: "https://i.ytimg.com/vi/KBBJqPL5-eU/maxresdefault.jpg"
description: "Learn the fundamentals of how to make online multiplayer games.Crash course in the fundamentals of computer networking and how to make multiplayer games.Fram…"
url: "https://youtu.be/KBBJqPL5-eU?si=zwvtacChmW8YAH6B"
```

## <code style="color:cyan">So, How it Works...</code>


Start off we start this with two type of multiplayer games - Offline games and Online Games

### Offline Games 

It actually like couch co-op or split screen game you can play like maria cart or halo..

### Online Games 

- Client-server -> In this a single server that hosted the game where the player connect and play together.


- Host-> There is another model of this is host model - Where one of the client can access the player.

- Peer to Peer -> this is where every client access the server and response for shared communication. 

### Asynchronous Game

These include Diablo market place like player can sell items to other player. 
Or where players can't communicate with each other also fall in Asynchronous Games.

### <code style="color:yellow">How it can be implemented </code>

Whenever a computer talked to each other on internet or right next to them uses the same protocol communication. 

- The computer use to communicate with each other are called TCP{Transmission communication protocol} and UDP{User datagram protocol}.
Here, the TCP sends the data **slower but reliable but in correct order** on the other hands UDP **sends the data faster but in random order**.
![[3-How it works.png]]

![[5-How it works.png]]

{-------------------------------}{-----------------------------------------------------}
           LAN                                          WAN


In this the IP address works as the street address where the Port address works as the house number.


### Game design >> Game State >> Tick Rate
Tick Rate- 
![[6-How it works.png]]


![[7-How it works.png]]

TCP can be used for smaller platform cuz the random packets delivery but when it comes to the high level like 3D physic or vectors we use UDP.

But the conflict here the order  of the data received using UDP to prevent this we use the buffer system same as when we watch youtube videos (the data that received but not shown to user).

## <code style="color:red">Client-side Prediction</code>
![[8-How it works.png]]

![[9-How it works.png]]

Technically the client side prediction means that the client stimulate the action before receiving the data. This help you in the smoother animation or gameplay environment.

![[10-How it works.png]]

This method may not be a prefect solution cuz sometime it crashes like if client predicted the stimulation of the specific point but later server  deliver the action of that specific point mean for wrong prediction making unstable condition meaning player moving back and forth quickly as that position synchronized to the server state to the client prediction state. And this sometime call rubber banding...

## <code style="color:purple">Remote procedure call (RPC) </code>

It allow to invoke the method on server such as adding a message to the chat log or opening a door.


## <code style="color:orange">Client Authoritative control</code>

If you want a client to move their own player they need to be wait for their command to send to the server and wait for the confirmation from the server side.
To change that we use client authoritative model where the client move their character and then send the command to the server and confirm to the other player.
![[11-How it works.png]]

### This may be ok for the other networking but what about the competitive game

-> All these design pattern are implemented by default networking brain 
As for Unity game engine most popular implementation are Netcode, Mirror, Photon, and Fishnet...
