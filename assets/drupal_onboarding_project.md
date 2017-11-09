**Drupal onboarding project**
=============================

This project is used as an onboarding project for new developers. The
intention of this project is to test and improve developers’ Drupal
skills.

**Technical details**
---------------------

This should be a Drupal 8 project.

Developer should set up a site on Pantheon
(https://dashboard.pantheon.io). You can get up to three free projects
there if you don’t put them to Live environment, so you can use one of
those. If you don’t have account there, create one. You will also have
to add your SSH key to the account on Pantheon, so you'll be able to
pull the code down. After you do this, create your first site. You will
then be able to clone the code to your computer and also download the
current database by using the Database / files menu on left and clicking
on Export.

From the design point of view, if your goal is site-building and backend
development, than bootstrap can be used as theme. If you’re a
frontender, we encourage you to build your theme from scratch.

**Brief description**
---------------------

The main functionality of the page is to show events that different
companies are organizing on different locations.

Administrator should be able to add company, location and also an event
which has reference to both items. Locations are well known locations
(such as Hotel Union, Kolosej ..) so administrator should be able to
select location from list or using autocomplete. Detailed fields needed
are listed below.

**Content types**
-----------------

Below is a list of content types with all the fields. Fields marked with
\* should be required.

### **Company**

We are using this to store information about company.

Design: Company\_page.png (preview)

#### **Fields:**

1.  Title\*

2.  Description\* (text editor needed)

3.  Logo\*

4.  Website

5.  Address

6.  Phone number

7.  Contact email

8.  Industry\* (taxonomy reference, make up your own)

### **Location**

We are using this to store information about location.

Design:

Normal: Location\_page.png (preview)

List view: Locations.png (preview)

#### **Fields:**

1.  Title\*

2.  Description\* (text editor needed)

3.  Image\*

4.  Website

5.  Address\*

6.  Phone number

7.  Contact email\*

8.  Equipment (taxonomy reference, make up your own e.g. air-condition,
    > parking, bar, food ...)

### **Event**

We are using this to store information about events.

Design:

Normal: Events\_page.png (preview)

List view: Events.png (preview)

#### **Fields:**

1.  Title\*

2.  Description\* (text editor needed)

3.  Start date\*

4.  End date\*

5.  Image\*

6.  Event type\* (taxonomy reference, make up your own e.g. sports,
    > culture, conference ...)

7.  Website (if exists, not mandatory)

8.  Organizer\* (reference to Company node)

9.  Location\* (reference to Location node)

**Display of content**
----------------------

First we want to display all of the items as lists:

-   Company list: a list of all companies with an option to search by
    > title or filter by industry

-   Locations list: a list of all locations with an option to search by
    > title or filter by equipment

-   Events list: a list of all events with an option to search by title
    > or filter by event type

When user clicks on one item (company, location, event), it has to go to
a page with all the details. The individual page (node) should print out
all fields that are on content type. Check the design files and try to
print them out as they are printed there. If you are backender, you are
doing this to make life easier to the frontender that will style your
work. If you are frontender - well, then you are making life easier to
yourself since you will have to style it afterwards.

Beside the fields that are on each content type, the page should have
different blocks for each content type as well:

-   Company: list of all events that this company is organizing with a
    > link to each event page

-   Location: list of all events organized in this location with a link
    > to each event page

-   Event: Location with brief description and link to full page,
    > Organizer (company) with brief description and link to full page

Print this blocks in a sidebar of individual node display.

**Special instructions for Front-end developers**
-------------------------------------------------

### **1. Set up local environment and install starter theme**

-   use our kickstarter theme from zip folder **kickstarter-8.x.zip**
    > (it uses Gulp and Sass). You can create your own starter theme,
    > but we recommend that you use our.

-   for Drupal 7 use branch "7.x"

-   place theme into correct directory.

-   Drupal 7 example: {your\_www\_root}/sites/all/themes/

-   Drupal 8 example: {your\_www\_root}/themes/

-   rename theme and set theme preview image (screenshot.png)

-   edit theme.info file and template.php file

-   enable your theme and set to default

-   read documentation/readme on kickstarter theme GitHub repository

### **2. Before you start theming**

-   Before you start writing your own code, read about Drupal Coding
    > Standards
    > [*https://www.drupal.org/docs/develop/standards/css*](https://www.drupal.org/docs/develop/standards/css)

-   Get to know the theme folder structure (you’ll see that some example
    > files are already placed inside). Put your custom new files in the
    > right place.

-   Read about Drupal template naming conventions

    -   Drupal 8:
        > [*https://www.drupal.org/docs/8/theming/twig/twig-template-naming-conventions*](https://www.drupal.org/docs/8/theming/twig/twig-template-naming-conventions)

    -   Drupal 7:
        > [*https://www.drupal.org/node/1089656*](https://www.drupal.org/node/1089656)

-   Read about JavaScript coding standard on Drupal

    -   [*https://www.drupal.org/docs/develop/standards/javascript/javascript-coding-standards*](https://www.drupal.org/docs/develop/standards/javascript/javascript-coding-standards)

### **3. Theming**

-   Open one of provided design files

    -   If you find any element that isn’t in design, you can leave it.
        > Design is more as a guideline for this example.

    -   For all the icons in design you can use FontAwesome library

-   Mobile theming

    -   We don’t have mobile design, so you make what you think will
        > be best. You will not always get a mobile design, so now it’s
        > up to you.

-   First you need to theme main navigation. Use CSS media breakpoints
    > with combination of JavaScript / jQuery and define desktop and
    > mobile navigation view (on mobile use hamburger icon). You can use
    > CSS animations as well. Create navigation with two level dropdown
    > on desktop, on mobile hide second level by default, and show only
    > on click or touch event. You can add icon "+" to show
    > second level. Navigation must be position fixed. Don’t be afraid
    > to import other libraries that you know and you’ve worked with -
    > for example FontAwesome.

-   Style slider on front page.

    -   You can use one of the following jQuery libraries

        -   Slick JS
            > [*http://kenwheeler.github.io/slick/*](http://kenwheeler.github.io/slick/)

        -   OWL Carousel
            > [*https://github.com/OwlFonk/OwlCarousel*](https://github.com/OwlFonk/OwlCarousel)

    -   Slider must be responsive, all texts and images must be visible
        > on mobile devices.

-   Open provided Companies.afdesign file

    -   You will style company node list by this design.

    -   For company node detail use

-   Event node

    -   Style event list like it is on Events.afdesign

    -   If there will be more than 4 events, apply one of the carousels
        > you’ve used on homepage slider and use prev/next
        > navigation type.

    -   For event detail use the design Events\_page.afdesign and
        > theme it.

    -   All blocks must be same heights. Shorten text and titles using
        > CSS ellipsis or some other method that you know, if there will
        > be too many characters displayed.

-   Location node

    -   TODO: Boštjan poglej ker dizajn bi bil za tole najbolj
        > primeren? :)

-   Footer

    -   Style footer by the design, create CSS3 pseudo elements for
        > triangle backgrounds on bottom. Change opacity of this
        > elements for mobile devices and set smaller size.

-   Global theming

    -   Create simple CSS3 hover transition for all CTA buttons.

    -   When mobile navigation will be triggered, disable scroll on
        > entire site and leave only navigation scrollable by Y axis.
        > Also try to apply overlay to entire site except navigation
        > with white rgb background with alpha channel set to 80%.

    -   Make CTA buttons as extendables, so you could reuse them
        > anywhere else in the code.

    -   Make sure you will set all container widths, colors, etc.
        > globally accessible and that they could be changed globally.

    -   Apply some rule only for mobile device. For example set
        > background to black on header. This must be done without media
        > breakpoint technique. You should target mobile devices only!

    -   Set default stylings for headings (h1,h2,...), paragraphs and
        > lists (ul,ol).

        -   For unordered list (&lt;ul&gt;) use custom check icon (img
            > or FontAwesome) instead of default list style type.

-   After you’re done

    -   Make main container width for 120px wider. Now check if your
        > code adapts to new width. (This is what can happen in real
        > life projects, when client suddenly decides to have wider
        > site, or maybe you just set it wrong...)

**Special instructions for Back-end developers**
------------------------------------------------

#### **Prerequisites:**

-   Create a custom module ‘ad\_general’ in modules/custom and enable it

-   Read about coding standards in Drupal, mainly focusing on indents
    > and whitespaces:
    > [*https://www.drupal.org/docs/develop/standards/coding-standards*](https://www.drupal.org/docs/develop/standards/coding-standards)

#### **Features to implement:**

1.  If a company node is created with the website field empty we want to
    > display a status message after the company is saved saying:
    > ‘Please consider adding a website for your company. It’s not
    > mandatory, but it’s a good way of showing people what you do’.

    a.  Hints:

        i.  Look into the Drupal hook system and check how can you do
            > some action when a node is being created for the
            > first time.

2.  Create a custom block which will be displayed in the sidebar on
    > event pages. The block should display how many days are left until
    > the event starts, example: ‘Days left to event start: 12’.

3.  If the event is in progress display ‘The event is in progress.’.

4.  If the event is over display ‘The event has ended.’.

5.  The block should not be cached.

    a.  Hints:

        i.  Find how to detect the currently displayed node

        ii. Load the date field values

        iii. Check out the Drupal 8 block manager on how to create a
            > block

6.  When a company node is being saved, we want to prevent users from
    > setting a no-reply email. Check if the email field starts with
    > ‘no-reply’ and if it does, set an error in the form validation.
    > There should be a message saying: ‘Please enter a valid
    > response email’.

    a.  Hints:

        i.  Use an appropriate hook to add a custom validation function
            > to the node add form

        ii. Learn how to properly set a validation error for a field

7.  On every event page we want to display a "Send to friend" block.
    > This should be a block with a form inside.

8.  The form should have a title, a name field(mandatory), an email
    > field(which has to be validated) and a ‘Send’ button.

9.  If the validation fails display an error message saying ‘Enter a
    > valid email address’.

10. If the validation passes send an email to the entered address:

11. Subject: \[name\] invited you to \[event\_title\]

12. Body: Check out this event by \[company\]! \[link\_to\_event\_node\]

13. Display a success message if the email has been sent.

    a.  Hints:

        i.  Create a custom block with the form as the markup

        ii. Check out the Drupal Form API

        iii. You’ll have to get the referenced companies title for the
            > email markup

        iv. Find how to send emails using Drupal

14. When the send form will be working, upgrade it by doing the AJAX
    > submit of that form instead of the page reload.

    a.  Hints:

        i.  Check out AJAX form submission in Drupal

15. For all the events create 'Add to favorites' link. Put it somewhere
    > on the Event page. After you'll do this, also create a page with
    > url /my-favorite-events, which will display a list of all the
    > events that the current logged in user added to favorites.

    a.  Hints:

        i.  Check Flag module

16. Client wants to display from 1-5 stars on the Location page, using
    > the values from equipment. So for example: if they have parking
    > and wi-fi, but no air-condition, they get 3 stars, if they have
    > air-condition as well, they get 4 stars etc. The equipment and
    > ranking is something you can make up. Out of your equipment items
    > (let's say you must have at least 5 of them) create a scoring
    > matrix, that will represent the number of stars. After that,
    > display number of stars on each Location node, depending on the
    > equipment that each location have.


