---
layout: post
title: "Running a Freedombox on a Raspberry Pi"
date: 2021-10-25 18:00:00 -0400
---

_(Last updated November 3rd, 2021)_

Freedombox is "a private server for non-experts." These days, it's easy to think up some reasons that regular people might prefer to keep their data close to home. [Freedombox](https://www.freedombox.org/), a part of the free and open source Debian universe, lets you do just that (literally, it stays in your house). After you install Freedombox onto any single-board computer and connect it to your home router, you can use it to host your own voice conference calls, transfer files without using Google Drive or Dropbox, host your own chat server, and to do a long [list](https://wiki.debian.org/FreedomBox/Features) of other things.

That's the idea, anyway. I thought I would try it out on the Raspberry Pi I've got so I followed this video [tutorial](https://www.youtube.com/watch?v=O-lXmLoxD00) and---bam---it didn't work. No stress, though. I'm still playing around with a format for this notebook---it's actually a 'blog,' I just won't admit it yet---but likely that's going to look like me coming back and making edits to this post as I make progress on the Freedombox setup. For now I'll lay out what I've tried so far and in the future I'll include my ~winning formula~.

# First try
In this [video](https://www.youtube.com/watch?v=O-lXmLoxD00), @Geekzone tells us to get together the requisite Raspberry Pi, micro-SD and adapters, power cable, and ethernet cable. The gist is you download the appropriate Freedombox image, flash it onto the micro-SD card (I used BalenaEtcher), and then plug in, _in this order_, the ethernet cable to connect the Raspberry Pi and the router, and then the power cord to turn on the the Raspberry Pi. After that, says the video, we should be able to create our admin account on the newly minted Freedombox by breezing over to freedombox.local and logging right on in. I followed all the steps, but for me at the moment, freedombox.local is a big fat server not found error. So why is that?

My best guess is that I didn't connect the Raspberry Pi to the internet properly before I powered it up. I had only just unplugged the router to make power-plug room and I was impatient so I just hit the figurative button, and even if the router was properly booted up or whatever, the ethernet cable seemed kinda loose when I checked it a few minutes later. Next steps? I'll try re-flashing the Freedombox image and be super careful plugging everything in. If that doesn't work, I found some scary-looking forum posts I'll try to scrounge through next.

# Second try: same thing again
I repeated all the same steps from the @Geekzone video just in case I screwed something up. I think it legit doesn't work, though I'm sure it has something to do with the differences in either our networks or our hardware; @Geekzone uses a different Raspberry Pi than me, and it seemed to work fine.

# Third try: Instructions from the Debian wiki
Thanks for nothing, YouTube! (But actually thanks to @Geekzone, I appreciate u). I have to step out of my comfort zone (video tutorials) and follow some steps on the [wiki](https://wiki.debian.org/FreedomBox/Hardware/RaspberryPi4B). Immediately seeing that things are likely more complicated than I first thought. UEFI firmware? Oi. To be honest I'm not even sure what I'm doing, downloading this and using that image to set up the Raspberry Pi, but I'm going with it. Actually no---the wiki says that an alternative is to install Debian on the Raspberry Pi and then get the Freedombox packages up and running. I'm going to try that instead, because that way at least I can get "inside" the Raspberry Pi and have a better idea of what's going on. Using the video tutorial method, basically all I had to go off was literally the flashing little LEDs on the computer board, so this will be an improvement either way.

Damn, as usual, having trouble following instructions because I'm on Windows. `wget` doesn't exist in git bash, or let me not say that---it would be a whole other process of installing it on my machine, etc. I just feel like Bash is so much more fluid and complete on linux. So needless to say I had to go around that part of the instructions.

Ugh! I can't get the debian setup on Raspberry Pi to work headlessly, I can't connect to it whether it's on wifi or directly connected with Ethernet. This is frustrating, I feel like I can't get past step one.

# Finally: this guy's forum post
Punch line: it's working now. I dug through @Jacob's [post](https://discuss.freedombox.org/t/best-way-to-put-freedombox-on-rbpi-4-2gb/323/2) and following his instructions worked. Hell yeah. The steps were pretty similar to what I did before, with some extras.
* flash the image to the micro-sd card
* add a blank file called `ssh` to the root of the boot partition
* use nmap to find the ip of the raspberry pi on my local network
* ssh into the raspberry pi
* expand the file system
* run `sudo apt-get update`, `sudo apt-get upgrade`, and the chunky `sudo DEBIAN_FRONTEND=noninteractive apt-get install freedombox-setup`
* hang on to the string from `sudo cat firstboot-wizard-secret`
* log in to the Freedombox by navigating to the raspberry pi's IP address in your browser and entering the secret string

And so that's great. Step two will be setting up some apps and actually putting the Freedombox to use. Running through this method successfully has made me question the first few tries. Honestly, maybe they didn't fail after all, but only stumbled at the moment of truth---logging in to the Freedombox from the browser. 

What am I saying here? Every time that I tried to set this up prior to the final successful attempt, I always tried to log into the Freedombox by going to `freedombox.local` in my browser, which absolutely did not work. @Jacob skips this entirely and says to just find the IP and use that directly. What if I had used nmap in the first place? The @Geekzone video method might have worked totally fine, and I just never got access to the functional Freedombox because I didn't bother to try its actual IP. Repeating those methods and testing this theory is a job for another day, but I thought it was worth noting.

As I'm getting a little deeper into the documentation relating to this whole question, I'm seeing that Freedombox isn't a super mature project yet. There are hardly any videos online that explain how to set up apps that run on the personal server, let alone resources that help users set up the software in the first place. Hopefully this post, once I've cleaned it up a bit, can add a little bit to that documentation.


| All post updates   |
|--------------------|
| November 3rd, 2021 |
| October 26th, 2021 |
| October 25th, 2021 |

