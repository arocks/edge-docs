# Welcome to the edge!

__edge__ - a rapid, cutting-edge Django project skeleton. 

![screenshot](http://i.imgur.com/PEyLbLWl.jpg)

## Features

* Python 3 support - e.g. Uses pathlib for paths in settings
* Django 1.7 support - e.g. south dependency removed
* Sign-in, Sign-up and Logouts - Basic user registration and sign-ins using crispy forms
* Bootstrap bundled - Snazzy Bootstrap 3 based home page and admin out of the box
* Clean start - Based on Django 1.7 project structure
* Secrets Secure - Picks SECRET_KEY from environment as a best practice
* Minimal dependencies - Only essential packages listed in requirements.txt not all recommended ones

__Warning__: Software is currently beta and bleeding edge.

## Motivation

* Django programmers are not designers. They need a better starting point say, with Bootstrap.
* Many project skeletons contain recommended packages making them bloated.
* None of the project skeletons were Python 3 and Django 1.7 compatible at the time of creating the project.
* Simple user authentication for rapid prototyping
* Better layout (a subjective preference) that is intuitive to use.

More details in this [blog post](http://arunrocks.com/introducing-edge-a-modern-django-project-template/)

## Which packages were included and why?

* django-environ - By default, settings has environment specific information. This package helps you define such variables in the environment which is more secure.
* django-crispy-forms - Provides the Sign-in and Sign-up forms.
* django-braces - Essential set of mixins used for the included views
* django-admin-bootstrapped - Added Bootstrap 3 theme to the admin

## Quick start:

Skip the next set of commands if you know how to create a virtual environment in Python 3:

    $ python3.4 -m venv py34env
    $ . py34env/bin/activate

Use the following commands but change `my_proj` at end of first command to the name of your project:

    $ django-admin.py startproject --template=https://github.com/arocks/edge/archive/master.zip --extension=py,md,html,env my_proj
    $ cd my_proj
    $ pip install -r requirements.txt 
    $ cd src
    $ python manage.py migrate

Project is on Github: [https://github.com/arocks/edge](https://github.com/arocks/edge)

## Customisation Tips:

1. Brand Name: Edit `src/templates/_brandname.html` 
2. Logo: Change `src/static/site/img/logo.png`
3. Settings: Set environment vars. Move `local.env` out of git.
4. CSS: Change `src/static/site/css/main.css`
5. Authentication: Use a more complete authentication solution like django-allauth that handle password resets, email ids etc.

## Changelog

=== (2014-09-12) ===

  * Added django-environ and pathlib
  * Added Sign-in, Sign-up, logout functionality. 
  * Admin now has bootstrap theme.

=== (2014-09-01) ===

  * initial release

## Screens

### After Log-in
![After Log-in](http://i.imgur.com/aCYser3l.jpg)

### Anonymous Visitor
![Anonymous Visitor](http://i.imgur.com/PEyLbLWl.jpg)

## Credits

- Background photo courtesy: [Death to the Stock Photo](http://deathtothestockphoto.com/)
- Social icons: [Font Awesome icons](http://fontawesome.io/)

## Proposed Features

- Add a simple user profile model <https://github.com/arocks/edge/issues/2>
- Add py.test in the dev env. Change app template to include it.
- Include `django compressor`. Full python sass pipeline might be ambitious.
  - Short [tip](http://jamie.curle.io/blog/using-pyscss-django_compressor/) on django compressor and pyscss
  - Twitter [scss port](https://github.com/twbs/bootstrap-sass). Adding as a [sub-module](http://stackoverflow.com/questions/5252450/using-someone-elses-repo-as-a-git-submodule-on-github) in github.
  - See also [django-pyscss](https://github.com/fusionbox/django-pyscss)
  - Bootstrap setup in Django tutorial [part 2](http://www.lasolution.be/blog/using-your-own-flavor-bootstrap-django-project-part-2.html)
- Extract navbar into a `_navbar.html` with a navigation pattern
- Add 404.html and 500.html
- Include a fabfile (or some other Py 3 compatible deployer like Paver) to push to a Cloud host 

Completed or partially done:

- Admin themed with bootstrap. Try to have foreign key drop down.
  - Django suit is not fully free. See Pricing.
  - [Grappelli](http://grappelliproject.com/) (not bootstrap :( but so many good features)
  - [django-admin-bootstrapped](https://github.com/django-admin-bootstrapped/django-admin-bootstrapped) (light but no foreign key part) [Intro post](https://riccardo.forina.me/bootstrap-your-django-admin-in-3-minutes/)
  - [django-admin-bootstrap Responsive](https://github.com/douglasmiranda/django-admin-bootstrap/)
  - Or simply override the templates in admin folder
- Add password reset and change [forms](http://www.reddit.com/r/django/comments/2hp91t/barebones_django_authentication_for_the/)
- Add messages (See [simple example](http://stackoverflow.com/a/16711962/3107299) )
- Add crispy forms for bootstrapped forms
- Sign in, sign out and sign up forms using crispy
- Include Django Debug toolbar
