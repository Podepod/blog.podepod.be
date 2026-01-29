+++
date = '2026-01-27T12:13:42Z'
draft = true
title = 'Hosting Gameservers for My Friends'
author = 'Podepod'
tldr = "Some research I've done to make it easy to host gameservers for my friends"
tags = ['research','games','hosting']
+++

## Some History

My interest in tech and IT started with hosting a simple game server for me and my friends to play together. Also an interest in how electronics work. So even now, a few years after I started my IT studies, I am still happily hosting games servers for my friends.

I run two basic minecraft survival servers full time for two different groups of friends. These are quite easy to run and more importantly, well documented on how to run them or tweak settings etc. Ofcourse there is also the occasional modded Minecraft server. These servers often come and go as we go through minecraft fases. After that it's fun to go back to a really basic server which is just vanilla minecraft.

But as we discover and play other games, I have hosted servers for other games aswell.

- BeamNG (BeamMP server)
- Terraria
- Eurotruck Simulator 2
- Arma 3 (only once, don't remember much about the experience)
- Factorio
- Satisfactory (Didn't work as good as I expected)
- Tried a FiveM (modded GTA V) server but couldn't get the mods I wanted to work, so I gave up

So to set up these servers I usually used an old PC I had installed some distro of Linux on, opened a port on the firewall of my home network and called it a day.
After a while, the ports open on my firewall were more then I would like because of course after we stopped playing on the server, I would shut down the server. But I forgot to remove the port forwarding rule on the firewall.

To avoid this, I recently started renting a VPS from Hetzner. This was something new because I never rented a server before. It is very interesting to see how it all works and I'm thinking about renting a dedicated server from them aswell... But for the moment that's besides the point. I'm hosting a lot of my services for personal use on this cloud server which was easier than I thought it would be. I'm also hosting those Minecraft servers and other game servers on it. Which still poses the same issues. There is still (a virtual) firewall where I need to setup all the port forwarding. And most important of all, I still need to do the cleanup of those portforwarding rules...

## Panel Software

I'm now looking at [Cubecoders AMP ](https://cubecoders.com/AMP) for this. As I found in the documentation AMP also controls the local firewall on the linux host. So I could use one host as a gameserver only, so no other content is on there, and open up a few ports with portforwarding and block those on the local firewall. In a way this would make the part of cleaning up a lot easier because AMP should do that for you when you remove a server. But I'm still figuring out if this is better security wise...

Also the AMP software works with licenses. Which I don't mind (mostly because it's a lifetime license and honestly they're quite cheap). I could also give my friends access to the panel so they could make and start their own servers. I'm not sure if that's a good idea, but it's an option which is nice.

### AMP licenses

For the license options there are three:

Standard edition:
- Costs 9 Euros
- You can deploy a single server and host max 5 gameserver instances on it.
- If I decide to give panel access to my friends, there are only three panel users available (so only two friends can use the panel)
- A good option, but I think the 5 instances limit will come to bite me

Professional edition:
- Costs 19 Euros
- Multiple servers can be deployed with a maximum of 15 instances accross the servers.
- This edition has unlimited panel users includes, so there is no problem anymore.
- This probably is the edition I need. The chance that I stick with just one server is quite big, but 15 instances at once should be enough

Advanced edition:
- Costs 38 Euros
- 50 instances limit
- All functionality the professional edition has
- Custom branding (own look to the panel, also display your own logo etc.)
- Centralized authentication
- Deployment templates
- The last three functions are for my usecase totally unnecessary, but kind of cool and they give me fun options for the future.

The point is, I don't actually need the Advanced edition right now (and probably ever). But it could be the start of some other cool projects in the future, like setting up a centralized authentication server for personal use, trying to figure out the deployment templates, ... 

But it costs a bit more, nothing major, but still to be taken into consideration. I could still just not buy a license and host all of those servers myself with a bit more work than just a few clicks. It still is interesting to see what's out there as an alternative to manually setting up these servers.

## Conclusion

I will keep hosting gameservers for my friends and I to play on. I'll try out the [Cubecoders AMP ](https://cubecoders.com/AMP) panel software to try and make it easier for me to setup those servers or even allow my friends to set up their own servers but I still don't know which license I'll buy.
