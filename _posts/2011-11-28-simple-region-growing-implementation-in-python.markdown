---
layout: post
status: publish
published: true
title: A simple region growing implementation in Python
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 318
wordpress_url: http://www.lengrand.fr/?p=318
date: 2011-11-28 13:51:14.000000000 +01:00
categories:
- OpenCV
- Python
- Tippy
tags:
- image processing
- tippy
- region growing
- prototyping
comments:
- id: 3155
  author: dg
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMi0xMi0xNSAxMToxMDowMCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0xMi0xNSAxMDoxMDowMCArMDEwMA==
  content: Hi! thank you very much for this work, it is pretty useful! I would like
    to know if this is the last version of the function, I want to put more than one
    seed....
- id: 3157
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0xMi0xNSAxMjoxNDo0OCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0xMi0xNSAxMToxNDo0OCArMDEwMA==
  content: ! "Hey ! \n\nReally glad it has been useful for you. \nI haven't touched
    the code for some time now, but I can think about updating it if you need :).
    \n\nLet me think about it"
- id: 3203
  author: dg
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMi0xMi0xNyAyMTozMToyOCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0xMi0xNyAyMDozMToyOCArMDEwMA==
  content: ! "Thank you!! :)  I'm running the function for different seeds and obtaining
    individual images, but still I need to have just one single final output ... \r\n\r\nbest!"
- id: 3212
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0xMi0xOCAwOTo0ODozOCArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0xMi0xOCAwODo0ODozOCArMDEwMA==
  content: ! "I will have a look at it during the holidays. \r\n\r\nIn the meantime,
    can't you apply the same algorithm multiple times on your image, and then perform
    a binary operation? \r\n\r\nCheck it out <a href=\"http://stackoverflow.com/questions/11262312/opencv-intersection-between-two-binary-images\"
    title=\"SO intersection images\" target=\"_blank\">here</a>, I think that using
    either an <strong>and</strong> or an <strong>or</strong> operation between your
    two output images ' will do what you want : merge the results. \r\n\r\nLet me
    know ;)"
- id: 3214
  author: dg
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMi0xMi0xOCAxMzoxOTowOSArMDEwMA==
  date_gmt: !binary |-
    MjAxMi0xMi0xOCAxMjoxOTowOSArMDEwMA==
  content: Thaaanks!!! I will let you know :)
- id: 3536
  author: dg
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMy0wMS0wOSAxNjozNjowMiArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0wOSAxNTozNjowMiArMDEwMA==
  content: ! "Hi! Happy 2013!\r\n\r\nSince I'm not an expert in opencv and python
    I couldn't achieve it...these functions requires arrays instead iplimages.....
    but so far still your library works for my purpose! thank you very much\r\n\r\nSorry
    for late reply.. I was also working on my input image :S\r\n\r\nThanks again!"
- id: 3539
  author: jll
  author_email: jlengrand@gmail.com
  author_url: ''
  date: !binary |-
    MjAxMy0wMS0wOSAxNjo0OToyNyArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0wOSAxNTo0OToyNyArMDEwMA==
  content: ! "Hey, t thanks! Best wishes to you too:)\r\n\r\nmy holidays were busier
    than expected finally:)\r\nWhat do you want to do exactly!? Do you still need
    help!?\r\n\r\nSend me a mail if you need more, I'll answer you:)"
- id: 3671
  author: dg
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMy0wMS0xNiAxMDo0NDoyNiArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0xNiAwOTo0NDoyNiArMDEwMA==
  content: ! "Thank you very much for your kindness... :O I didn't find your e-mail
    address :(... Basically I need to put several seeds in one input image (this is
    a matrix transformed to image) and obtain a single output image with regions..
    the idea is to not have overlapping regions..  \r\n\r\nSo far Im using several
    seeds using for loop in the part of your code calling the function and obtaining
    independant outputs, but this is giving me overlapping regions and it would really
    really useful if I don't have to join output images to a single one manually.
    \r\n\r\nIf you wish I can write you an email!\r\n\r\nThanks again"
- id: 3928
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMy0wMS0yNSAxMToxNDozMCArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0yNSAxMDoxNDozMCArMDEwMA==
  content: ! "Hey, \n\nIt would help a lot if you could send me a \"ready to go\"
    script of what you want to do so that I can see and try to upgrade my script.
    \n\nSomething with the upload of the image, and the positions of the seeds you
    want.\n\nPut it on git somewhere and I'll look into it."
- id: 4004
  author: Diana
  author_email: drgalindog@linuxmail.org
  author_url: ''
  date: !binary |-
    MjAxMy0wMS0yOCAxMzoyMjowOCArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0yOCAxMjoyMjowOCArMDEwMA==
  content: Now it is already solved! thank you very much again. :)
- id: 4014
  author: Margarita Gonzalez Ramirez
  author_email: margy9003@hotmail.com
  author_url: ''
  date: !binary |-
    MjAxMy0wMS0yOSAwMjowNDowNiArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0yOSAwMTowNDowNiArMDEwMA==
  content: ! "Hi, I saw your program and I said that is the program that I need. I
    compiled in linux (terminal) and I showed those mistakes. Can u help me to solve
    them?\r\n\r\n./testrg.py: line 1: import: command not found\r\nfrom: can't read
    /var/mail/opencv.cv\r\n./testrg.py: line 4: import: command not found\r\n./testrg.py:
    line 5: import: command not found\r\n./testrg.py: line 6: import: command not
    found\r\n./testrg.py: line 8: user_input: command not found\r\n./testrg.py: line
    10: img_name: command not found\r\n./testrg.py: line 11: threshold: command not
    found\r\n./testrg.py: line 12: syntax error near unexpected token `('\r\n./testrg.py:
    line 12: `img = cv.LoadImage(img_name, cv.CV_LOAD_IMAGE_GRAYSCALE);'\r\n\r\nThanks"
- id: 4019
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMy0wMS0yOSAwOTo0ODo0NCArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0wMS0yOSAwODo0ODo0NCArMDEwMA==
  content: ! "Hi, \n\nI am not sure what you mean. \nThis code is Python, so you should
    not have to compile it but run it with python. \n\nthat means do something like
    : \n\n<code>\npython testrg.py\n</code>\n\nIf you want to be able to use ./testrg.py
    directly, you need to append a <a href=\"http://en.wikipedia.org/wiki/Shebang_(Unix)\"
    title=\"shebang wikipedia\" target=\"_blank\">shebang</a> at the beginning of
    the file: \n\n<code>\n#!/usr/bin/python\n</code>\n\nHope this helps !"
- id: 19038
  author: Pascal
  author_email: hmarois21@hotmail.com
  author_url: http://priveyes.craym.eu
  date: !binary |-
    MjAxMy0xMC0yOCAxNTowMTo1MCArMDEwMA==
  date_gmt: !binary |-
    MjAxMy0xMC0yOCAxNDowMTo1MCArMDEwMA==
  content: ! "Hi !\r\nI'm not understand this part : (the first dist value does nothing
    ?) TY\r\n\r\n#add the nearest pixel of the contour in it\r\n        dist = abs(int(numpy.mean(contour_val))
    - mean_reg)\r\n \r\n        dist_list = [abs(i - mean_reg) for i in contour_val
    ]\r\n        dist = min(dist_list)    #get min distance"
---
Hi all,

Here is a simple example of (simple) <strong><a title="region growing" href="http://en.wikipedia.org/wiki/Region_growing" target="_blank">Region Growing algorithm</a></strong> in <strong>Python</strong>.
It is part of my<a title="github_tippy" href="http://github.com/jlengrand/Tippy" target="_blank"> current project</a>, called <strong>Tippy</strong>.

<strong>Tippy</strong> tries to implement use the power of <strong><a title="opencv" href="http://opencv.willowgarage.com/wiki/" target="_blank">OpenCV</a></strong> and Python to fasten <a title="computer_vision" href="http://en.wikipedia.org/wiki/Computer_vision" target="_blank">Computer Vision</a> prototyping.
The idea is to get as much result as possible with a minimum of code.

A word about <a title="REGION_GROWING" href="http://en.wikipedia.org/wiki/Region_growing" target="_blank">region growing</a> , and this implementation :

This approach to segmentation examines neighboring pixels of initial “seed points” and determines whether the pixel neighbors should be added to the region. The process is iterated on, in the same manner as general data clustering algorithms"
Basically, region growing is an<strong> iterative method used to extract similar parts of an image</strong>. One or several points are chosen as a start. The region then grows until it is finally blocked by the<strong> stop criteria</strong>. This criteria is generally an inside/outside region comparison (energy, size, . . .).
Region growing is massively used in medical imaging, and object detection. <a title="mine_hunting ECUA" href="http://drive.google.com/open?id=0B4bXocpgiAyxY1I3d2lIR2tvSHcf" target="_blank">Here is an example of application in automatic <strong>Mine Hunting</strong></a>, which I worked with last year at <a title="TNO" href="http://www.tno.nl/" target="_blank">TNO</a>.

The following method uses one seed point, defined by the user. The region grows by comparing with its neighbourhood. The chosen criteria is in this case a difference between outside pixel's intensity value and the region's mean.
The pixel with minimum intensity in the region neighbouhood is chosen to be included. The growing stops as soon as the difference is larger than a threshold.

In this implementation, a 4-connectivity has been chosen. The 8-connectivity should be included soon.
Due to the method itself, <strong>only grayscale images</strong> may be processed for now. So color images should be converted first.
<img class="size-full wp-image-320" title="region growing tests with a gnu" src="{{ site.url }}/images/posts/2011/11/region_growing.jpg" alt="region growing tests with a gnu" width="629" height="285" />

Here is the input image, the image with the seed point placed, and the final result!

<br>

Here is the region growing function implemented in Tippy:

{% highlight python %}
import sys
import cv
import numpy

def simple_region_growing(img, seed, threshold=1):
    """
    A (very) simple implementation of region growing.
    Extracts a region of the input image depending on a start position and a stop condition.
    The input should be a single channel 8 bits image and the seed a pixel position (x, y).
    The threshold corresponds to the difference between outside pixel intensity and mean intensity of region.
    In case no new pixel is found, the growing stops.
    Outputs a single channel 8 bits binary (0 or 255) image. Extracted region is highlighted in white.
    """

    try:
        dims = cv.GetSize(img)
    except TypeError:
        raise TypeError("(%s) img : IplImage expected!" % (sys._getframe().f_code.co_name))

    # img test
    if not(img.depth == cv.IPL_DEPTH_8U):
        raise TypeError("(%s) 8U image expected!" % (sys._getframe().f_code.co_name))
    elif not(img.nChannels is 1):
        raise TypeError("(%s) 1C image expected!" % (sys._getframe().f_code.co_name))
    # threshold tests
    if (not isinstance(threshold, int)) :
        raise TypeError("(%s) Int expected!" % (sys._getframe().f_code.co_name))
    elif threshold < 0:
        raise ValueError("(%s) Positive value expected!" % (sys._getframe().f_code.co_name))
    # seed tests
    if not((isinstance(seed, tuple)) and (len(seed) is 2) ) :
        raise TypeError("(%s) (x, y) variable expected!" % (sys._getframe().f_code.co_name))

    if (seed[0] or seed[1] ) < 0 :
        raise ValueError("(%s) Seed should have positive values!" % (sys._getframe().f_code.co_name))
    elif ((seed[0] > dims[0]) or (seed[1] > dims[1])):
        raise ValueError("(%s) Seed values greater than img size!" % (sys._getframe().f_code.co_name))

    reg = cv.CreateImage( dims, cv.IPL_DEPTH_8U, 1)
    cv.Zero(reg)

    #parameters
    mean_reg = float(img[seed[1], seed[0]])
    size = 1
    pix_area = dims[0]*dims[1]

    contour = [] # will be [ [[x1, y1], val1],..., [[xn, yn], valn] ]
    contour_val = []
    dist = 0
    # TODO: may be enhanced later with 8th connectivity
    orient = [(1, 0), (0, 1), (-1, 0), (0, -1)] # 4 connectivity
    cur_pix = [seed[0], seed[1]]

    #Spreading
    while(dist<threshold and size<pix_area):
    #adding pixels
        for j in range(4):
            #select new candidate
            temp_pix = [cur_pix[0] +orient[j][0], cur_pix[1] +orient[j][1]]

            #check if it belongs to the image
            is_in_img = dims[0]>temp_pix[0]>0 and dims[1]>temp_pix[1]>0 #returns boolean
            #candidate is taken if not already selected before
            if (is_in_img and (reg[temp_pix[1], temp_pix[0]]==0)):
                contour.append(temp_pix)
                contour_val.append(img[temp_pix[1], temp_pix[0]] )
                reg[temp_pix[1], temp_pix[0]] = 150
        #add the nearest pixel of the contour in it
        dist = abs(int(numpy.mean(contour_val)) - mean_reg)

        dist_list = [abs(i - mean_reg) for i in contour_val ]
        dist = min(dist_list)    #get min distance
        index = dist_list.index(min(dist_list)) #mean distance index
        size += 1 # updating region size
        reg[cur_pix[1], cur_pix[0]] = 255

        #updating mean MUST BE FLOAT
        mean_reg = (mean_reg*size + float(contour_val[index]))/(size+1)
        #updating seed
        cur_pix = contour[index]

        #removing pixel from neigborhood
        del contour[index]
        del contour_val[index]

    return reg
{% endhighlight %}

Here is a <strong>simple test</strong> of the function, using Tippy functions. If you only want to use the function, juste remove the tippy stuff and copy the function in your source.
Please note than <strong><a title="Compiling OpenCV for Linux (Debian)" href="http://www.lengrand.fr/2011/11/compiling-opencv-for-linux-debian/" target="_blank">OpenCV</a></strong> is needed for the function to work ;)

{% highlight python %}
import cv

import tippy.segmentations as se
import tippy.basic_operations as bo
import tippy.display_operations as do

user_input = 0

img_name = "tippy/data/gnu.jpg"
threshold = 20
img = cv.LoadImage(img_name, cv.CV_LOAD_IMAGE_GRAYSCALE)

if user_input:
    seed = bo.mouse_point(img, mode="S") # waits for user click to get seed
else:
    seed = (70, 106)

out_img = se.simple_region_growing(img, seed, threshold)

do.display_single_image(out_img, "Region Growing result")
{% endhighlight %}

As you can see, the implementation is rather short in code.
An option has been included to let user interactively choose their seed.

<strong><a title="github_tippy" href="http://github.com/jlengrand/Tippy" target="_blank">Tippy is available here</a></strong>
As the project is in its very beginning, only a few functions are implemented for now.
But I have a lot more coming for you :).

As you can see in the source, tests are included with each function. Applications notes and examples will shortly be available too.
Finally, there is now proper installer for now. <strong>Simply add the tippy folder in your sources and include the files you need.</strong>

I would be very pleased to find some co-workers. It would allow the library to grow much faster :). So feel free to <a title="github_tippy" href="http://github.com/jlengrand/Tippy" target="_blank">fork the project</a> ;)
And (constructive) comments are of course encouraged too !

See you soon
Julien
