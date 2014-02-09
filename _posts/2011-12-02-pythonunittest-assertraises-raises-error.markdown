---
layout: post
status: publish
published: true
title: ! 'Python/Unittest : assertRaises raises Error'
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
wordpress_id: 327
wordpress_url: http://www.lengrand.fr/?p=327
date: 2011-12-02 13:49:49.000000000 +01:00
categories:
- Python
tags:
- tippy
- unittest
- unit tests
- agile
- TDD
- test driven development
comments:
- id: 828
  author: md
  author_email: md@pmcd-cons.com
  author_url: ''
  date: !binary |-
    MjAxMi0wNC0xOSAyMTo1MzowNSArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wNC0xOSAyMDo1MzowNSArMDIwMA==
  content: ! "test_square_vlaue gives an eroror because assertRaises wants for 2nd
    arg a callable not a function call.\r\nthis should do:\r\nself.assertRaises(TypeError,
    df.square_value, 'A')"
- id: 873
  author: Julien Lengrand-Lambert
  author_email: julien@lengrand.fr
  author_url: http://www.lengrand.fr
  date: !binary |-
    MjAxMi0wNC0yNCAxMjo0MToyNCArMDIwMA==
  date_gmt: !binary |-
    MjAxMi0wNC0yNCAxMTo0MToyNCArMDIwMA==
  content: ! "Thanks for the info, I'll try this way of doing next time. \r\nIt is
    prettier than my current solution :)"
---
Hi all,

Today, a small hint about <strong>unit tests</strong> in Python I discovered while working on <strong><a title="tippy on github" href="https://github.com/jlengrand/Tippy" target="_blank">Tippy</a></strong>.

In order to get as reliable code as possible, I am currently experiencing <strong><a title="agile" href="http://en.wikipedia.org/wiki/Agile_software_development" target="_blank">Agile</a></strong> techniques, and especially <strong><a title="TDD" href="http://fr.wikipedia.org/wiki/Test_Driven_Development" target="_blank">TDD</a></strong>. I develop <strong>Tippy</strong> in Python, and test methods with the excellent <a title="unittest framework" href="http://docs.python.org/library/unittest.html" target="_blank">unittest</a> framework.One of (in my mind at least) the most important tips Agile provides is the "<a title="fail fast" href="http://en.wikipedia.org/wiki/Fail-fast" target="_blank">fail fast</a>" rule. And to fit with this rule, all my methods check their inputs before performing anything else.

It implies a lot of <strong>assertRaises</strong> assertions in my tests. Here is an example of how it could be used :

Let's say I want to create a (dum) function calculating the square value of a number. I will have to test that the input can really be multiplied.
<ul>
	<li>First, here is the corresponding (still dum :p) function in file dum_function.py :</li>
</ul>
[python]
def square_value(a):
    &quot;&quot;&quot;
    Returns the square value of a.
    &quot;&quot;&quot;
    try:
        out = a*a
    except TypeError:
        raise TypeError(&quot;Input should be a string:&quot;)

    return out
[/python]
<ul>
	<li>Here is the test to be performed (only this test is inserted):</li>
</ul>
[python]
import dum_function as df # import function module
import unittest
class Test(unittest.TestCase):
    &quot;&quot;&quot;
    The class inherits from unittest
    &quot;&quot;&quot;
    def setUp(self):
        &quot;&quot;&quot;
        This method is called before each test
        &quot;&quot;&quot;
        self.false_int = &quot;A&quot;

    def tearDown(self):
        &quot;&quot;&quot;
        This method is called after each test
        &quot;&quot;&quot;
        pass
    #---
    ## TESTS
    def test_square_value(self):
        # assertRaises(excClass, callableObj) prototype
        self.assertRaises(TypeError, df.square_value(self.false_int))

if __name__ == &quot;__main__&quot;:
    unittest.main()
[/python]
<ul>
	<li>We are now ready to test our function! Here is what happens when trying to run the test :</li>
</ul>
[python]
======================================================================
ERROR: test_square_value (__main__.Test)
----------------------------------------------------------------------
Traceback (most recent call last):
  File &quot;test_dum_function.py&quot;, line 22, in test_square_value
    self.assertRaises(TypeError, df.square_value(self.false_int))
  File &quot;/home/jlengrand/Desktop/function.py&quot;, line 8, in square_value
    raise TypeError(&quot;Input should be a string:&quot;)
TypeError: Input should be a string:

----------------------------------------------------------------------
Ran 1 test in 0.000s

FAILED (errors=1)
[/python]

The <strong>TypeError</strong> is actullay raised, and generates a test failure. The problem is that this is <strong>exactly the behavior</strong> we wanted :s.

To avoid this error, simply run the function using lambda in the test call :

[python]

self.assertRaises(TypeError, lambda: df.square_value(self.false_int))

[/python]

The final output :

[python]
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
[/python]

Perfect !

<em><strong>Note :</strong> For the purpose of this article, I did not work "backwards" (created test before the function). I think this would have been counter productive for the effect I wanted to highlight.</em>
