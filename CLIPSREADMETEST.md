# CLIPS
[![Build Status](https://magnum.travis-ci.com/BYU-ODH/CLIPS.svg?token=ckqz5jFpqLxNdR6qseWY)](https://magnum.travis-ci.com/BYU-ODH/CLIPS)
[![Code Climate](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/badges/75b9acd8c4700c9462e2/gpa.svg)](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/feed)
[![Test Coverage](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/badges/75b9acd8c4700c9462e2/coverage.svg)](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/coverage)

The latest incarnation of WebCLIPS

![Beloved Mascot](alex.jpg)

## Table of Contents
1. [Getting Started](#getting-started)
2. [Code Quality](#code-quality)
  2. [Pylint](#pylint)
  2. [pytest](#pytest)
3. [Migrations](#migrations)
  1. [Alembic](#alembic)
4. [API](#api)
  1. [API Authorization](#apiauthorization)
  2. [apiDoc](#apidoc)

###Getting Started
1. Make sure the following are installed on your computer and in your path.
    1. [Phython](https://www.python.org/downloads/) (Any of the version 3s will work, but be sure you install the Python for your OS)
    2. [PostgreSQL](http://www.postgresql.org/download/)
    3. [Psycopg](http://initd.org/psycopg/download/)
    4. (May not be necessary for everyone, but will be for Windows users): PostgreSQL Frontend [here?](https://sourceforge.net/projects/psql/)

    *For instructions on how to get Python running on a Windows 10 machine, see [here] (https://github.com/rbrinck/Programming-for-Windows/blob/master/PythonSetup.md)*

2. Add `CLIPS_DATABASE_URI=postgresql://username:password@host/db_name` to your environment variables.
    1. To do so, follow steps 1-6.1 in [this tutorial](https://github.com/rbrinck/Programming-for-Windows/blob/master/PythonSetup.md), but instead of clicking "edit" in step 6.3, click "new" and insert "CLIPS_DATABASE_URI" as the "variable name" and "postgresql://yourusername:yourpostgrespassword@host/db_name" as the "variable value".
    *If you don't remember creating a username, it's probably "postgres", which is currently the default.*

3. Make sure you have pip and that it's working. An easy way to do this is to run `pip3 --version` or `pip --version`. You can also just do a search on your drive. If it's not there, you might want to look into getting an updated version of Python.
    1. You can upgrade your pip by running `python -m pip install --upgrade pip`.
    
    *Note: If you also have Perl installed, this has it's own pip that your Command Prompt will default to unless you specify "pip.exe". (This will apply any time you want to use the `pip` command in Python.)*

4. If you're not already there, cd to your CLIPS directory.

5. As mentioned below in "Code Quality", you may need to install several tools by running `sudo pip3 install -r requirements.txt` (or if you're in Windows, you can skip `sudo`).
    1. If you're having problems, trying running `pip install sh`.
    
    *"sh" is only supported by linux and osx. For instructions on how to circumvent this problem, see [this page](https://github.com/rbrinck/Programming-for-Windows/blob/master/SubstitutingSH.md)*, then run `pip3 install -r requirements.txt` again.
    *You may have to install both [xenon](https://www.google.com/search?q=python+xenon&rlz=1C1GGGE_enUS479US480&oq=python+xenon&aqs=chrome..69i57j0l5.2419j0j7&sourceid=chrome&ie=UTF-8) and [tornado](https://pypi.python.org/pypi/tornado/4.2.1) separately.*
    *If you're still having problems, you may have to manually change which version "requirements.txt" has to match the version you installed*

6. To start the server, run `python3 startup.py` in your command line in the CLIPS directory on your computer.
    
   *If this doesn't work, try `python startup.py`*

###Code Quality
We use several tools to check the quality of our code.  These can all be installed locally by running:<br>
`sudo pip3 install -r requirements.txt`

####Pylint
We are using pylint to check the style and formatting of our code.

Run Locally:<br>
`./runlint.sh`

####pytest
We use pytest for testing.  Travis will fail any build will less than 90% code coverage.

Running tests requires specifying a test database. Set:<br>
`CLIPS_TEST_DATABASE_URI=postgresql://username:password@host/db_name`<br>

Run Tests Locally:<br>
`./runtest.sh`

###Migrations

####Alembic
We use Alembic to run migrations.  Alembic expects a global variable to know which database to connect to.
Set:<br>
`CLIPS_DATABASE_URI=postgresql://username:password@host/db_name`<br>
substituting the information for your setup.<br>

Run Latest Migrations:<br>
`alembic upgrade head`

###API

Start up API Locally:<br>
`python3 startup.py`

Once started, navigate to [localhost:8888](http://localhost:8888) to access the API

####APIAuthorization
For endpoints that require authorization, add an entry to the user table (a uuid value of your choice) and send that uuid in the Authorization header.<br>
`INSERT INTO public.user VALUES ('6b3ae5e8-30a6-11e5-a0b0-34e6d71ecad3');`<br>
`curl -i http://localhost:8888/api/1.0.0/question -H "Authorization: 6b3ae5e8-30a6-11e5-a0b0-34e6d71ecad3"`

####apiDoc
We use [apiDoc](http://apidocjs.com/) to document the API.  Be sure to add apiDoc comments to any new API function to keep the docs up-to-date.

Install apiDoc Locally:<br>
`sudo npm install apidoc -g`

Generate Docs:<br>
`apidoc`
