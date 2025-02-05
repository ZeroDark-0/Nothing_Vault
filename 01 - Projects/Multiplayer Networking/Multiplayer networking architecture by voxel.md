---
date: 2025-02-06T00:18
tags: 
link: https://youtu.be/EFzFHrzIiz8?si=O4fKG5vzfI9sd9Xa
cssclasses:
  - center-images
---

The usual way to connect in multiplayer is to connect through Server, but the problem here is the latency and ping issue. 
Playing Co-op, the action did by the player have to go to the server and then deliver to the different player.

![[2-Multiplayer networking architecture.png]]

But for that we can use the Peer 2 Peer method to directly connect to the player and the issue here is the IP address is exposed to each other.

To prevent that we use the Relay method- 

![[3-Multiplayer networking architecture.png]]

## <code style="color:blue">How it works</code>

Here a Lobby, 
why to use this hassle system - this can help you to reduce the lag and no IP address is shared ..
but a lobby can host multiple relay...[[ED-202502060042.excalidraw]]
