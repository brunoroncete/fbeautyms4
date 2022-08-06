# User Experience

## Initial Discussion

* I wanted to create a website linked to a database, which allows users to log in, search for and find products to buy them.
* I wanted to be able to add, edit and delete inventory of products for sale.

## As a site owner
 - I want to be able to add new or edit existing products.
 - I want to be able to remove existing products.
 - I want to be able to add new/existing products to "special offers/sale", "featured products".
 - I want to be able to add new, edit or remove existing categories and brands.

## As a customer
 - I want the main purpose of the site to be clear so that I immediately know what the site is intended for upon entering.
 - I want to view a list of products or look for an individual item by its category.
 - I want to be able to view individual product details, product Image, the price and the product description.
 - I want to be able to view order confirmation and save my contact details in my registered Profile
 - I want to easily access my previous orders.
 - I want to be able to contact the store of the website incase I have any issues or questions.

---

# UI
- A responsive Navbar
- A search function for users to find available products
- A registration/login form for the first time and returning users
- A loading page was implemented to stop poor impressions from data loading slowly
- A footer to provide some information and social links
- Forms for the admin to add new or modify existing products

# Wireframes
 - [Wireframes_desktop_tablet.pdf](#)
 - [Wireframe-mobile](#)

# Database Schema
I started planning the database after I have done my wireframes to justify which fields I would require and what collections I would have to use. After the initial discussion with my mentor, I have settled with the current database schema.
 - [Database.pdf](./readme_media/database_diagram.png)
 - [View diagram on dbdiagram.io](https://dbdiagram.io/d/6186a3a8d5d522682dfb80c9)

# Database Model
- [Database model](./readme_media/database_model.pdf)



---
# Deployment

Detailed deployment can be found [here](https://github.com/brunoroncete/fbeautyms4/readme_files/docs/deployment.md)


---
# Technologies Used

## Languages Used

-   [HTML5](https://en.wikipedia.org/wiki/HTML5)
-   [CSS3](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)
-   [Jquery](https://en.wikipedia.org/wiki/Jquery)
-   [Python3](https://en.wikipedia.org/wiki/Python_Programming_Language)

## Frameworks, Libraries & Programs Used

1. [Bootstrap 5.x:](https://getbootstrap.com/)
    - Bootstrap 5.x was used to assist with the responsiveness and styling of the website.
2. [Font Awesome 5:](https://fontawesome.com/)
    - Font Awesome was used on all pages throughout the website to add icons for aesthetic and UX purposes.
3. [jQuery:](https://jquery.com/)
    - jQuery came with bootstrap to make the navbar entire site responsive.
4. [Git](https://git-scm.com/)
    - Git was used for version control by utilizing the Gitpod terminal to commit to Git and Push to GitHub.
5. [GitHub:](https://github.com/)
    - GitHub is used to store the projects code after being pushed from Git. 
6. [Balsamiq:](https://balsamiq.com/)
    - Balsamiq was used to create the [wireframes](https://github.com/) during the design process.
7. [Heroku:](https://heroku.com/)
    - Heroku was used to create  and deploy our app.    
8. [Django:](https://django.com/)
    - Django was used to create the framework.
9. [Postgresql:](https://postgresql.org/)
    - Mongodb was used to create database and to connect server to our site.
10. [Stripe:](https://stripe.com/)
    - Stripe was used to accept and authorise payment for any item purchased on the site.
11. [AWS:](https://s3.console.aws.amazon.com/)
    - Amazon S3 was used to manage and save media and static files in Its cloud service.        
12. [TinyMce](https://www.tiny.cloud/)
    - To create rich text editor for the text field for user to be able to create pretty text.

---


# Testing

The W3C Markup Validator and W3C CSS Validator Services were used to validate every page of the project to ensure there were no syntax errors in the project.

-   [W3C Markup Validator](https://jigsaw.w3.org/css-validator/#validate_by_input) - [Results](./readme_media/w3_html_check.png)
-   [W3C CSS Validator](https://jigsaw.w3.org/css-validator/#validate_by_input) - [Results](./readme_media/w3_css_check.png)
-   [Lighthouse](https://https://developers.google.com/web/tools/lighthouse) - [Results](./readme_media/lighthouse.png)

## Testing User Stories from User Experience (UX) Section

### Customer Goals

1. As a customer, I want the main purpose of the site to be clear so that I immediately know what the site is intended for upon entering.
     1. It is clear that the web site is a store.

2. As a customer, I want to be able to view a list of products, so that I can select some to purchase.

     1. Upon entering the site. The homepage navigation bar have links to list of products and categories, user have the option to view all products or search for a specific product.

    
3. As a customer, I want to be able to view individual product details, product Image, the price, the product description and the compatible cartridges.
   1. By clicking on the featured product from the home page, or by viewing all products and selecting one uses can view detailed information about product <br>
   
4. As a customer, I want to be able to view order confirmation and save my contact details in my registered Profile.
   1. After loging in, selecting the option my profile, the user is able to check his orders and update his details.
   
5. As a customer, I want to easily access my previous orders.
       
     1. In my profile the user is able to check all his previous orders <br>
 

## Further Testing

-   The Website was tested on Google Chrome, Mozilla Firefox, Microsoft Edge and Safari browsers.
-   The website was viewed on a variety of devices such as Desktop, Laptop, iPhone SE, iPhone 11, One+ 9 Pro, and iPadPro.
-   A large amount of testing was done to ensure that all pages were linking correctly
-   Friends and family members were asked to review the site and documentation to point out any bugs and/or user experience issues.

# Known Issues

######

# Problems encountered

- When checkout with selected update profile user 'Full name' was saved a tuple like so: ```('User Name',)``` instead of ```User Name```
  - **SOLVED** Problem was in the code where extra comma was added: ![Extra comma](./readme_media/bug_with_name.png)

- When adding new cartridge with image uploaded and without selecting any related printer(even if it already highlighted in the box) cartridge won't get assigned to that printer.
- When adding new cartridge without selecting image it works fine.
  - As a temporary workaround, after saving new cartridge go to admin dashboard and reassign cartridge to the related printer. 
  - **SOLVED** Found bug in saving form where I was calling  ```image.save()``` instead of main form ```form.save()```
- W3 validator gave me warning:
- ![The type attribute is unnecessary for JavaScript resources.](./readme_media/javascript_type_warning.png)
- To **solve** it i removed all ```type=text/javascript``` from ```<script>``` tags
- ``Duplicate ID delete-review-modal``. was found by markup validator
  - Had to rewrite bootstrap modal to handle multiple buttons pointing to the same modal. Solution found in [Bootstrap documentation](https://getbootstrap.com/docs/5.0/components/modal/#varying-modal-content)
- Search bar icon get shifted down on some pages
   ![](readme_media/search_icon_shift.png)
  - Fixed it by declaring .form-control and .btn styles to have font size set to 1.4 rem

---

# Credits

## Code

-   Code were copied and modified from the Full Stack Frameworks with Django, Boutique Ado Project and Hello Django Testing.

-   Bootstrap5 template was used throughout the project mainly to make site responsive using the [bootstrap 5](https://getbootstrap.com/)

## Content

-   All content was written by the developer.

## Media

-   All Images belong to the copyright owner.

# Acknowledgements

- Student Care and Tutor at Code Institute for their support.
- Deployment steps adapted to suit my project from [here](https://github.com/Abibubble/ms4-lead-shot-hazard)
- Some code testing was adapted to suit my project from [here](https://github.com/Abibubble/ms4-lead-shot-hazard)