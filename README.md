# devcontainers

请写三个devcontainer模板，分别对应着Python、Node.js和Go语言的开发环境。
1. 三个文件夹分别为：python-uv、node、go
2. 每个文件夹内都包含一个`.devcontainer`文件夹，里面有`devcontainer.json`和`Dockerfile``docker-compose.yml`。
    * 基础镜像为`mcr.microsoft.com/vscode/devcontainers/base:ubuntu`。
3. 每个`devcontainer.json`文件中都包含以下内容：
    * `"name"`: 对应的开发环境名称，如"Python Dev Container"、"Node.js Dev Container"、"Go Dev Container"。
    * service: 设置为`app`，在`docker-compose.yml`中定义一个名为`app`的服务。
    * `"dockerFile"`: 指向当前文件夹中的`Dockerfile`。
    * `"settings"`: 包含一些VS Code的设置，如终端集成默认使用zsh。
    * `"extensions"`: 列出一些推荐安装的VS Code扩展，如Python、Node.js和Go相关的扩展。
    * `"remoteUser"`: 设置为`vscode`。
    * containerUSer设置为`vscode`，确保容器内的用户权限正确。
    * `"features"`: 使用`ghcr.io/devcontainers-extra/features/zsh-plugins:0`，并指定要安装下列ZSH插件 git zsh-autosuggestions zsh-syntax-highlighting。
    * python使用features安装python-uv环境，node使用features安装node环境，go使用features安装go环境, 并指定版本号为最新的稳定版本。
        * python ghcr.io/devcontainers-extra/features/uv:1
        * node ghcr.io/devcontainers-extra/features/node:2
        * go ghcr.io/devcontainers-extra/features/go:1
    * workspaceFolder设置为`/workspace`，并且在`docker-compose.yml`中将当前文件夹挂载到容器的`/workspace`目录。