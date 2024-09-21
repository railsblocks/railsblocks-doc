## 项目打包与镜像托管

本章节将介绍如何将项目打包为 Docker 镜像，并托管到 Docker Hub 上。我们采用 Docker 打包的方式，通过 Docker Buildx 工具将项目打包成支持多架构的镜像。

### 1. 安装与配置 Docker 环境

#### 1.1 安装 Docker

在进行项目打包之前，需要先安装 Docker。你可以参考 [Docker 官方文档](https://docs.docker.com/get-docker/) 来获取适用于各平台的安装教程。

#### 1.2 安装 Docker Buildx 插件

[buildx](https://docs.docker.com/reference/cli/docker/buildx/build/) 是 Docker 提供的一个增强型构建插件，可以实现跨平台的构建能力。大部分 Docker 的新版本中已经默认包含了 `buildx` 插件。你可以通过以下命令来验证 `buildx` 是否可用：

```bash
docker buildx version
```

如果未安装 `buildx`，可以参考 Docker 官方指南安装或配置。

### 2. 项目打包为 Docker 镜像

#### 2.1 编写 Dockerfile

首先，需要确保项目根目录下存在一个正确的 `Dockerfile` 文件，用于定义镜像的构建步骤。通过Dockerfile，我们可以指定项目的构建环境、依赖、运行命令等。

#### 2.2 构建镜像

在项目根目录下，使用 Docker 构建镜像。为了支持多平台架构，这里使用 `buildx` 命令构建镜像。

```bash
docker buildx build --platform linux/amd64 -t <DockerHub-用户名>/<镜像名>:<标签> .
```

具体到本项目中，执行以下命令：

```bash
docker buildx build --platform linux/amd64 -t qichunren/railsblocks:main-latest .
```

- `--platform linux/amd64`：指定生成适用于 `linux/amd64` 平台的镜像。
- `-t`：指定镜像的名称与标签，格式为 `<用户名>/<镜像名>:<标签>`。
- `.`：表示当前目录为 Docker 构建上下文。

#### 2.3 推送镜像到 Docker Hub
在镜像构建完成后，可以将其推送到 Docker Hub 进行托管。推送命令如下：

```bash
docker push <DockerHub-用户名>/<镜像名>:<标签>
```

在本项目中，执行以下命令：

```bash
docker push qichunren/railsblocks:main-latest
```

此命令将本地构建的镜像推送到 Docker Hub 上的 `qichunren/railsblocks` 仓库，并使用 `main-latest` 作为标签。

### 3. 验证镜像

成功推送镜像到 Docker Hub 后，你可以通过以下命令在任何支持 Docker 的环境下拉取并运行该镜像：

```bash
docker pull <DockerHub-用户名>/<镜像名>:<标签>
```

在本项目中，拉取并运行镜像的命令如下：

```bash
docker pull qichunren/railsblocks:main-latest
```

然后参见 [部署与运行](deployment.md) 章节，了解如何在 Docker 环境下部署与运行项目。

---

### 4. 总结

通过上述步骤，你可以成功将项目打包为 Docker 镜像并推送到 Docker Hub 上托管。此方法确保了项目环境的可移植性与一致性，方便了在不同平台上的部署与运行。