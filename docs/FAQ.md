## Installation

### Does Edge support Python 2.7?

Yes, since Edge 2.0 we have a common codebase supporting Python 2.x and 3.x

### What is `local.env` file and why should I copy it?

Django requires you to mention certain confidential information in `settings.py` like your SECRET_KEY and database connection details. This could get added to your git repository and reach the wrong hands. Ideally, Django Edge can pick these details from the environment variables (say set in your Python virtual env `activate` script).

However, this can be cumbersome to setup while you want to quickly start working on a new project. So you have the option of using a `.env` file where all the environment variables can be defined. When a new project is created a sample `local.sample.env` will be provided which can be used for development.

Later you can use environment variables say in production which will override the values in your `local.env`. For security reasons, `local.env` will be ignored by git. So make sure you have noted the details in this file seperately.

### Why do I keep getting "OSError: decoder zip not available" errors?

This is a problem with Pillow library being unable to handle PNG files. Since Pillow is usually compiled while installing the dependencies in `requirements.txt`, you will need to reinstall Pillow.

On Ubuntu, the fix is running the following commands (in your virtualenv):

    $ pip uninstall Pillow
    $ sudo apt-get install libjpeg-dev zlib1g-dev
    $ pip install -I Pillow

## Sign up and Sign in

### I want to add an extra field or step to signup or sign in process. Where should I start?

The accounts app contains most of the sign up and sign in functionality. The views are all class based and can be easily extended. There are two places you can start:

* `src/accounts/forms.py`: You can add extra fields like captchas here
* `src/accounts/views.py`: You can change the functionality like sending confirmation emails here

## Design and UI

### How can I customized the appearance in terms of logo, icon, Bootstrap theme etc?

1. Brand Name: Edit `src/templates/_brandname.html`. Or use a one-liner:

        echo "Fantasy Quidditch" > src/templates/_brandname.html
 
2. Logo: Change `src/static/site/img/logo.png`. Or use a one-liner:

        curl -o src/static/site/img/logo.png http://icons.iconarchive.com/icons/iconka/harry-potter/32/broom-icon.png

2. Banner: Change `src/static/site/img/banner.jpg`. Or use a one-liner:

        curl -o src/static/site/img/banner.jpg https://farm8.staticflickr.com/7153/6709315743_5412d64169_o_d.png

4. Bootstrap Theme: Change `src/static/bootstrap/css/bootstrap.min.css`. Or use a one-liner:

        curl -o src/static/bootstrap/css/bootstrap.min.css http://bootswatch.com/paper/bootstrap.min.css

### I don't prefer a full height cover image. How can I change it?

You can reduce the height of the jumbotron, say add this to the end of in `main.css` to make the cover image half the height of the browser window:

    .corporate-jumbo { height: 50%; }

## Deployment

### How to run this with gunicorn?

In production you will want to use the `settings/production.py`. Make sure that your `wsgi.py` picks up the right settings. You can do this in either one of these three ways:

1. Set the environment variable `DJANGO_SETTINGS_MODULE` to point to `my_proj.settings.production`. This can be mentioned in your virtualenv's activate script.

2. Pass a [commandline argument](http://gunicorn-docs.readthedocs.org/en/latest/settings.html#raw-env) while invoking gunicorn:

3. Edit or copy the `wsgi.py` with the following line:

        os.environ.setdefault("DJANGO_SETTINGS_MODULE", "my_proj.settings.production")

_[Thanks to abadger1406 for this question]_
