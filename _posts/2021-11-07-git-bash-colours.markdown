---
layout: post
title: "Editing the shell prompt in Git Bash"
---

Maybe it's just me, but the default fonts and colour schemes in a lot of shell terminals are god awful. I use Git Bash, PuTTY, and CygWin frequently and like, I mean...

![difficult-to-read Vim screenshot](/assets/21-11-07-vim-screenshot.PNG)

Like for real I'll give you five dollars if you can tell me, from a normal reading distance, what the bit after the shebang and the commented line say. I'm not even that colourblind as far as I know and man, that is awful.

I wrote that script the other day using Vim in the CygWin shell. Forgetting which shell was really the culprit, I just spent some time trying out ways to switch the colours and font in Git Bash (whoops!). In the end, the default Git Bash colours aren't too bad, but it still led me down the trail of looking into this kind of config stuff.

![less painful Vim screenshot](/assets/21-11-07-git-vim-screenshot.PNG)

I haven't even actually figured out how to change the Vim font or colours in either shell---likely I'll do another post on that sometime soon. What I _did_ figure out, though, is how to change the shell prompt in Git Bash. Here's how!

# Editing the shell prompt in Git Bash

Oh man, did I just do the recipe website thing where I write 2000 words of preamble before the actual content. Thanks for suffering through it all, here's the real deal.


In Alan P. Barber's [post](https://alanbarber.com/post/how-to-customize-the-git-for-windows-bash-shell-prompt/), they explain that to change the shell prompt in Git Bash, you need to edit the script at `C:\Program Files\Git\etc\profile.d\git-prompt.sh`.

I thought I would be clever and edit it with Vim, since I'm trying to learn it, but it turned into a bit of a nightmare. Git Bash is---at best---a compromise, letting Windows users access Git via the command line without by any means giving the complete Linux experience. My Vim attempt crashed since I don't have permission to edit `git-prompt.sh` or even the permission to _modify_ the permissions with `chmod`, and `sudo` doesn't even exist in Git Bash. Bailed on this idea, needless to say.

In Alan Barber's post, you'll notice the [ADMINISTRATOR] label in the Notepad++ window title. Once you navigate over to the `git-prompt.sh` script in File Explorer and open it up for editing in Notepad++, that's the way that you can get around the permissions issue.

After that it's pretty straightforward. The script itself is only a few lines that set environment variables. For me, to get rid of the glowing purple "MINGW64" at the end of every Git Bash shell prompt, I just had to delete the two lines that say

`PS1="$PS1"'\[\033[35m\]' # change to purple`

`PS1="$PS1"'$MSYSTEM ' # show MSYSTEM`

The end result:

![git bash shell prompt without the "MINGW64" appended](/assets/21-11-07-git-bash-screenshot.PNG)

There are likely some other flexibilities that editing this script opens up, and I'm looking forward to exploring them in the future. Hopefully I'll also get around to solving my original problem, and find a way to use Vim in a shell without feeling like I'm trying to read the fine print on a medicine bottle.
