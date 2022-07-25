# CRUD 代码生成

如何快速创建一个后台的增删节查改（CRUD）的包括控制器、模型、视图页面的全套代码？在 Rails 中一般是用如下的命令来生成：

```
$ ./bin/rails generate scaffold HighScore game:string score:integer
```

但是一般数据的增删查改的管理功能是放在后台（/admin）中的，通过如下的命令来生成：

```
$ ./bin/rails generate model ProductCategory name url_slug \ 
  position:integer parent_id:integer

$ ./bin/rails g scaffold_controller Admin::ProductCategory \ 
  name url_slug position:integer --model-name=ProductCategory --no-jbuilder
```

这样会在生成后台管理中的针对 product_categories 表的全套代码，同时在后台的管理菜单中也会有一个链接。