Newsletter Subscription
=======================

---

This is a **Bolt** extension. You can read more about awesome Bolt CMS built on top of Silex microframework at Bolt.cm. 

---

The "Newsletter Subscription" extension provides automated managment of a list of newsletter subscribers. It does not deal with the actual sending of the newsletter, only with the subscription/desubscription of users.  

License
-------

This extension is licensed under the MIT license.


Basic usage
-----------

To use it, just insert the following into a template:

    {{ newslettersubscription() }}

    
Features
--------

With just the above Twig function, the extension provides:

- A database table to store your subscribers' data.
- A subscribe form.
- Two-phase subscription confirmation:
    1. User submits the subscription form.
    2. User receives a confirmation email with a confirmation link.
    3. User clicks the confirmation link and the subscription is confirmed.
- Cancel subscription via an unsubscription link.
- Logged-in users (Admins and Developers) are shown a download link to download the list of subscribers as a CSV file.
- Subscription, confirmation and unsubscription emails are sent to users.
- Subscription and unsubscription notification emails are sent to a predefined address.    

Settings
--------

There are a lot of settings available in `config.yml`. All of them are self documented in the file itself, so there is no point in repeating them here. Just remember that `config.yml.dist` stores all the default values, so you only need to set a given setting if you want to overwrite defaults.

How to download the subscribers list
------------------------------------

First of all, provide a value for `admin_secret` setting different from the default.

Then, if you are logged in as *Developer* or *Administrator* you will see the option to download the subscribers CSV file. Just click the link and the file wil start downloading.  
 
You can also download the file without using the browser at all. Just use the download link in some other application able to perform http downloads. 

Example:

    wget "http://mybolt.com/page/newsletter?adminaction=download&secret=abc123" -O subscribers.csv  
    
or 
    
    curl -s "http://mybolt.com/page/newsletter?adminaction=download&secret=abc123" > subscribers.csv

**NOTE**: The download link will only work if the following conditions are all met:

- The `admin_secret` setting has a value that is different from the default (`abc123` in the above example).
- The download url provides a `secret` argument with the same value as `admin_secret`.

So unauthorized persons cannot get the valuable list of your subscribers. 


TO-DO
-----

- Bolt does not (yet?) provide a way for extensions to add an administrative interface, so there is no easy way to administer the subscribers list. If you want to modify or delete something you'll have to use some database access application (i.e. phpMyAdmin).

 
     
