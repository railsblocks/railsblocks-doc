# Theme deveopment API

## 主题文件结构

```
theme/
├── assets/
│   ├── css/
│   ├── js/
│   └── images/
├── layout/
│   ├── theme.liquid
│   └── other-layouts.liquid
├── snippets/
│   ├── header.liquid
│   ├── footer.liquid
│   └── product-card.liquid
├── templates/
│   ├── index.liquid
│   ├── product.liquid
│   ├── page.liquid
│   ├── post.liquid
│   └── collection.liquid
└── config/
    └── settings_schema.json
```

### 目录说明

- assets/: 存放CSS、JavaScript和图片等静态资源
- layout/: 包含主布局文件和其他布局模板
- sections/: 可重用的页面部分,如页眉、页脚等
- snippets/: 可在多个模板中重用的代码片段
- templates/: 各种页面类型的模板文件
- config/: 主题配置文件,如settings_schema.json

## 常用代码片断

网页标题标签：

```
<title>{% if page_title != blank %}{{ page_title }} - {% endif %}{{ site.name }}</title>
```

静态资源文件引用：

静态资源文件一般包括Javascript文件、CSS样式文件、图片文件等，它们都应该放到主题的 assets 目录中，也可以放到 assets 目录中的子目录中。

例如引用当前主题中的 application.css
```
{{ 'application.css' | asset_url | stylesheet_tag }}
```

引用当前主题中的 app.js 文件
```
<script src="{{ 'app.js' | asset_url }}" defer></script>
```

引用当前主题中的图片文件:
```
<img src="{{ 'logo.png' | asset_url }}" alt="Logo">
``` 


显示网站导航链接：

```
{% render_menu "Main Menu" -%}
  <div class="flex items-center">
    {% for item in menu_items -%}
      <a class="py-2 text-blue-600 hover:underline" href="{{ item.url }}">{{ item.display_name }}</a>
    {% endfor -%}
  </div>
{% endrender_menu -%}
```

多个链接组成菜单，可以在菜单管理中进行设置。

显示文章分类的子分类列表:

例如：显示'blog'分类的所有子分类：

```
{% for category in blogs.blog.categories %}
  <li><a class="py-2 text-sm hover:underline" href="{{ category.url }}">{{ category.name }}</a></li>
{% endfor %}
```


## 常用 Liquid 语法

### 对象


{{ product.title }}
{{ collection.products }}
{{ cart.total_price }}

### 标签

条件语句:
{% if product.available %}
  In stock
{% else %}
  Sold out
{% endif %}

循环:

{% for product in collection.products %}
  {{ product.title }}
{% endfor %}

过滤器

{{ product.title | upcase }}
{{ product.price | money_with_currency }}

注释

{% comment %}
  这是一段注释
{% endcomment %}

包含其他模板

{% render 'product-card' %}

分页

```
{% paginate collection.products by 12 %}
  {% for product in collection.products %}
    <!-- 产品展示代码 -->
  {% endfor %}
  {{ paginate | default_pagination }}
{% endpaginate %}
```