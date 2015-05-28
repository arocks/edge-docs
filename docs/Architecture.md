Let's have a very high-level view of the components within a project created with Edge.

Have a look at the project layout of an Edge project:

    Top-directory
    ├── docs
    ├── logs
    ├── README.md
    ├── requirements
    │   ├── base.txt
    │   ├── development.txt
    │   └── production.txt
    ├── requirements.txt
    └── src
        ├── Your project name
        │   ├── __init__.py
        │   ├── logger.py
        │   ├── settings
        │   │   ├── base.py
        │   │   ├── development.py
        │   │   ├── local.sample.env
        │   │   └── production.py
        │   ├── urls.py
        │   ├── views.py
        │   └── wsgi.py
        ├── accounts
        │   ├── admin.py
        │   ├── forms.py
        │   ├── migrations
        │   ├── models.py
        │   ├── templates
        │   ├── tests.py
        │   ├── urls.py
        │   └── views.py
        ├── manage.py
        ├── media
        ├── profiles
        │   ├── admin.py
        │   ├── apps.py
        │   ├── forms.py
        │   ├── migrations
        │   ├── models.py
        │   ├── signals.py
        │   ├── templates
        │   ├── tests.py
        │   ├── urls.py
        │   └── views.py
        ├── static
        │   ├── bootstrap
        │   │   ├── css
        │   │   ├── fonts
        │   │   └── js
        │   └── site
        │       ├── css
        │       ├── ico
        │       ├── img
        │       └── js
        └── templates


An Edge project will have two apps by default:

* accounts
* profiles

### Accounts App

This app is mainly a set of views that can handle user signups, login, logout and password changes. If you want to change any of these views or the information shown in these forms, you should start here. You can easily extend these views as they are class-based.

### Profiles App

This app contains the user profile model, containing all the user details apart from authentication data. Any application specific user profile fields like birthdate or designation could go here.

By default, the base profile contains:

* Profile Picture: This is also shown as a thumbnail on the upper left before the user's name 
* Bio: A brief write-up about the user in their own words.
* Email Verified (internal field): Since the default workflow accepts your email address as you login without verification (for convenience), you can always send a verification mail to confirm if the user provided email address was correct.
* Slug (internal field): A 32 character unique identifier for the user. This is used to generate unique URLs for each user's profile without leaking their user ID database field.

The views and forms have been written to show and edit user information. Here user information is presented by combining the user authentication information from `User` model and user profile fields. From a user's point of view they would like to see/edit their details together.
