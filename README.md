reddit-flair-tool
=================

A little script to automated creating and updating flair on reddit subreddits.

Requires:
 * Pillow ('pip3 install Pillow') 
 * PRAW
 * possibly other image manipulation libraries like libjpeg-dev.

Written in Python 3.

Usage:

flairTool.py [-h] [-m MOD] [-p PASSWORD] [-i IMAGEDIR] [-s SUBREDDIT]
                    [-l {none,all,debug,info,warning,error,critical}]

(re)create the user flair of the given subreddit.

optional arguments:
  -h, --help            show this help message and exit
  -m MOD, --mod MOD     Name of BGG mod with auth to update.
  -p PASSWORD, --password PASSWORD
                        Password of mod account given.
  -i IMAGEDIR, --images IMAGEDIR
                        The directory that contains the flair images. Default
                        is "./images"
  -s SUBREDDIT, --subreddit SUBREDDIT
                        Subreddit to update. Default is "timotab".
  -l {none,all,debug,info,warning,error,critical}, --loglevel {none,all,debug,info,warning,error,critical}
                        The level at which to log. Must be one of none, debug,
                        info, warning, error, or critical. Default is none.
                        (This is mostly used for debugging.)


This script assumes 16x16 images (GIF, PNG, JPG) in the images directory. The file names should be words separated by dashes. The file names will become the text in the flair selection box with the dashes replaced by spaces and the words capitalized. Ex: filename foo-bar-baz.png will become flair labled with "Foo Bar Baz". The username and password can be passed in on the command line or a file in the $PYTHONPATH named "AccountDetails.py" can be used. The AccountDeatils.py file must declare the username and password as so:

USERNAME = my_reddit_username
PASSWORD = my_reddit_password


Enjoy.


