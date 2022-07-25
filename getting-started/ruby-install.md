# Install Ruby

Ruby 可以安装在 Linux / Mac / Windows 操作系统中。在这里不推荐在 Windows 操作系统中使用 Ruby 开发。

## 源代码安装

首先从 Ruby 语言的官方网站上下载源代码，然后在目标机器上编辑安装。

    wget https://cache.ruby-lang.org/pub/ruby/3.0/ruby-3.1.1.tar.gz
    tar -xf ruby-3.1.1.tar.gz
    cd ruby-3.1.1
    ./configure --prefix=/usr/local/ruby-3.1.1 --disable-install-doc
    make
    sudo make install
    # Add '/usr/local/ruby-3.1.1/bin' to $PATH and safe path
    # sudo vim /etc/environment
    # sudo visudo
    source /etc/environment
    ruby -v

## rbenv

https://github.com/rbenv/rbenv

https://github.com/rbenv/ruby-build

## Docker

待完善文档

## 相关链接

- Ruby 语言官方网站：[https://www.ruby-lang.org/](https://www.ruby-lang.org/)
- Ruby 语言代码仓库：[https://github.com/ruby/ruby](https://github.com/ruby/ruby)
