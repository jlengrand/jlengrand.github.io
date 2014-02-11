---
layout: page
status: publish
published: true
title: Programming Tips
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 431
wordpress_url: http://www.lengrand.fr/?page_id=431
date: 2011-12-28 14:24:01.000000000 +01:00
categories: []
tags: []
comments:
- id: 124
  author: The Programming Tips page is back | loup2fu
  author_email: ''
  author_url: http://www.lengrand.fr/2011/12/the-programming-tips-page-is-back/
  date: !binary |-
    MjAxMS0xMi0yOCAxNDo1MToyMSArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0xMi0yOCAxMzo1MToyMSArMDEwMA==
  content: ! '[...] Programming Tips [...]'
- id: 126
  author: Simply print current function name | loup2fu
  author_email: ''
  author_url: http://www.lengrand.fr/2011/12/simply-print-current-function-name/
  date: !binary |-
    MjAxMS0xMi0yOCAxNjo1NTozNCArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0xMi0yOCAxNTo1NTozNCArMDEwMA==
  content: ! '[...] You can also find this tip in my Programming Tips page, in the
    Python section. [...]'
- id: 135
  author: ! 'Programming tips : New Wordpress section | loup2fu'
  author_email: ''
  author_url: http://www.lengrand.fr/2012/01/programming-tips-new-wordpress-section/
  date: !binary |-
    MjAxMi0wMS0wMyAxMzozNzoyMCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0wMS0wMyAxMjozNzoyMCArMDEwMA==
  content: ! '[...] You will find the content here [...]'
---
Here is a list of all simple tips I have been searching for in the past. I put them here to find them easily !

they are classified by language/topic :
<ul>
	<li><a href="#bash">Bash</a></li>
	<li><a href="#python">Python</a></li>
	<li><a href="#c">C/C++</a></li>
	<li><a href="#git">Git and GitHub</a></li>
	<li><a href="#elec">Electronics</a></li>
	<li><a href="#ocv">OpenCV</a></li>
	<li><a href="#svn">Subversion</a></li>
	<li><a href="#prof">Profiling</a></li>
	<li><a href="#word">Wordpress</a></li>
</ul>
Hopefully one of those tips will help someone :)

<hr />



<hr />

<a name="bash"></a>
<h1>BASH</h1>
<span style="color: #ff9900;">FLV to AVI conversion : </span>

You will need ffmpeg

{% highlight bash %}
$ sudo apt-get install ffmpeg
$ ffmpeg -o /your/flv/file.flv -vcodec mpeg1-video \
 -acodec copy -ar 44100 -s 320x240 -y /your/avi/file.avi
{% endhighlight %}

<hr />

<span style="color: #ff9900;">OGG to AVI conversion : </span>

You will need mencoder

{% highlight bash %}
$ sudo apt-get install mencoder
$ mencoder out.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o Winner.avi
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get the size of a file :</span>

Here are two simple ways:

{% highlight bash %}
$ ls -s file
$ stat file-c %s
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get the processing time of a function/script:</span>

Simply run the same command prepended with <em>time</em>

{% highlight bash %}
$ time previous_command
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get the number of arguments in command line:</span>

Use the variable<strong> $# </strong>to get the number of arguments of previous command.

<span style="text-decoration: underline;">WARNING</span>: The name of the command stands for one argument!

<hr />

<span style="color: #ff9900;">Get the list of dependencies of a binary:</span>

Simply run the same command prepended with <em>ldd</em> :

{% highlight bash %}
$ ldd previous_command
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Demonize a process : </span>

The command to search for is<strong> start-stop-daemon</strong>, with start option.

To avoid any output in stdout, use redirection:

{% highlight bash %}
$ command &amp;> /dev/null&amp;
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Launch a process at startup:</span>

A link must be placed in /etc/init.d, using ln -s

{% highlight bash %}

$ mv /etc/init.d

$ ln -s /path/to/file link

{% endhighlight %}

<span style="text-decoration: underline;">WARNING:</span> A printf in a startup process will lead to a crash as it blocks the remaining processes.

<span style="text-decoration: underline;">INFO:</span> In embedded Linux, startup processes will have to be named using a Sxx name, where xx is a digit between 1 and 99.

The processes will be run in ascending order, so be careful not to block the system (samba after network, . . . )

<hr />

<span style="color: #ff9900;">Block interruptions (CTRL+C) :</span>

Simply add the line

{% highlight bash %}

trap " 2 3

{% endhighlight %}

where you want to 'trap' the command.

End catching interruptions by adding where you want to stop

{% highlight bash %}

trap 2 3

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Use floats in a script, and convert them back to integers:</span>

The operations can be performed with bc :

{% highlight bash %}

$ VAR=$(echo "2.2/ 10.65" | bc -l)

{% endhighlight %}

To switch back to the int value :

{% highlight bash %}

$ (ceil) INT=${VAR/.*}

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Search for pattern in all files of a folder:</span>

{% highlight bash %}

$ "find ./ -name .svn -prune -o -type f -print | xargs grep -Hi" //pattern//

{% endhighlight %}

The .svn part is used to avoid searching in the <a title="subversion wiki" href="http://en.wikipedia.org/wiki/Apache_Subversion">subversion</a> folder of my projects.

{% highlight bash %}

$ grep -R //pattern//@@ is also a solution.

{% endhighlight %}

It is even possible to create an alias with it (see <a href="#alias_anchor">Add a one line command in terminal</a>).

<hr />

<a name="alias_anchor"></a>
<span style="color: #ff9900;"> Add a one line command in terminal:</span>

You may use some one-line commands lots of times a day in terminal.

You can define aliases to gain productivity:

{% highlight bash %}

$ vim ~/.bash_aliases

{% endhighlight %}

Simply add a new line at the end of the file :

{% highlight bash %}

alias_name = "my_one_line_command"

{% endhighlight %}

Restart your terminal, you're done!

<hr />

<span style="color: #ff9900;">Seconds since epoch:</span>

{% highlight bash %}

$ date -d "$FIRST_TIME" +"%s"

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Directly get the correct <a title="shebang wiki" href="http://en.wikipedia.org/wiki/Shebang_%28Unix%29">shebang</a> for you script:</span>

{% highlight bash %}

$ which //language// > my_script

{% endhighlight %}

<strong>Example :</strong>

{% highlight bash %}

$ which bash > my_script.sh

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get the encoding of a file:</span>

{% highlight bash %}

$ file -i //unkown_file_type//

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Remove all .svn folders from a repo:</span>

{% highlight bash %}

$ cd //my_folder///

$ find -name ".svn" -exec rm -rf {} \;

{% endhighlight %}

<span style="text-decoration: underline;">INFO:</span> Can be performed for any folder type, changing the .svn part

<hr />

<span style="color: #ff9900;">Get information about your Linux version:</span>
<ul>
	<li>Description file:</li>
</ul>
{% highlight bash %}

$ cat /etc/lsb-release

{% endhighlight %}
<ul>
	<li>Kernel version:</li>
</ul>
{% highlight bash %}

$ uname -a

{% endhighlight %}
<ul>
	<li>More information about Kernel (compiler and so on):</li>
</ul>
{% highlight bash %}

$ cat /proc/version

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get information about your processor(s):</span>

{% highlight bash %}

$ cat /proc/cpuinfo

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Change default browser in Linux:</span>

{% highlight bash %}

$ update-alternatives &amp;&amp;config x-www-browser

{% endhighlight %}

You will have to choose between all installed browsers in you distro.

<hr />

<span style="color: #ff9900;">Add a user to the sudoers:</span>

{% highlight bash %}

$ visudo

{% endhighlight %}

Search for the line

{% highlight bash %}

@@ root ALL=(ALL) ALL@@

{% endhighlight %}

Add this new line just below :

{% highlight bash %}

user_name ALL=(ALL) ALL

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Get information about you graphical card:</span>

{% highlight bash %}

$ lspci | grep VGA

{% endhighlight %}

You may try this if first is not working :

{% highlight bash %}

$ lspci | grep video

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Add tab completion for sudo commands:</span>

Add

{% highlight bash %}

complete -cf sudo

{% endhighlight %}

in your <strong>.bashrc. </strong>It can be done simply in running the following command once:

{% highlight bash %}

$ echo "complete -cf sudo" > ~/.bashrc

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Read information in <a title="elf files wiki" href="http://en.wikipedia.org/wiki/Executable_and_Linkable_Format">elf files</a>:</span>

{% highlight bash %}

$ readelf -h $1 | grep 'Class\|File\|Machine'

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Sniff on serial interface to read output of a device :</span>

{% highlight bash %}

$ sudo apt-get install jpnevulator

$ jpnevulator --read --ascii --tty /dev/ttyUSB0

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Remove trailing / in path in a script:</span>

{% highlight bash %}

#!/bin/bash

FOLDER=$1

echo ${FOLDER%/}

{% endhighlight %}

<hr />



<hr />

<a name="python"></a>
<h1>PYTHON</h1>
<span style="color: #ff9900;">Get variable name as a string:</span>

{% highlight python %}

blah = 1

blah_name = [ k for k , v in locals (). iteritems () if v is blah ][ 0 ]

{% endhighlight %}

<span style="text-decoration: underline;"> WARNING</span> : Not very clever however, as variables in Python may have more that one name ! Use with caution!

<hr />

<span style="color: #ff9900;">Replace a part of a table [Numpy]:</span>

{% highlight python %}

small_BW=where((L[temp[ptr-1]]==ptr),1,0)

a=BW[posi_0:posi_1,posi_2:posi_3]

a[:,:]=small_BW.copy()

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Reshape table without size information:</span>

Put -1 as second argument, the info will automatically be processed.

{% highlight python %}

array.reshape(3,-1)

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Concatenate 2 tables [Numpy]: </span>

{% highlight python %}

c=numpy.concatenate((a,b),axis=0)

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Cast data in table to int:</span>

{% highlight python %}

Ndarray.astype(int)

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Write in the end of a file :</span>

Use <strong>add</strong> mode :

{% highlight python %}

file.open(file_name, 'a')

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Test if variable exists:</span>

{% highlight python %}
try:
    print variable
except NameError:
    print "Error!"
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Check if variable is one of several choices:</span>

{% highlight python %}
if a in [b, c,d]:
    blabla
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Multi instanciation in Python:</span>

{% highlight python %}
a = b = c = 1+1
{% endhighlight %}

<span style="text-decoration: underline;">WARNING</span>: Those three variables are the same object!

<hr />

<span style="color: #ff9900;">Print function name :</span>

{% highlight python %}
import sys

def tutut():
    """
    Dum function displaying its name!
    """
    print sys._getframe().f_code.co_name

if __name__ == '__main__':
    tutut()
{% endhighlight %}

And here is the result

{% highlight bash %}
[airballman@ubuntu:~]$ python tutut.py
tutut
{% endhighlight %}

<hr />



<hr />

<a name="c"></a>
<h1>C/C++</h1>
<span style="color: #ff9900;">Block interruptions (CTRL+C):</span>

Include the signal header :

[c]
#include signal.h
[/c]

At the beginning of the main, insert

[c]
signal(SIGINT, fction)
[/c]

with
<ul>
	<li><strong>fction</strong> the function to be started on detection.</li>
	<li><strong>SIGINT</strong> the interrupt to be detected.</li>
</ul>

<hr />

<span style="color: #ff9900;">Some simple basics that helped :</span>

<span style="text-decoration: underline;">About variables</span> :
<ul>
	<li>age -> value</li>
	<li>&amp;age -> pointer</li>
</ul>
<span style="text-decoration: underline;">About pointers</span> :
<ul>
	<li>ptr -> ptr value(which is an address)</li>
	<li>*ptr -> variable value placed in the address.</li>
</ul>
<span style="text-decoration: underline;"> If <strong><em>age</em></strong> is a variable</span> :
<ul>
	<li><strong><em>age</em></strong> is its value</li>
	<li><strong><em>&amp;age</em></strong> is its pointer</li>
</ul>
<span style="text-decoration: underline;">If <strong>ptr</strong> is a pointer</span> :
<ul>
	<li><strong>ptr</strong> is the pointer value (which is an address)</li>
	<li><strong>*ptr</strong> is the value of the variable contained in at the address.</li>
</ul>
<span style="text-decoration: underline;">Pointers creation</span>:

[c]
int *ptr = NULL; //Is just a creation, the * does not stand for anything else than declaring the pointer.

int age = 10;

*ptr=&amp;age; //ptr is already created, the * now means that whe want to assign its value
[/c]

<hr />

<span style="color: #ff9900;">Those two are equivalent (used for structures):</span>
<ul>
	<li>a->b</li>
	<li>*(a.b)</li>
</ul>

<hr />

<span style="color: #ff9900;">Define a variable in a Makefile :</span>
<ul>
	<li> Use the<strong> -D</strong> option in the <strong>CFLAGS</strong></li>
	<li><strong>#define</strong> in the C code</li>
</ul>

<hr />



<hr />

<a name="git"></a>
<h1>Git and GitHub</h1>
Simple reminders to manage a project with <strong><a title="git" href="http://git-scm.com/">Git</a></strong> and <strong><a title="gitHub" href="https://github.com/jlengrand">GitHub</a></strong> interface.

<span style="color: #ff9900;">Clone a project from my personal GitHub account:</span>

{% highlight bash %}
$ git clone git@github.com:jlengrand&amp;/projet.git
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Clone a project from another source:</span>

{% highlight bash %}
$ git clone git://git.berlios.de/gpsd
{% endhighlight %}

<hr />

<span style="color: #ff9900;">Push modifications previously locally committed:</span>

Should be performed once in a while to keep remote repository up to date. Do not forget to pull before pushing to avoid conflicts.

{% highlight bash %}
$ git push -origin master
{% endhighlight %}

More information can be found in git documentation

<span style="text-decoration: underline;">INFO</span> : No need to create a folder first, as a main folder is automatically created for the project.

<hr />



<hr />

<a name="elec"></a>
<h1>Electronics</h1>
Some basic tipe for new embedded Eletronics programmers (like me ;) )

<span style="color: #ff9900;">Use of DDx, PORT and PIN registers:</span>
<ul>
	<li> <strong>DDx</strong>: Choice of pins state: Inputs or Outputs</li>
	<li><strong>PORT</strong>: Set the outputs state, rules the outputs (ex : set Pin to 0)</li>
	<li><strong>PIN</strong>: Reads the inputs states, or toggle values. (ex: Toogle Pin)</li>
</ul>

<hr />

<span style="color: #ff9900;">Easily set a bit to 0 in a register:</span>

[c]
PPR=PPR &amp; 0b01111111
[/c]

<hr />

<span style="color: #ff9900;">Easily set a bit to 1 in a register:</span>

[c]
PPR=PPR &amp; 0b01111111
[/c]

<hr />

<span style="color: #ff9900;">Debug hardware errors after optimization:</span>

In case your C code does not work any more after Optimization (-O2 -O3)
<ul>
	<li> Check if<strong> global variables</strong> are used in <strong>interruptions</strong></li>
	<li>Try to set them as <strong>volatile</strong></li>
</ul>
<div>

<hr />

<span style="color: #ff9900;">Hazardous hardware resets:</span>

Check if your <strong>interruptions</strong> are initialized in your code !

Otherwise, the C code will automatically jump to a <strong>non-existing address</strong>, causing the reset.

<hr />

<span style="color: #ff9900;"> I/O problems:</span>

In case of I/O problems in your code, check your Hardware and especially your <strong>resistors</strong>

Try to unsolder them and run the code.

</div>

<hr />

<div id="tiddlerElectronics">

<span style="color: #ff9900;">Embedded electronics main architecture code:</span>

Generally, embedded architecture software is divided into 3 main layers :
<ul>
	<li><strong>Drivers</strong>: Whose job is to interact with Hardware at a low level (Ex : Read spi data)</li>
	<li><strong>Services/Components</strong>: Intermediate layer, interface between drivers and Applications</li>
	<li><strong>Application</strong>: Higher layer, which aims at achieving the main purpose of the project (Ex: Calculate movement using an accelerometer)</li>
</ul>
<ul>
	<li><strong>Here is a simple drawing to get the idea:</strong></li>
</ul>
[caption id="" align="aligncenter" width="881" caption="Embedded Architecture Drawing"]<img class=" " title="Embedded Architecture" src="https://dl-web.dropbox.com/get/Public/00_Website/03_Images/Embedded_architecture.png?w=efee537d" alt="Embedded Architecture" width="881" height="380" />[/caption]

<span style="text-decoration: underline;">INFO</span>: The main idea behind that when you code is the reuse! The application may not be reusable, but drivers and components must !
 If you did good, you should be able to use the same application in two architectures, changing only components and drivers.

</div>

<hr />



<hr />

<a name="ocv"></a>
<h1>OpenCV</h1>
Memos and Tips about the <strong><a title="External link to http://opencv.willowgarage.com/wiki/" href="http://opencv.willowgarage.com/wiki/" target="_blank">OpenCV</a></strong> library.

<span style="text-decoration: underline;">In C/C++:</span>

<span style="color: #ff9900;">Place a pointer to the beginning of pixel in an image:</span>

Can be used to naviguate through pixels easily (and more efficiently than some openCV functions).

[c]
char *pImage = iplImage->ImageData
[/c]

<hr />

<span style="color: #ff9900;">Short review of the IplImage structure:</span>

What's really needed to work with an Image

[c]
* IplImage struct {
    depth # Number of channels (gray level, color, . . .)
    sizeX
    sizeY
    * ImageData } #Pixels of the image
    ...}
[/c]

<hr />

<span style="color: #ff9900;">Simple tips for Image Processing optimization in C:</span>

An image is stored in a memory a a long line (n*m size)

<strong>Always go trough the buffer way, and not the opposite!</strong>

[c]
for (i in nb_lines):
    for (j in nb_cols):
        //do stuff
    }
}
[/c]

and

[c]
for (j in nb_cols):
    for (i in nb_lines):
        //do stuff
    }
}
[/c]

are different !

<strong>The second one is 10% faster than the other !</strong>

<hr />

<span style="text-decoration: underline;">In Python</span> :

<span style="color: #ff9900;">Error on compiling OpenCV with Python bindings:</span>

If you get this error when trying to compile OpenCV in Linux

{% highlight bash %}

Could NOT find PythonLibs (missing: PYTHON_INCLUDE_DIRS) in cmake

{% endhighlight %}

Simply try installing <strong><a title="pydev package" href="http://packages.ubuntu.com/fr/hardy/python-dev">python-dev</a></strong> packages.

It should solve the problem.

<hr />



<hr />

<a name="svn"></a>
<h1>Subversion</h1>
<span style="color: #ff9900;">To create a new branch in one of your repositories:</span>
<ul>
	<li> Copy your trunk folder. This will automatically proceed the mkdir</li>
</ul>
{% highlight bash %}

$ svn cp trunk -> new_branch

{% endhighlight %}

Update the information

{% highlight bash %}

$ svn update

{% endhighlight %}

<span style="text-decoration: underline;">INFO</span>: The command is an update and not a commit, as this is the server who performed the operation!

You're done!

<hr />

<span style="color: #ff9900;">Merge your branch back in your trunk:</span>

Move to your trunk folder

{% highlight bash %}

$ cd path/to/my/trunk

{% endhighlight %}

Merge the branch:

{% endhighlight %}

$ svn merge --reintegrate ./^branch

{% endhighlight %}

<span style="text-decoration: underline;">INFO</span>: The reintegrate option allows continuing to work in the branch even once reintegrated

<hr />

<span style="color: #ff9900;">Some tips:</span>
<ul>
	<li>A tag is used to get a precise version, fixed in time (Ex : V1.1)</li>
	<li>The trunk must always stay as the main reference to branches and tags (ie. <strong>cd /my/trunk</strong> before operations).</li>
	<li>Always use the<strong> ^</strong> sign to merge and branch folders. It allows to avoid using absolute path.</li>
</ul>
<ul>
	<li>The <strong>^</strong> corresponds to /path/to/my/svn/root/folder</li>
	<li>If you're running Windows, you might want to look at <strong><a title="tortoise" href="http://tortoisesvn.net/">tortoisesvn</a>.</strong></li>
</ul>

<hr />



<hr />

<a name="prof"></a>
<h1>Profiling</h1>
Simple tips for software profiling using Linux.

<span style="color: #ff9900;">Simple steps on using gprof:</span>

<strong><a title="gprof" href="http://www.cs.utah.edu/dept/old/texinfo/as/gprof.html">gprof</a></strong> is a really efficient prototyping tool designed by Richard Stallman

It is a total graal to exactly know where your bottlenecks are, and which parts of your software have to be optimized first!
<ul>
	<li>Simply install gprof on your computer (for debian based distros).</li>
</ul>
{% highlight bash %}

$ sudo apt-get install gprof

{% endhighlight %}
<ul>
	<li>Compile your C code with the <strong>-pg</strong> option</li>
	<li>Execute your program, just as usual</li>
	<li>You will see that a<strong> gmon.out</strong> file was created during the execution</li>
	<li>You can retrieve the results of profiling by running gprof:</li>
</ul>
{% highlight bash %}

$ gprof your_binary gmon.out >> saved_report

$ vim saved_report

{% endhighlight %}

<hr />

<span style="color: #ff9900;">Simple command-line to search for memory leacks:</span>

Using the <strong><a title="valgrind" href="http://valgrind.org/">Valgrind</a></strong> library.

{% highlight bash %}

$ valgrind --tool=memcheck --leak-check=yes --show-reachable=yes --num-callers=20 --track-fds=yes ./test

{% endhighlight %}

<hr />



<hr />

<a name="word"></a>
<h1>Wordpress</h1>
Some very simple tips and hints for wordpress.

<span style="color: #ff9900;">Insert an horizontal line in a post :</span>

Simply insert the <strong><hr/> tag</strong> while in <strong>html</strong> edition mode .

<hr />

<span style="color: #ff9900;">Insert anchors/links in a section of a page:</span>

This is done in two different steps :
<ul>
	<li><strong>Define the anchor</strong>. You should place the following code where you want the user to be redirected.</li>
</ul>
[html]your article <a name= "name_of_the_anchor"></a> here.[/html]


<ul>
	<li><strong>Create a link to the anchor</strong>. Depending on what you want, you should insert :</li>
</ul>

<div><span style="text-decoration: underline;">If the anchor is placed in the same page :</span></div>
[html]<a href= »#name_of_the_anchor »>my highlighted text</a>[/html]

<div><span style="text-decoration: underline;">If the anchor is in another page :</span></div>
[html]<a href= »http://www.website.fr/#name_of_the_anchor »>my highlighted text</a>
<a href= »#name_of_the_anchor »>my highlighted text</a>
[/html]

<strong>You can see the result everywhere on this page, in the topic listing :).</strong>
