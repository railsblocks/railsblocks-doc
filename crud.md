# CRUD Generator

How to quickly create a full set of code for a backend Create, Read, Update, Delete (CRUD) operation, including controllers, models, and view pages?

Here's how you might do it in Rails:

```
$ ./bin/rails generate scaffold HighScore game:string score:integer
```

However, the general data management functions of Create, Read, Update, Delete (CRUD) are placed in the backend (/admin). They can be generated with the following command:

```
$ ./bin/rails generate model ProductCategory name url_slug \ 
  position:integer parent_id:integer

$ ./bin/rails g scaffold_controller Admin::ProductCategory \ 
  name url_slug position:integer --model-name=ProductCategory --no-jbuilder
```

This will generate a full set of code for the product_categories table in the backend management, and there will also be a link in the backend management menu.