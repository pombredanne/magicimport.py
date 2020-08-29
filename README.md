# magicimport.py

We're making L5 autonomous cars, but for some reason we can't seem to make L5 autonomous software that "just works".

The idea of magicimport.py is to allow an arbitrary piece of Python code to fetch its own dependencies and versions at runtime and "just run", no questions asked, without fuss.
Behind the hood it uses virtualenv to create a virtual environment and install its dependencies there without messing with your system Python packages.

The ONLY package it will install to your system (and in user-space, only) is virtualenv itself, if you don't already have it.

Normally you would do this:
```
import tornado
```
and of course your system may complain that tornado wasn't found. And so you want to create a virtualenv, go Googling for how to create a virtualenv, create the virtualenv, install tornado, and run your python script.

With magicimport.py you can do this:
```
from magicimport import magicimport
tornado = magicimport("tornado")
```
and BAM, you have tornado, no questions asked.

You can even specify a version number that you would like, e.g.
```
from magicimport import magicimport
tornado = magicimport("tornado", version = "4.5")
```

and you will get that exact version.

Enjoy!

## FAQ

0. Is this production ready?

No. Don't use this in production. This is mostly just a convenience hack for small personal projects.

1. Does it work with Python 2?

No. Not yet, but people should move to Python 3 already.
