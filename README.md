# Django Tutorial: Local Library

Project by: *Kassie Bradshaw*

Started: *11-02-2021*

## [Part 2 : Creating a skeleton website](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/skeleton_website)

Date Started: *11-02-2021*

|||
| --- | --- |
| **Prerequisites:** | --- |
| **Objective:** | --- |

**Overview**:

This article shows how you can create a "skeleton" website, which you can then populate with site-specific settings, paths, models, views, and templates (we discuss these in later articles).

---

## [Part 3: Using Models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

Date: *11-02-2021*

|||
| --- | --- |
| **Prerequisites:** | Django Tutorial Part2: Creating a skeleton website |
| **Objective:** | To be able to design and create your own models, choosing fields appropriately |

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

**Overview**:

After we defined our models and created some initial library records to work with, it's time to write the code that presents that information to users. The first thing we need to do is determine what information we want to display in our pages, and define the URLs to use for returning those resources. Then we'll create a URL mapper, views, and templates to display the pages.

The following diagram describes the main data flow, and the components required when handling HTTP requests and responses. As we already implemented the model, the main components we'll create are:

URL mappers to forward the supported URLs (and any information encoded in the URLs) to the appropriate view functions.
View functions to get the requested data from the models, create HTML pages that display the data, and return the pages to the user to view in the browser.
Templates to use when rendering data in the views.

![Overview Diagram](locallibrary/assets/django-tutorial-part-5-overview.png)

As you'll see in the next section, we have 5 pages to display, which is too much information to document in a single article. Therefore, this article will focus on how to implement the home page, and we'll cover the other pages in a subsequent article. This should give you a good end-to-end understanding of how URL mappers, views, and models work in practice.

---

## [Part 6: Generic list and detail views](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views)

Date: *11-04-2021 - 11-27-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 5 |
| **Objective:** | To understand where and how to use generic class-based views, and how to extract patterns from URLS and pass the information to views. |

**Overview**:

In this tutorial we're going to complete the first version of the LocalLibrary website by adding list and detail pages for books and authors (or to be more precise, we'll show you how to implement the book pages, and get you to create the author pages yourself!)

The process is similar to creating the index page, which we showed in the previous tutorial. We'll still need to create URL maps, views, and templates. The main difference is that for the detail pages, we'll have the additional challenge of extracting information from patterns in the URL and passing it to the view. For these pages, we're going to demonstrate a completely different type of view: generic class-based list and detail views. These can significantly reduce the amount of view code needed, making them easier to write and maintain.

The final part of the tutorial will demonstrate how to paginate your data when using generic class-based list views.

---

## [Part 7: Sessions framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Sessions)

Date: *11-27-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 6 |
| **Objective:** | To understand how sessions are used. |

**Overview**:

The LocalLibrary website we created in the previous tutorials allows users to browse books and authors in the catalog. While the content is dynamically generated from the database, every user will essentially have access to the same pages and types of information when they use the site.

In a "real" library you may wish to provide individual users with a customized experience, based on their previous use of the site, preferences, etc. For example, you could hide warning messages that the user has previously acknowledged next time they visit the site, or store and respect their preferences (e.g. the number of search results that they want to be displayed on each page).

The session framework lets you implement this sort of behavior, allowing you to store and retrieve arbitrary data on a per-site-visitor basis.

---

## [Part 8: User authentication and permissions](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Authentication)

Date: *11-27-2021 - 11-30-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 7 |
| **Objective:** | To understand how to set up and use user authentication and permissions |

**Overview**:

Django provides an authentication and authorization ("permission") system, built on top of the session framework discussed in Part 7, that allows you to verify user credentials and define what actions each user is allowed to perform. The framework includes built-in models for Users and Groups (a generic way of applying permissions to more than one user at a time), permissions/flags that designate whether a user may perform a task, forms and views for logging in users, and view tools for restricting content.

*NOTE: According to Django, the authentication system aims to be very generic, and so does not provide some features provided in other web authentication systems. Solutions for som common problems are available as third-party packages. For example, throttling of login attempts and authentication against third parties (e.g. OAuth).*

In this tutorial we'll show you how to enable user authentication in the LocalLibrary website, create your own login and logout pages, add permissions to your models, and control access to pages. We'll use the authentication/permissions to display lists of books that have been borrowed for both users and librarians.

The authentication system is very flexible, and you can build up your URLs, forms, views, and templates from scratch if you like, just calling the provided API to log in the user. However, in this article, we're going to use Django's "stock" authentication views and forms for our login and logout pages. We'll still need to create some templates, but that's pretty easy.

We'll also show how to create permissions, and check on login status and permissions in both views and templates.

---

## [Part 9: Working with forms](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)

Date: *11-30-2021 - 12-03-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 8 |
| **Objective:** | To understand how to write forms to get information from users and update the database. To understand how the generic class-based editing views can vastly simplify creating forms for working with a single model. |

**Overview**:

An HTML Form is a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server. Forms are a flexible mechanism for collecting user input because there are suitable widgets for entering many different types of data, including text boxes, checkboxes, radio buttons, date pickers and so on. Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.

While we haven't created any forms in this tutorial so far, we've already encountered them in the Django Admin site -- for example, the screenshot below shows a form for editing on of our Book models, comprised of a number of selection lists and text editors.

![admin portal "add book" example](locallibrary/assets/admin_book_add.png)

Working with forms can be complicated! Developers need to write HTML for the form, validate and properly sanitize entered data on the server (and possibly also in the browser), repost the form with error messages to inform users of any invalid fields, handle the data when it has successfully been submitted, and finally respond to the user in some way to indicate success. Django Forms take a lot of the work out of all these steps, by providing a framework that lets you define forms and their fields programmatically, and then use these objects to both generate the form HTML code and handle much of the validation and user interaction.

In this tutorial, we're going to show you a few of the ways you can create and work with forms, and in particular, how the generic editing views can significantly reduce the amount of work you need to do to create forms to manipulate your models. Along the way, we'll extend our LocalLibrary application by adding a form to allow librarians to renew library books, and we'll create pages to create, edit and delete books and authors (reproducing a basic version of the form shown above for editing books).

---

## [Part 10: Testing a Django web application](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing)

Date: *12-03-2021 - 12-08-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 9 |
| **Objective:** | To understand how to write unit tests for Django-based websites |

**Overview**:

The Local Library currently has pages to display lists of all books and authors, detail views for Book and Author items, a page to renew BookInstances, and pages to create, update, and delete Author & Book items. Even with this relatively small site, manually navigating to each page and superficially checking that everything works as expected can take several minutes. As we make changes and grow the site, the time required to manually check that everything works properly will only grow. If we were to continue as we are, eventually we'd be spending most of our time testing, and very little time improving our code.

Automated tests can really help with this problem! The obvious benefits are that they can be run much faster than manual tests, can test to a much lower level of detail, and test exactly the same functionality every time (human testers are nowhere near as reliable!) Because they are fast, automated tests can be executed more regularly, and if a test fails, they point to exactly where the code is not performing as expected.

In addition, automated tests can act as the first real-world "user" of your code, forcing you to be rigourous about defining and documenting how your website should behave. Often they are the basis for your code examples and documentation. For these reasons, some software development processes start with test definition and implementation, after which the code is written to match the required behavior (e.g. test-driven and behavior-driven development).

This tutorial shows how to write automated tests for Django, by adding a number of tests to the LocalLibrary website.

---

## [Part 11: Deploying Django to production](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment)

Date: *12-08-2021*

|||
| --- | --- |
| **Prerequisites:** | Complete all previous tutorial topics, including Django Tutorial Part 10 |
| **Objective:** | To learn where and how you can deploy a Django app to production |

**Overview**:

Once your site is finished (or finished "enough" to start public testing) you're going to need to host it somewhere more public and accessible than your personal development computer.

Up to now you've been working in a development environment, using the Django development web server to share your site to the local browser/network, and running your website with (insecure) development settings that expose debug and other private information. Before you can host a website externally you're first going to have to:

* Make a few changes to your project settings.
* Choose an environment for hosting the Django app.
* Choose an environment for hosting any static files.
* Set up a production-level infrastructure for serving your website.

This tutorial provides some guidance on your options for choosing a hosting site, a brief overview of what you need to do in order to get your Django app ready for production, and a worked example of how to install the LocalLibrary website onto the Heroku cloud hosting service.

---
