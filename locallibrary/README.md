# Django Tutorial: Local Library

Project by: *Kassie Bradshaw*

Started: *11-02-2021*

## [Part 2 : Creating a skeleton website](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/skeleton_website)

Date Started: *11-02-2021*

|||
| --- | --- |
| **Prerequisites:** | --- |
| **Objective:** | --- |
|

**Overview**:

This article shows how you can create a "skeleton" website, which you can then populate with site-specific settings, paths, models, views, and templates (we discuss these in later articles).

---

## [Part 3: Using Models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

Date: *11-02-2021*

|||
| --- | --- |
| **Prerequisites:** | Django Tutorial Part2: Creating a skeleton website |
| **Objective:** | To be able to design and create your own models, choosing fields appropriately |
|

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

|||
| --- | --- |
| **Prerequisites:** | Django Tutorial Part3: Using models |
| **Objective:** | To understand the benefits and limitations of the Django admin site, and use it to create some records for our models |
|

**Overview**:

The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records. This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data. The admin application can also be useful for managing data in production, depending on the type of website. The Django project recommends it only for internal data management (i.e. just for use by admins, or people internal to your organization), as the model-centric approach is not necessarily the best possible interface for all users, and exposes a lot of unnecessary detail about the models.

All the configuration required to include the admin application in your website was done automatically when you created the skeleton project (for information about actual dependencies needed, see the Django docs here). As a result, all you must do to add your models to the admin application is to register them. At the end of this article we'll provide a brief demonstration of how you might further configure the admin area to better display our model data.

After registering the models we'll show how to create a new "superuser", login to the site, and create some books, authors, book instances, and genres. These will be useful for testing the views and templates we'll start creating in the next tutorial.

---

## [Part 5: Creating our home page](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page)

Date: *11-02-2021 to 11-04-2021*

|||
| --- | --- |
| **Prerequisites:** | Read the [Django Introduction](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction). Complete previous tutorial topics (including [Django Tutorial Part 4: Django admin site](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)) |
| **Objective:** | Learn to create simple url maps and views (where no data is encoded in the URL), get data from models, and create templates. |
|

**Overview**:

After we defined our models and created some initial library records to work with, it's time to write the code that presents that information to users. The first thing we need to do is determine what information we want to display in our pages, and define the URLs to use for returning those resources. Then we'll create a URL mapper, views, and templates to display the pages.

The following diagram describes the main data flow, and the components required when handling HTTP requests and responses. As we already implemented the model, the main components we'll create are:

URL mappers to forward the supported URLs (and any information encoded in the URLs) to the appropriate view functions.
View functions to get the requested data from the models, create HTML pages that display the data, and return the pages to the user to view in the browser.
Templates to use when rendering data in the views.

![Overview Diagram](assets/django-tutorial-part-5-overview.png)

As you'll see in the next section, we have 5 pages to display, which is too much information to document in a single article. Therefore, this article will focus on how to implement the home page, and we'll cover the other pages in a subsequent article. This should give you a good end-to-end understanding of how URL mappers, views, and models work in practice.

---

## [Part 6: Generic list and detail views](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views)

Date: *11-04-2021 - 11-27-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 5 |
| **Objective:** | To understand where and how to use generic class-based views, and how to extract patterns from URLS and pass the information to views. |
|

**Overview**:

In this tutorial we're going to complete the first version of the LocalLibrary website by adding list and detail pages for books and authors (or to be more precise, we'll show you how to implement the book pages, and get you to create the author pages yourself!)

The process is similar to creating the index page, which we showed in the previous tutorial. We'll still need to create URL maps, views, and templates. The main difference is that for the detail pages, we'll have the additional challenge of extracting information from patterns in the URL and passing it to the view. For these pages, we're going to demonstrate a completely different type of view: generic class-based list and detail views. These can significantly reduce the amount of view code needed, making them easier to write and maintain.

The final part of the tutorial will demonstrate how to paginate your data when using generic class-based list views.

---

<!-- |||
| --- | --- |
| **Prerequisites:** | --- |
| **Objective:** | --- |
| -->
