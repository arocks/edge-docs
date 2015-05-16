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

In production you will want to use the production `settings.py`. Make sure that your `wsgi.py` picks up the right settings. You can do this in two ways:

1. Set the environment variable `DJANGO_SETTINGS_MODULE` to point to `my_proj.settings.production`
2. Edit or copy the `wsgi.py` with the following line:

        os.environ.setdefault("DJANGO_SETTINGS_MODULE", "my_proj.settings.production")

_[Thanks to abadger1406 for this question]_
