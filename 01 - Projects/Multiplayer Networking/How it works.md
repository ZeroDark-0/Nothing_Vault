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
