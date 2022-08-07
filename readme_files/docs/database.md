### Database Design

As Django works with SQL databases by default, I was using SQLite in development. Heroku, however, provides a PostgreSQL database for deployment

### User Model

The User model utilized for this project is the standard one provided by `django.contrib.auth.models`

### Profiles App

| Name | Database Key | Field Type | Type Validation |
| :-------------: |:----------------:| :--------------: | :---------: |
|User | user |	OneToOneField 'User'| on_delete=models.CASCADE
|Default Phone Number |	default_phone_number | CharField | max_length=20, null=True, blank=True
|Default Country | default_country | CountryField | blank_label='country', null=True, blank=True
|Default Postcode | default_postcode | CharField | max_length=20, null=True, blank=True
|Default Town or City | default_town_or_city | CharField | max_length=40, null=True, blank=True
|Default Street Address1 | default_street_address1 | CharField | max_length=80, null=True, blank=True
|Default Street Address2 | default_street_address2 | CharField | max_length=80, null=True, blank=True

### Products App

`Category` model

| Name | Database Key | Field Type | Type Validation |
| :-------------: |:----------------:| :--------------: | :---------: |
|Name | name | CharField | max_length=254
|Friendly Name | friendly_name | CharField | max_length=254, null=True, blank=True

`Product` model

| Name | Database Key | Validation | Field Type|
| :-------------: |:----------------:| :--------------: | :---------: |
|Product id | id | primary_key=True | AutoField
|Name | name | default='', max_length=254 | CharField
|SKU | sku | max_length=254, null=True, blank=True | CharField
|Description | content | blank=False | TextField
|Price | price | max_digits=6, decimal_places=2 | DecimalField
|Image| image| blank=False | ImageField
|Rating | rating | blank=True | DecimalField


### Post

| Name | Database Key | Validation | Field Type|
| :-------------: |:----------------:| :--------------: | :---------: |
|id | id | primary_key=True | AutoField
|Category| category | on_delete=models.CASCADE | ForeignKey
|Title | title | max_length=100 | CharField
|Slug | slug | max_length=200, unique=True | SlugField
|Intro | intro | validators=[MinLengthValidator(100)], max_length=400 | TextField
|Article | article | validators=[MinLengthValidator(250)]| TextField
|Image| image | blank=True | ImageField
|Date_added| date_added| auto_now_add=True | DateTimeField

### Category_post

| Name | Database Key | Validation | Field Type|
| :-------------: |:----------------:| :--------------: | :---------: |
|Title | title | max_length=100 | CharField
|Slug | slug | max_length=200, unique=True | SlugField


### Order

| Name | Database Key | Validation | Field Type|
| :-------------: |:----------------:| :--------------: | :---------: |
|Order id | id | primary_key=True | AutoField
|User | user | User, on_delete=models.CASCADE, related_name="orders" | ForeignKey(User)
|Full name | full_name | max_length=50 | CharField
|Phone number | phone_number | max_length=20, blank=False | CharField
|Country | country | max_length=40, blank=False | CharField
|Postcode | postcode| max_length=40, blank=True | CharField
|Town or City | town_or_city | max_length=40, blank=False | CharField
|Street address 1 | street_address1 | max_length=40, blank=False | CharField
|Street address 2 | street_address2 | max_length=40, blank=False | CharField
|County | county | max_length=40, blank=False | CharField
|Date | date | default=timezone.now | DateField
|Total price | total_price | max_digits=100, decimal_places=2, default=0.00 | DecimalField

### OrderLineItem

| Name | Database Key | Validation | Field Type|
| :-------------: |:----------------:| :--------------: | :---------: |
|Order Line Item id | id | primary_key=True | AutoField
|Order | order | Order, related_name="orderline", null=False | ForeignKey
|Product | product | Product, null=False | ForeignKey
|Quantity | quantity | blank=False | IntegerField

### Security

Using config variables in heroku, all SECRET access keys are stored safely to prevent unwanted connections to the database.

Django allauth was used to set up user registration and built in decorators allowed restricted access to certain features on the website that are not intended for regular users.
