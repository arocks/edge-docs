## Installation

### Does Edge support Python 2.7?

Yes, since Edge 2.0 we have a common codebase supporting Python 2.x and 3.x

### What is `local.env` file and why should I copy it?

Django requires you to mention certain confidential information in `settings.py` like your SECRET_KEY and database connection details. This could get added to your git repository and reach the wrong hands. Ideally, Django Edge can pick these details from the environment variables (say set in your Python virtual env `activate` script).

However, this can be cumbersome to setup while you want to quickly start working on a new project. So you have the option of using a `.env` file where all the environment variables can be defined. When a new project is created a sample `local.sample.env` will be provided which can be used for development.

Later you can use environment variables say in production which will override the values in your `local.env`. For security reasons, `local.env` will be ignored by git. So make sure you have noted the details in this file seperately.

### Why do I get an ImproperlyConfigured exception about "SECRET_KEY setting must not be empty", after installation?

You need to copy `local.env` file as mentioned in the installation steps. The previous answer explains why this is needed.

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

### How to use other databases like PostgreSQL, MySQL etc.?

You will need to change the `DATABASE_URL` in your environment's `settings.py`. Unlike the default Django settings, you do not have to set `DATABASES` to a large dictionary of key-value pairs. Instead, you can set a database URL in `DATABASE_URL` containing the engine, username, password, port etc.

By default, this is set to `sqlite:///db.sqlite3` to use a SQLite3 database. To use other databases use the following URL patterns (based on [dj-database-url](https://github.com/kennethreitz/dj-database-url)):

Engine |	Django Backend | URL
-------|-------------------|---------
PostgreSQL |	django.db.backends.postgresql_psycopg2 |	postgres://USER:PASSWORD@HOST:PORT/NAME
PostGIS |	django.contrib.gis.db.backends.postgis |	postgis://USER:PASSWORD@HOST:PORT/NAME
MySQL |	django.db.backends.mysql |	mysql://USER:PASSWORD@HOST:PORT/NAME
MySQL (GIS) |	django.contrib.gis.db.backends.mysql |	mysqlgis://USER:PASSWORD@HOST:PORT/NAME
SQLite |	django.db.backends.sqlite3 |	sqlite:///PATH

For example, a PostgreSQL database setting might be:

    DATABASE_URL=postgres://admin_user:SeCRet143232@127.0.0.1:5432/database

Notice that special characters can be URL encoded (say in the password) but it is better to avoid them.

### How to run this with gunicorn?

Pass the WSGI callable as a [commandline argument](http://gunicorn-docs.readthedocs.org/en/latest/run.html#django) while invoking gunicorn (change `my_proj` to your Edge project's name):

    { venv_path }/bin/gunicorn my_proj.wsgi -c gunicorn.conf.py -p gunicorn.pid

In production you would want to use the `settings/production.py`. Hence, `wsgi.py` points to the production settings by default. It will already have a line like the following:

    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "my_proj.settings.production")

In case you want to run gunicorn with a different settings file say `settings/staging.py` you will need to set the environment variable `DJANGO_SETTINGS_MODULE`, say like this:

    { venv_path }/bin/gunicorn --env DJANGO_SETTINGS_MODULE=my_proj.settings.staging my_proj.wsgi -c gunicorn.conf.py -p gunicorn.pid

_[Thanks to abadger1406 for this question]_
