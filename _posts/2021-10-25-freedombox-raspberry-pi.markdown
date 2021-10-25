---
layout: post
title: "Running a Freedombox on a Raspberry Pi"
date: 2021-10-25 18:00:00 -0400
---

_(Last updated October 25th, 2021)_

Freedombox is "a private server for non-experts." In 2021, it doesn't take a lot of imagination to think up some reasons that regular people might prefer to keep their data close to home. [Freedombox](https://www.freedombox.org/), a part of the free and open source Debian universe, lets you do just that. After you install Freedombox onto any single-board computer and connect it to your home router, you can use it to host your own voice conference calls, transfer files without using Google Drive or Dropbox, host your own chat server, and to do a long [list](https://wiki.debian.org/FreedomBox/Features) of other things.

That's the idea, anyway. I thought I would try it out on the Raspberry Pi I've got so I followed this video tutorial and---bam---it didn't work. No stress, though. I'm playing around with a format for this notebook (which is actually a 'blog,' I just haven't admitted that to myself yet) and likely that will look like me coming back and making edits to this post as I make progress on the Freedombox setup. For now I'll lay out what I've tried so far and in the future I'll include my ~winning formula~.

# First try
In this [video](https://www.youtube.com/watch?v=O-lXmLoxD00), @Geekzone tells us to get together the requisite Raspberry Pi, micro-SD and adapters, power cable, and ethernet cable. The gist is you download the appropriate Freedombox image, flash it onto the micro-SD card (I used BalenaEtcher), and then plug in, _in this order_, the ethernet cable to connect the Raspberry Pi and the router, and then the power cord to turn on the the Raspberry Pi. After that, says the video, we should be able to create our admin account on the newly minted Freedombox by breezing over to freedombox.local and logging right on in. I followed all the steps, but for me at the moment, freedombox.local is a big fat server not found error. So why is that?

My best guess is that I didn't connect the Raspberry Pi to the internet properly before I powered it up. I had only just unplugged the router to make power-plug room and I was impatient so I just hit the figurative button, and even if the router was properly booted up or whatever, the ethernet cable seemed kinda loose when I checked it a few minutes later. Next steps? I'll try re-flashing the Freedombox image and be super careful plugging everything in. If that doesn't work, I found some scary-looking forum posts I'll try to scrounge through next.

| All post updates   |
|--------------------|
| October 25th, 2021 |

