# 前端 Javascript 部署方案

## Rails 中的 Javascript 问题

在 Rails 框架发展的过程中，其中的 Javascript 打包方案经历多次的演进，每次都有一个大变样。目前前端开发领域中 Javascript 的打包方法有多种，比校常用的有 webpack、Parcel、Rollup、esbuild 等。在 Rails 5 中引入了 webpacker gem 包，它集成了 webpack 打包功能。到了 Rails 7 发布时，放弃了 webpacker 了，它也改成 shakapacker 了。Rails 7 中默认使用的 importmap 工具，它是采用了现代浏览器支持的 es module 接口，从而不需要像其它的工具一样来打包了。我个人还是不喜欢这种激进的方式。

## 我采用的方式

由于 Javascript 的打包方式多样化，Rails 7 直接放弃了集成打包功能，引入了 propshaft、jsbundling-rails、cssbundling-rails 几个 gem 包，统一了 assets 文件的输出目录，从而将烦杂的前端方案完全交给前端部分去处理了。这样做了之后 Rails 7 又变成了我喜欢的样子。

我采用了 esbuild 的打包方案。采用它是因为它打包速度快，使用方便。在 package.json 文件中：

```
"scripts": {
  "build": "esbuild --minify app/javascript/*.js --bundle --sourcemap --outdir=app/assets/builds"
}
```

这样执行 `yarn build` 后 app/javascript 目录中的 js 文件（不包括下一层目录）就会打包到 app/assets/builds 中了。
