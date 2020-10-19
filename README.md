# zsh
These are my notes on zsh and starting to use it.  Also I anticipate that I will be writing some plugins and if I do I wanted to make it available to the public.

# Zsh Introduction 

Last week I had a weird second that made me do a little deeper dive than usual. I’m living in the age of Covid-19. It is October 17, 2020, so you can get a mental model of the happenings. I’m a data engineer for a business process organization. So the work I do being in the cloud can be done remotely. I meet with my team on WebX, I get tickets assigned to me to work on.  I code and meet, meet and code, so it’s a collaborative effort centered around code. 

The weird second came about when I needed to add something to my $PATH. 

I tried to do it on the fly and the perfect storm of maybe doing it wrong even for bash and definitely not doing it right for zsh cause my boss who I have tremendous respect for to say, “no that’s not how you do it in zsh but if you type bash in the terminal it will take you back to bash for as long as you have your terminal open and you can do that”. 

So I did it to make my command work and I felt a little embarrassed.  I had caught wind that zsh was coming and was going to be here and my new Mac got here 3 weeks ago and it was there.  Bash doesn’t come installed right away but every time you open the terminal it messaged you to change install it. Having had tons and tons of experience with command line terminal through the years (I’m an 80s kid so that’s a lot of years of different shells.) I had the expectation that it would be intuitive for me to use this new shell. For some reason it wasn’t, maybe it was the experience of having someone that I respect to call me out that put a bad taste in my mouth but after thinking through it I didn’t want to gamble on the software being or not being intuitive so I went for an initial little bit of a deeper diver. Of course, there was plenty deeper to go.  

My target objectives for this deep dive were:

* Understand what zsh was. 
* Understand why it was replacing bash (Which I felt uncomfortable about.)
* Verify that it was properly installed.
* Learn some features that were unique to zsh that would make my work easier.  

After some Google searches I found out some good information for the zsh n00b.

Post 1:
https://medium.com/@zarinlo/deck-out-your-mac-terminal-z-shell-zsh-made-easy-232f5da30ce6
My google search yielded this very insightful post where I gain some fundamental knowledge about Zsh. 
* Z shell - also zsh is a UNIX shell that is built on top of the Bourne shell(macOS default shell), better known as bash. 
* Reading that put my mind at easy.  Built on bash. That’s good news, so I started building a picture in my mind that it was an enhance bash. (That might be a “proper” metaphor but that was where I landed when I read that sentence. 
* Z shell is basically an extended version of Bash, with many additional features.
* In UNIX/Linux env, you typically have a .barshrc file for Bash.  
* The rc file, otherwise known as the run-control file, is a file of declarations or commands associated with a program that it interprets on startup.  
* Before now I didn’t know the rc was for run-control.  I just knew it as the file that had all the resources I needed to load up after it booted. It’s nice to know something like that because knowing the meaning of something creates an index in the human mind.  What I’m saying is that meaning allows for humans to recall information better.  Meaning is one of the few indexes that the human mind can use to recall information.  In this case although I didn’t know what rc meant I did know how to use the file. 
* The post reviews an install of zsh and git using Homebrew a Mac package management system exactly like apt-get is for Ubuntu and npm is for Node.js.  Package managers have become all the rage in the last 5 years. Homebrew is not affiliated with Apple and is completely independent of them. 
    * brew install zsh
    * brew install git
* My system had already had zsh and git on it. 
* This post presented me with something I knew nothing about, the Oh My Zsh framework.  
Post 2: https://ohmyz.sh/ 
* Post 1 had the link to the Post 2 which is the the Oh My Zsh framework web site.
* The word framework means something specific to developers.  It means a resource for building application in where a lot of the decision of   how something is going to be coded to get a certain outcome from the app you are coding have been pre-made for you. You code will be formatted in a certain way because of the way the framework resources expect to be used. And I don’t think that is what they mean by framework.  I think what they mean by framework is what software developers mean by a library. Because in looking closely at the Oh My Zsh “framework” it looks like a series of MEANINGFUL commands that have been created using zsh aliasing mechanism and group into namespaces that Oh My Zsh framework calls plugins.  These plugin facilitate the used of terminal by amalgamating the commands offer at a lower level of of the software into more meaningful commands from the software, that making it more contextual thusly more memorable and “easier to use”. 
* At that point I looked to the call of installing the OMZ framework via terminal as something I wanted to do from a clean state.  Meaning I wanted to install it as an upgrade from bash and not having zsh already installed since the framework installed zsh also. So I googled how to revert my system back to bash. 
* This is where the real learning began for me and it got more fun. 
Post 3: https://www.cyberciti.biz/faq/change-default-shell-to-bash-on-macos-catalina/
* Is the post that outlined the steps to take to revert everything to bash.  
* Before search and finding Post 3 I learned that if I was in zsh and wanted to go to bash all I had to do in the window was type bash. 
* I also learned that when I closed the window bash was gone and zsh was back and that felt a little unexpected.  Maybe I thought it would be easy but it was not going to be as easy as me calling bash for it to remain every time I open a window.  There was some work to do. 
* First thing I learned from Post 3 was something I had not even considered. Apple replace bash with Z shell for licensing reasons. I’m sure more details can be found out on that but it’s beyond the scope of the targeted knowledge but the solved their licensing issue with zsh.
* Step 1 to going back to bash was to see if it was still on the system by the following terminal commands:
    * cat /etc/shells - this command lists the shells that are on the system (make sure you put the s in shells, for some reason I’ve not a few times already and I get: cat: /etc/shell: No such file or directory (as I should)
    * bash appeared on the list
➜  / cat /etc/shells
\# List of acceptable shells for chpass(1).
\# Ftpd will not allow users to connect who are not using
\# one of these shells.

/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
* And there they are and the place where they can be found. 
* Step 2 is changing your zsh to bash and surprisingly it’s essentially the same command you used to change bash to zsh. 
* chsh -s /bin/bash (ch -change, sh - shell, -s the shell is /bin/bash) Easy peasy. 
Post 4 is the man doc for chsh: https://linux.die.net/man/1/chsh
* In case you are not aware the man command in *nix stands for manual and several web sites have made the bash/zsh manual on the web for easy of search. 
* Keep in mind we are changing the shell back to bash because of my fastidious (nit-pick) nature in which I feel compelled to go back to a “known state” which has been many years of bash (at least my definition of a known state because the zsh install was working and working is also a known state)  and do the upgrade to zsh with the Oh My Zsh framework.
* I go to Step 2 chsh -s /bin/bash as previously mentioned
* The terminal messages back the user name and that for that user: chsh: no changes made
* I’m confused what.  
* I go back reverify tat I saw bash in the /etc/shells file. 
* It’s there. I go to the file system location, it’s there. 
* I attempt todo the chsh command again, 3 more times each time verifying that I had not missed anything I start to google the message: chsh: no changes made. Nothing significant comes up.  
* I read on on more on Post 3.
* I do the echo $SHELL and it returns zsh
* I do the bash —version it gives me the bash version because remember bash is installed I have just failed to switch it to being the default shell again. 
* I read some more and I’m clear that the previous steps didn’t work for me.  The are easy steps so I dig deeper to see if I can change something to make it work.  
* I read further in Post 3. 
* For some reason that was clear to the writer of Post 3 he switch context to a different approach
* How to update or upgrade bash version?
    * brew install bash
    * brew installs bash
    * This new version of bash is in /usr/local/bin/bash
    * I run ls -l /usr/local/bin/bash
    * It shows in the file system. 
    * I cat /etc/shells
    * It doesn’t show in the shells file. 
    * We have to append it to the file
* At this point I learn something fascinating. 
    * The instructions say
        * sudo -i
        * And I look at that for a few seconds and I’m like what is that?
* First let me tell you the net result of running sudo -i
* It changed my user to root.  I went from being me to being root.
➜  ~ whoami <br>
<my_user> <br>
➜  ~ sudo -i <br>
Password: <br>
XXXXXXXX:~ root# whoami <br>
root <br>
XXXXXXXX:~ root# <br><br>

############################ <br><br>

➜  ~ whoami <br>
<my_user> <br>
➜  ~ sudo -i <br>
Password: <br>
XXXXXXXXX:~ root# echo /usr/local/bin/bash >> /etc/shells <br>
XXXXXXXXX:~ root# chsh -s usr/local/bin/bash <br>
Changing shell for root. <br>
chsh: WARNING: shell 'usr/local/bin/bash' does not exist <br>
XXXXXXXXX:~ root# exit <br>
logout <br>
➜  ~ whoami <br>
<my_user> <br>
➜  ~ bash --version <br>
GNU bash, version 5.0.18(1)-release (x86_64-apple-darwin19.5.0) <br>
Copyright (C) 2019 Free Software Foundation, Inc. <br>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> <br><br>

This is free software; you are free to change and redistribute it. <br>
There is NO WARRANTY, to the extent permitted by law. <br>
➜  ~ <br><br>

I have to say that the   sudo -i
Was a cool discovery from me.  
I had used Linux before and had become root by sudo su -
But never sudo -i. 

Post 5: https://linux.die.net/man/8/sudo
This is the explanation from Post 5:
-i [command]
The -i (simulate initial login) option runs the shell specified by the password database entry of the target user as a login shell. This means that login-specific resource files such as .profile or .login will be read by the shell. If a command is specified, it is passed to the shell for execution via the shell's -c option. If no command is specified, an interactive shell is executed. sudo attempts to change to that user's home directory before running the shell. The security policy shall initialize the environment to a minimal set of variables, similar to what is present when a user logs in. The Command Environment section in the sudoers(5) manual documents how the -i option affects the environment in which a command is run when the sudoers policy is in use.

* I’m back to bash. I’m even in a more recent version of bash than I knew I could be on a Mac.  I never questioned if I could upgrade bash on a Mac.  I wish I would had known in 2015 when I was writing a bash script and I could have used more advanced features of bash.  
* This part of my quest for zsh was by far the best part. 
* I’m going to go to zsh but I love that I have options. 
* As you can see when I changed the shell to bash I tested that the terminal app new what version of bash it was using.  And it did. 
* I also 
    * /usr/local/bin/bash --version
    * As a check also, as Post 3 recommended it. 
    * All was well.  
    * I was back to bash and an more advance version of it. <br>
**FINALLY A CLEAN INSTALL OF ZSH** <br>
* In Post 1 I had read of Oh My Zsh. 
* I read that it puts down zsh, a framework with plugins and themes. 
* I wanted to make use of all those tools. 
* So I did the install of Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)”
* It was great to see it doing its thing the clever messages that come up with the install 
* Then it told me there was a warning, it was validating some zsh dirs and it didn’t like 2 that were there
* I supposed that it was from the previous install
* It gave me instruction that if I basically understood the provenance of these directories to add 
    * ZSH_DISABLE_COMPFIX=“true” to the .zshrc file. 
    * So I did. 
* NOTE: Many posts out there say that if you don’t know where zsh is to install it by:
    * chsh -s $(which zsh)
    * I think there is a benefit to knowing and thus you can be precise and if you don’t want to install Oh My Zsh framework you can just cat the /etc/shells files and see exactly where it is. 
    * / cat /etc/shells
    * \# List of acceptable shells for chpass(1).
    * \# Ftpd will not allow users to connect who are not using
    * \# one of these shells.
    * 
    * /bin/bash
    * /bin/csh
    * /bin/dash
    * /bin/ksh
    * /bin/sh
    * /bin/tcsh
    * /bin/zsh

**Oh My Zsh Plugins and Themes**
Post 6: https://github.com/ohmyzsh/ohmyzsh/
* This document is my introduction narrative to zsh.  Post 1 there is a section that explains what to do to your .zshrc file to enjoy the plugins. 
plugins=(
  git sublime vscode jsontools 
)
If you look at the plugins what you see is a series of aliases that look extremely useful for a chained command line terminal commands that are useful. Making it easy to use the said commands for the application the plugin is for.  I went ahead and kept all the ones in the example because I use all of them except jsontools and I left it on there and added a few that I knew were in the plugin page of the framework which is in Post 6. 
* The list of plugins in found in ~/.oh-my-zsh/plugins
* Each subdirectory will show the name of a tool that has plugins. 
* Some you will recognize and others you won’t add to the the list of your plugin configuration as you see useful and with caution that you don’t put too many and cause your system to slowdown because you are loading too many. 
Post 7: https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
* All the are shown in Post 7 as of this date October 18, 2020. 
* Should this document become stale you can update your install and get all the contemporary themes. 
* The one that is preconfigured is at the very top called robbyrussell
* All you have to do is go to your .zshrc file and find the variable ZSH_THEME and change it’s value with the theme you want.  
* After visiting with the themes I changed mine to “jonathan”: ZSH_THEME="jonathan"
**Next Post**
Now that we understand better:
* what zsh is
    * Enhanced bash 
* why it was replacing bash (Which I felt uncomfortable about.)
    * Licensing issue
* If it's properly installed
    * chsh 
* Some features that were unique to zsh that would make my work easier
    * Plugins and Themes
I’ll be posting on productivity features that the new shell brings to us and how to better leverage those features. 