# CLIPS
[![Build Status](https://magnum.travis-ci.com/BYU-ODH/CLIPS.svg?token=ckqz5jFpqLxNdR6qseWY)](https://magnum.travis-ci.com/BYU-ODH/CLIPS)
[![Code Climate](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/badges/75b9acd8c4700c9462e2/gpa.svg)](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/feed)
[![Test Coverage](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/badges/75b9acd8c4700c9462e2/coverage.svg)](https://codeclimate.com/repos/55357094e30ba07d9e002cc0/coverage)

The latest incarnation of WebCLIPS

![Beloved Mascot](alex.jpg)

## Table of Contents
1. [Getting Started](#getting)
2. [Code Quality](#code)
  2. [Pylint](#pylint)
  2. [pytest](#pytest)
3. [Migrations](#migrations)
  1. [Alembic](#alembic)
4. [API](#api)
  1. [API Authorization](#apiAuthorization)
  2. [apiDoc](#apiDoc)

###Getting Started
1. Make sure you have Phython 3 installed on your computer.

*For instructions on how to get Python running on a Windows 10 machine, see [here] (https://help.github.com/articles/relative-links-in-readmes/). and [here] (https://github.com/rbrinck/Programming-for-Windows/blob/master/PythonSetup.md)*

2. Make sure you have pip and that it's working. An easy way to do this is to run `pip3 --version` or `pip --version` depending on which you feel like using. You can also just do a search on your drive. If it's not there, you might want to look into getting an updated version of Python.

*Note: If you also have Perl installed, this has it's own pip that your Command Prompt will default to unless you specify "pip.exe"*

3. If you're not already there, cd to your CLIPS directory.

4. As mentioned below in "Code Quality", you may need to install several tools by running `sudo pip3 install -r requirements.txt` (or if you're in Windows, you can skip `sudo`).

5. To start the server, run
`python3 startup.py` in your command line in the CLIPS directory on your computer.

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
