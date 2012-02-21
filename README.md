localserve
==========

Sometimes you have a static HTML site and all you want to do is view it in the
browser without mucking about with your webserver configuration or `file:///`
URLs (that break absolute paths and prevent AJAX from working properly).

How about you just `cd` into the website directory, type `localserve` and
start browsing the site instead?

Also, it's like super easy to install.

Requirements
------------
Python 2.4 or higher (yup, 3x included).

Installation
------------
1. Place the `localserve` executable on your `$PATH`.
2. There's no step 2.

What's wrong with `python -m SimpleHTTPServer`?
-----------------------------------------------
Nothing!

It's just that I happen to move across systems -- and believe it or not, some
only have Python 3 installed by default (hat tip to Arch users).

Of course, you could just alias this:

    python -m SimpleHTTPServer || python -m http.server

and it'll work. Except that you can't specify the port number as an argument.
So you turn it into a shell function or a script instead:

    function localserve() {
        python -m SimpleHTTPServer $1 || python -m http.server $1
    }

But then you see all the exception tracebacks and the `No module named
SimpleHTTPServer` error on Arch. And you cant' just `/dev/null` the `STDERR`
stream because that hides the useful errors, too. Like *address already in use*
or *permission denied* when attempting to bind a system port as a regular user.

And once you start thinking about updating the script to check for the Python
version and the specified port numbers you should just put this baby on your
`$PATH` instead.


License
-------
Copyright (c) 2012, Tomas Sedovic <tomas@sedovic.cz>

This program is licensed under the terms of the 2-clause ("simplified") BSD
license. See the attached LICENSE.txt file for the full text of the license.
