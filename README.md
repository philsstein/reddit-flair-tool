reddit-flair-tool
=================

A little script to automated creating and updating flair on reddit subreddits.

Warning: This script blows away any existing flair - so be careful. Save existing flair images to the image directory you're going to use. This script (re)creates the flait based solely on the images and filenames it is given.

Requires:
 * Pillow ('pip3 install Pillow') 
 * PRAW ('pip3 install praw')
 * possibly other image manipulation libraries like libjpeg-dev. ('sudo apt-get install libjpeg-dev')

Written in Python 3.

Usage:
```bash
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
```

This script assumes 16x16 images (GIF, PNG, JPG) in the images directory. The file names should be words separated by dashes. The file names will become the text in the flair selection box with the dashes replaced by spaces and the words capitalized. Ex: filename foo-bar-baz.png will become flair labled with "Foo Bar Baz". The username and password can be passed in on the command line or a file in the $PYTHONPATH named "AccountDetails.py" can be used. The AccountDeatils.py file must declare the username and password as so:

```python
USERNAME = my_reddit_username
PASSWORD = my_reddit_password
```

Example usage:
```bash
> ls ./images
18xx.gif  hanabi.png  foo-bar.gif
> ./flairTool.py -m mod_uid -p my_password -s my_subreddit -i ./images -l info
```

This would make three flairs in the -s my_subreddit subreddit named "18xx", "Hanabi", "Foo Bar" with the matching images. 

Enjoy.


