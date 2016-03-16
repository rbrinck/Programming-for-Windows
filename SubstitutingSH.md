#Substituting "sh"

1. run `pip install pbs` in your command line

You may have to separately download some packages, like Xenon, and edit one of their files so that they search for *pbs* instead of *sh*.

####Using Xenon as an example of how to do this:
1. Follow the instructions [here](https://pypi.python.org/pypi/setuptools) to download Pythons setuptools.
2. run `pip install xenon`
    1. If this isn't working, just clone [this repository](https://github.com/rubik/xenon/) and try again.
3. Notice where the error occurs. (For me: "C:Users\*Username*\AppData\Local\Temp\pip-build-eeuuojms\sh\sh.py", line 37, in <module> support." % __version__)"
    1. It will whine again that you need to install pbs 0.110, even though you already have.
4. Go to that file and change the line it gave you.
5. Replace "sh 1.11" with "pbs 0.110".
6. run `pip install xenon` again.
7. Magic! It should be working now. If not, please send me a message so I can improve my tutorial.
