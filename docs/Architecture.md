Let's have a very high-level view of the components within a project created with Edge.

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
