# Welcome to the edge v2.0!

[__edge__](https://github.com/arocks/edge/) - a rapid, cutting-edge Django project skeleton. More screenshots below:

![screenshot](http://i.imgur.com/hvmrudL.jpg)

## Features

* Python 2.7 and 3.4 support - the same codebase works on the latest Python versions
* Django 1.7 support - e.g. no south dependency
* Sign-ups and Log-ins - Basic user registration, log-ins, forgot password etc. using crispy forms
* User Profiles - extendible user profile with great defaults like profile picture
* Bootstrap bundled - Themed Bootstrap 3 based home page and admin out of the box
* Clean start - Based on Django 1.7 project structure
* Secrets Secure - Picks SECRET_KEY from environment as a best practice
* Minimal dependencies - Only essential packages listed in requirements.txt not all recommended ones

__Warning__: Software is currently beta and bleeding edge.

## Motivation

* Django programmers are not designers. They need a better starting point say, with Bootstrap.
* Writing code for signup, login and user profiles seems repetitive in every project.
* Many project skeletons contain numerous recommended packages making them bloated.
* None of the project skeletons were Python 3 and Django 1.7 compatible at the time of creating the project.
* Simpler and less annoying user authentication for rapid prototyping
* Better layout (a subjective preference) that is intuitive to use.

More details in this [blog post](http://arunrocks.com/introducing-edge-a-modern-django-project-template/)

## Which packages were included and why?

* django-environ - By default, settings has environment specific information. This package helps you define such variables in the environment which is more secure.
* django-authtools - Custom user model and class based auth views.
* django-crispy-forms - Provides the Sign-in and Sign-up forms.
* django-braces - Essential set of mixins used for the included views
* django-admin-bootstrapped - Added Bootstrap 3 theme to the admin
* easy-thumbnails - (optional) for profile picture thumbnails.

## Quick start:

Skip the next set of commands if you already know how to create a virtual environment. Here is how to create a new virtual environment in Python 3.4 using the built-in `venv` library:

    $ python3.4 -m venv py34env
    $ . py34env/bin/activate

Check if Django is installed. It is needed for `django-admin` command to work.

    $ pip install -U django

Use the following commands but change `my_proj` (at end of first command and other places) to the name of your project:

    $ django-admin.py startproject --template=https://github.com/arocks/edge/archive/master.zip --extension=py,md,html,env my_proj
    $ cd my_proj
    $ pip install -r requirements.txt 
    $ cd src
    $ python manage.py migrate
    $ python manage.py createsuperuser

On Windows, you might want to install the requirements file using wheels (especially if you don't have a C compiler) using the following command instead:

    $ pip install --use-wheel -r requirements.txt 

On some Linux systems, Pillow will not install unless you install a C compiler:

    $ sudo apt-get install python3-dev python3-setuptools

Now, you are all set. Adding a new app say `polls` would be like:

    $ python manage.py startapp polls

Please raise an issue on the [Github project page](https://github.com/arocks/edge) if you notice any bugs and would like to request features.

# Table of contents

* [FAQ (Frequently Asked Questions)](FAQ.md)
* [Tutorials](Tutorials.md)
* [Architecture](Architecture.md)
* [Credits](Credits.md)
* [Proposed Features](Proposed_Features.md)
* [Changelog](Changelog.md)

## Screens

### Anonymous Visitor
![Anonymous Visitor](http://i.imgur.com/fSyrWq2.jpg)

### Login Page
![login page](http://i.imgur.com/qdBIn94.jpg)

### After Log-in
![After Log-in](http://i.imgur.com/hvmrudL.jpg)

### User's Profile page
![Profile page](http://i.imgur.com/etvmQG4.jpg)

### Video Demo

[![Demo](http://share.gifyoutube.com/y4V1bw.gif)](http://youtu.be/ff_xRmG27mg)

[View on YouTube](http://youtu.be/ff_xRmG27mg)


