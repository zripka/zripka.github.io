# My notes for the git bash colours post

- take a screenshot of that bash script I wrote the other day
- the comments and other stuff, like what comes after the shebang is just awful, it's almost impossible to see and I'm not even colourblind as far as I know.
- I want to make the font a bit bigger and make the colour scheme less horrible to look at - how?
- started by looking at Alan P. Barber's [post](https://alanbarber.com/post/how-to-customize-the-git-for-windows-bash-shell-prompt/)
- in windows file explorer, go to `C:\Program Files\Git\etc\profile.d\git-prompt.sh` and open it up with Notepad++ or similar
- I mean, it probably makes more sense to open it with vim within the git bash shell
- take a screenshot of the above file within vim to show what the file looks like and also show off how bad my current font & colour scheme is (the default git bash)
- it's like reading the fine print on a medication bottle, is this what we're supposed to look at all day?
- okay what does this say
- there are some things in here I don't understand - why does the second conditional check if the file it's in exist, and then run itself? wouldn't that create an infinite loop?
- that being said, this looks pretty simple. Overall it's like, mainly just assigning values to environment variables as far as I can tell.
- some stuff in Alan Barber's post I don't care that much about but I'll do it anyway so I got rid of the 'MINGW64' that appears in every prompt by deleting `PS1="$PS1"'\[\033[35m\]' # change to purple
PS1="$PS1"'$MSYSTEM ' # show MSYSTEM`
- okay, before I try to change the colours I decided to just change the prompt text. When I tried to save, nothing happened; vim gave me the message Can't open file for writing
- this is tricky. I don't have permission to write to the file, so I tried to use chmod to give myself permission, but I also don't have permission to change permissions on the file. Finally, there's no sudo command installed in git bash, so I can't use it for chmod or to directly write to the git-prompt.sh file. Maybe that's why Alan Barber says to use Notepad++, because of the permissions regime.
- installing sudo on git bash looks hacky and a time suck so I'm skipping it. Back to Notepad++
- Even Notepad++ makes a point of saying that I'm not allowed to edit this, though the workaround comes when it asks to open in Administrator mode. You can see in Alan Barber's screenshots that their Notepad++ is also in Administrator mode, though they left it out of the instructions, which feels to me like an important omission. 
- okay I saved it and still nothing. Just realized what's up with that weird loop - it's looking for some other file that also could contain this kind of config. I'm just going to comment that out for the time being.
- got it going. Now that I've gone through this process, this may not actually be what I want. I don't mind the shell type stuff honestly, except maybe the font could be a bit bigger. It's really while I'm editing inside of Vim that's the issue. Maybe that's more of a Vim config thing than a git bash config thing. Hmm.
- Thanks to Alan P. Barber for the post!
