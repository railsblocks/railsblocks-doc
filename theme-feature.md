# 主题功能

为了减少开发工作量，让项目复用度高，本项目支持了多主题功能。准确的说应该是前台多主题，后台还是同一套管理代码。

通过这样的方式，你可以方便地开发出各种类型的 WEB 应用，满足各种类型的需求。通过多主题功能，你可以开发一个产品起步站 (Landing page)、博客网站 (Blog)、资讯网站 (News)、公司网站 (Compnay)、外贸网站、电商网站 (Ecommerce) 等等。

## 起步

每一个主题都是位于 `app/themes` 目录中。通过命令 

```
$ ./bin/rails g theme YourThemeName
```

可以生成一个默认的主题。

### 主题组成

一个主题是由若干页面（html.erb）、js、css 和图片等静态资源文件，还有多语言翻译文件组成。

```
my-app
└── app
    ├── views
    └── themes
        └── your-theme
            ├── README.md
            ├── assets
            │   ├── builds
            │   ├── images
            │   └── stylesheets
            ├── locales
            │   ├── en.yml
            │   └── zh-CN.yml
            └── views
                ├── layouts
                │   ├── application.html.erb
                │   └── _header.html.erb
                └── home
                    └── index.html.erb
```

主题中的页面开发和你所熟悉的 app/views 目录中的开发没有两样，遵循同样的 Rails 约定，同样的 ERB 模板语言。只不过是为了区分多个主题，在 app/themes 目录中分开了。

## 资源文件 Assets

* 图片文件放于 assets/images/ 中
* builds 目录是终的可以引用的文件