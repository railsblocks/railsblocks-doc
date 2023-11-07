# Multi-theme Functionality

In order to reduce development workload and improve project reusability, this project supports multi-theme functionality. To be precise, it should be multiple themes in the front-end, while the back-end still uses the same set of management code.

In this way, you can conveniently develop various types of WEB applications to meet different types of needs. Through the multi-theme function, you can develop a product landing page, blog site, news site, company site, foreign trade site, e-commerce site, and so on.

## Get started

The theme code is located in the **app/themes** directory. Run the following command:

```
$ ./bin/rails g theme YourThemeName
```

You can quickly generate a default theme, and then start your creation based on actual needs.

### Theme Composition Structure

A theme is composed of several pages (html.erb), js, css and other static resource files, as well as I18N translation files.

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


The composition of the pages in the theme is no different from what you are familiar with in the **app/views** directory, following the same Rails conventions and the same ERB template language. It's just that in order to distinguish multiple themes, they are separated in the app/themes directory.

## Resource Assets

* Image files are placed in the **assets/images/** directory.
* The **builds** directory is the final file that can be referenced.

For simple Javascript files that do not need to be packaged, you can directly put them in the **builds** directory, and then use the normal `javascript_include_tag` method to reference JS in the page.

If you are using front-end engineered Javascript and need to go through processes like packaging, you can use the tools you are familiar with to complete it, and put the final output files in the **builds** directory.