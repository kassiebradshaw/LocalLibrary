# Django Tutorial: Local Library

Project by: *Kassie Bradshaw*

Started: *11-02-2021*

## [Part 2 : Creating a skeleton website](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/skeleton_website)

Date Started: *11-02-2021*

* Prerequisites:
* Objective:

**Overview**:

This article shows how you can create a "skeleton" website, which you can then populate with site-specific settings, paths, models, views, and templates (we discuss these in later articles).

---

## [Part 3: Using Models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

Date: *11-02-2021*

* Prerequisites: Django Tutorial Part2: Creating a skeleton website
* Objective: To be able to design and create your own models, choosing fields appropriately

**Overview**:

Django web applications access and manage data through Python objects referred to as models. Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc. The definition of the model is independent of the underlying database — you can choose one of several as part of your project settings. Once you've chosen what database you want to use, you don't need to talk to it directly at all — you just write your model structure and other code, and Django handles all the dirty work of communicating with the database for you.

This tutorial shows how to define and access the models for the LocalLibrary website example.

**Notes to refer back to in this section**:

* Fields
* Field arguments
* Field types
* Every model should, at the very least, have a `__str__` method
* Also recommended: `get_absolute_url()` --> returns a URL for displaying individual model records on the website
  * Don't forget to import at the top --> `from django.urls import reverse`

    ```Python
        def get_absolute_url(self):
            """Returns the url to access a particular instance of the model"""
            return reverse('model-detail-view', args=[str(self.id)])
    ```

* Meta to set default ordering

---

## [Part 4: Django admin site](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)

Date: *11-02-2021*

* Prerequisites: Django Tutorial Part3: Using models
* Objective: To understand the benefits and limitations of the Django admin site, and use it to create some records for our models

**Overview**:

The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records. This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data. The admin application can also be useful for managing data in production, depending on the type of website. The Django project recommends it only for internal data management (i.e. just for use by admins, or people internal to your organization), as the model-centric approach is not necessarily the best possible interface for all users, and exposes a lot of unnecessary detail about the models.

All the configuration required to include the admin application in your website was done automatically when you created the skeleton project (for information about actual dependencies needed, see the Django docs here). As a result, all you must do to add your models to the admin application is to register them. At the end of this article we'll provide a brief demonstration of how you might further configure the admin area to better display our model data.

After registering the models we'll show how to create a new "superuser", login to the site, and create some books, authors, book instances, and genres. These will be useful for testing the views and templates we'll start creating in the next tutorial.

---
