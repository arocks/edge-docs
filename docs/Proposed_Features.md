- [ ] Add py.test in the dev env. Change app template to include it.
- [ ] Include `django compressor`. Full python sass pipeline might be ambitious.
    - Short [tip](http://jamie.curle.io/blog/using-pyscss-django_compressor/) on django compressor and pyscss
    - Twitter [scss port](https://github.com/twbs/bootstrap-sass). Adding as a [sub-module](http://stackoverflow.com/questions/5252450/using-someone-elses-repo-as-a-git-submodule-on-github) in github.
    - See also [django-pyscss](https://github.com/fusionbox/django-pyscss)
    - Bootstrap setup in Django tutorial [part 2](http://www.lasolution.be/blog/using-your-own-flavor-bootstrap-django-project-part-2.html)
- [ ] Add 404.html and 500.html
- [ ] Include a fabfile (or some other Py 3 compatible deployer like Paver) to push to a Cloud host 
- [ ] Add a template debugging tag for breaking pdb or any other debugger?

### Completed or partially done:

- [X] Logging into files for debugging: http://www.caktusgroup.com/blog/2015/01/27/Django-Logging-Configuration-logging_config-default-settings-logger/
- [X] Add a better debugger like werkzeug by [adding a few lines to wsgi.py](http://stackoverflow.com/questions/17689797/how-to-use-werkzeug-debugger-in-dotcloud?noredirect=1#comment26054122_17689797)
- [x] Add a simple user profile model <https://github.com/arocks/edge/issues/2>
- [x] Extract navbar into a `_navbar.html` with a navigation pattern
- [x] Admin themed with bootstrap. Try to have foreign key drop down.
    - Django suit is not fully free. See Pricing.
    - [Grappelli](http://grappelliproject.com/) (not bootstrap :( but so many good features)
    - [django-admin-bootstrapped](https://github.com/django-admin-bootstrapped/django-admin-bootstrapped) (light but no foreign key part) [Intro post](https://riccardo.forina.me/bootstrap-your-django-admin-in-3-minutes/)
    - [django-admin-bootstrap Responsive](https://github.com/douglasmiranda/django-admin-bootstrap/)
    - Or simply override the templates in admin folder
- [x] Add password reset and change [forms](http://www.reddit.com/r/django/comments/2hp91t/barebones_django_authentication_for_the/)
- [x] Add messages (See [simple example](http://stackoverflow.com/a/16711962/3107299) )
- [x] Add crispy forms for bootstrapped forms
- [x] Sign in, sign out and sign up forms using crispy
- [x] Include Django Debug toolbar
