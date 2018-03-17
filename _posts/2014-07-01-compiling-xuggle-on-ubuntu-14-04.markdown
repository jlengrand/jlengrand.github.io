---
layout: post
status: publish
published: true
title: Compiling Xuggle on Ubuntu 14.04
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- programming
- java
tags:
- xuggle
- java
- xuggle
- codec
- ubuntu
comments: []
---

This guide applies for the latest [Xuggle][1] release from [Github][2] (5.5).
<br />
<br />

It is useful if you want to compile **Xuggle** from source on the latest **Ubuntu** release (14.04). I have been compiling using a **64 bits** system.
<br />

You can find more complete information on the [dedicated page from the Xuggle website][3].
And if you need even more info, you can have a look at [the advanced build page][4].
<br />
<br />
First of all, we will need to install some packages needed during the compilation :
<br />

    $ apt-get install ant git yasm # Installing various dependencies
    $ apt-get install build-essential # g++, gcc and others

We then want to download and install the latest Java 7 realease
For that, we use a ppa.

    $ add-apt-repository ppa:webupd8team/java
    $ apt-get update && apt-get install oracle-java7-installer

Then, we can clone the latest Xuggle source code directly from github :

    $ git clone http://github.com/artclarke/xuggle-xuggler.git
    $ cd xuggle-xuggler


**We will also need to upgrade g++**. Indeed, if we don't do that the compilation will result in an error due to unauthorized type conversion.
The precise error message is :

    ([exec] ../../../../../../../csrc/com/xuggle/xuggler/Codec.cpp:158:38: error: converting 'false' to pointer type 'int (*)(AVCodecContext*, void*, int*, AVPacket*)' [-Werror=conversion-null])

To solve this, I configured **g++ < 4.8** to be used by default **(4.6 here)**

    $ apt-get install g++-4.6
    $ update-alternatives --remove-all g++
    $ update-alternatives --display c++
    $ update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 10
    $ update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 20

    $ update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++ 30
    $ update-alternatives --set c++ /usr/bin/g++
    $ update-alternatives --config g++ # Choose the older version



Finally, we can try to compile Xuggle from source.

    $ ant stage

Compilation takes roughly **10 minutes** on my system.
<br />
<br />
If the compilation is successful, you can get the generated **jar** in the dist folder.
The latest release of Xuggle embeds the **so** files directly in the jar, so you shouldn't need anything else.
<br />
<br />
Compiling Xuggle from scratch in 14.04 has been surprisingly easy comparing to 12.04. The compilation scheme has been greatly improved in the latest Xuggle release.
<br />
<br />
**Note : Xuggle is now deprecated, and has not been updated for now almost a year. So far, I haven't found an equivalent that would be just as good. Let me know if you do!**


  [1]: http://www.xuggle.com/
  [2]: http://github.com/artclarke/xuggle-xuggler
  [3]: http://www.xuggle.com/xuggler/build
  [4]: http://www.xuggle.com/xuggler/advbuild