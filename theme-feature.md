
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

## 常用Liquid语法

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