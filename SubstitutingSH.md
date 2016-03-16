#Substituting "sh"

1. run `pip install pbs` in your command line

You may have to separately download some packages, like Xenon, and edit one of their files so that they search for *pbs* instead of *sh*.

####Using Xenon as an example of how to do this:
This is an example of how to fix an error for Xenon, but if you ever get an error along the lines of "`ImportError: sh 1.11 is currently only supported on linux and osx. please install pbs 0.110 (http://pypi.python.org/pypi/pbs) for windows support.`", follow the following steps (but with your own traceback information and only following steps 3-5):

1. Follow the instructions [here](https://pypi.python.org/pypi/setuptools) to download Pythons setuptools.
2. run `pip install xenon`
3. Identify where the error occurs. (For me: "C:Users\[`Username`]\AppData\Local\Temp\pip-build-eeuuojms\sh\sh.py, line 37, in <module> support . . .")
    1. It will whine again that you need to install pbs 0.110, even though you already have.
4. Go to that file and change the line it gave you.
5. Replace "sh 1.11" with "pbs 0.110".
6. run `pip install xenon` again.
    1. If this isn't working, just clone [this repository](https://github.com/rubik/xenon/), then run `python setup.py` in whatever folder you cloned the xenon repository to.
7. Magic! It should be working now. If not, please send me a message so I can improve my tutorial.
 
If you run into any "sh" errors elsewhere, follow the 
