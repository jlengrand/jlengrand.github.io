---
layout: post
status: publish
published: true
title: Automating thr activation/deactivation of Spotify's proxy settings
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- work
- job
- development
tags:
- bash
- experiment
- spotify
- ing
- work
- startup
- hack
comments: []
---

I'm a **BIG** fan of **[Spotify](https://www.spotify.com/)**. I use it every day, hours on end. 
I like the fat client though, I find the web version way too buggy and unstable.
<br/><br/>
At ING, we use a HTTP proxy and I have configured Spotify to go through the proxy. At home, I don't use anything. 
This means that every day, I have to go back to my settings, disable / enable the proxy and restart Spotify. This is very annoying.
<br/><br/>
So annoying in fact that I started using the web player at home, to my disappointment.
<br/><br/>
Finally, it go me tired enough so I decided to dig deeper into the issue and find a solution. **It had to be possible to automate this.** 
<br/><br/>
The first step was to find the location of the config file. On my Macbook, it is located in __$HOME/Library/Application Support/Spotify/prefs__.
In this file,  I saw the line : __network.proxy.mode=1__.
The rest is child's play
<br/><br/>
Here is the final script I came out with to enable/disable spotify's proxy settings. I called it **spotiProxy**

```bash
#!/bin/sh

ON_OFF=$1
SPOTIFY_PREFS="$HOME/Library/Application Support/Spotify/prefs"
PROXY_ON="network.proxy.mode=2" #HTTP Proxy
PROXY_OFF="network.proxy.mode=1" #No proxy

if [ ! -f "$SPOTIFY_PREFS" ]; then
    echo "Spotify preference file not found. Exiting"
    exit 1
fi

if [ "$ON_OFF" = "on" ]
then
    echo "Activating Spotify proxy settings"
    sed -i -e "s/$PROXY_OFF/$PROXY_ON/g" "$SPOTIFY_PREFS"
elif [ "$ON_OFF" = "off" ]
then
    echo "Deactivating Spotify proxy settings"
    sed -i -e "s/$PROXY_ON/$PROXY_OFF/g" "$SPOTIFY_PREFS"
elif [ "$ON_OFF" = "show" ]
then
    cat "$SPOTIFY_PREFS"
    exit 1
else
    echo "Invalid command entered. Please use 'spotiProxy on' or 'spotiProxy off'"
    exit 1
fi

number_processes=$(pgrep Spotify | wc -l)
if [ $number_processes -gt 1 ] 
then
    echo "Restarting Spotify"
    osascript -e 'quit app "Spotify"'
    sleep 1
    open -a Spotify
fi
```

It's usage is very simple :
* Call it with `spotiProxy on` (or off)
* It will set you settings accordingly, and restart Spotify if it was already running.
* Enjoy!

This script is run automatically every time I arrive at home or at the office. Nothing to do any more. Joy!

<br/><br/>
If you want more info, you can check out the related [Spotify forum post](https://community.spotify.com/t5/Desktop-Mac/Script-to-change-settings/m-p/4446246#M531825) or [the gist on github](https://gist.github.com/jlengrand/ec2fff0f741ae0a59a7f203d9ffee348).
<br/><br/>
See you next time!
