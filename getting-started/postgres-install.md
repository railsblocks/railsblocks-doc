# Postgres 数据库

我喜欢采用 docker 来运行 Postgres 数据库，用如下的命令：

```
docker run --rm -p 5432:5432 -e POSTGRES_USER=YourName -e POSTGRES_HOST_AUTH_METHOD=trust --name=railsblocks-postgres postgres
```

docker 中不会保留数据，每次启动后，在 Rails 中需要创建数据库，执行 migration 等。

```
#!/bin/sh

bundle exec rails db:create
bundle exec rails db:migrate
bundle exec rails db:seed
```
