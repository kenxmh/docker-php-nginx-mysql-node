# docker-php-node-nginx
## 介绍
集成 PHP Nginx Node 的 Docker 环境，开发和生产都可以
* 支持各服务的自定义配置，包括端口、版本、数据卷路径等
* PHP 已配置好 Composer，可选扩展齐全，按需安装即可，支持各种框架 Laravel、ThinkPHP 等
* nginx 附带自用 Laravel + Nuxt Site + Vue Admin 的配置
* Node 同样支持各种框架 Vue 和 Nuxt 等
* 已在线上部署过 Laravel + Nuxt Site + Vue Admin

旨在构造各平台一致的纯净开发和部署 **环境**
当前的目录设计并不适合一键部署和启动
如果需要一键部署，还需要修改目录和.env的数据卷，并相应的Dockerfile补充部署命令

## 如何使用：
### 第一步：配置 .env 和 docker-compose.yml
.env 的主要配置项
* 各服务的版本（如果想换版本，需要先去[Docker hub](https://hub.docker.com/search?q=&type=image)确认版本是否存在）
* 各服务的本地的数据卷路径（如果想调整目录结构）
* PHP所需扩展（可选扩展基本齐全，按项目所需安装即可）
* 数据库密码

docker-compose.yml 的主要配置项
* 数据卷的对应
* 端口（可以修改端口映射，或者项目较多可以添加新端口）

### 第二步：构建镜像和后台挂载
```
docker-compose build
docker-compose up -d
```

### 第三步：迁移项目www目录（如果仅创建新项目，则跳过此步）

**注意：**要将项目内原本 `localhost` 或 `127.0.0.1` 都要修改为所用的服务名，如 `mysql`, `redis`, `nginx`，否则会导致无法连接

### 第四步：进入服务

如何进入服务
* PHP：`docker exec -it php /bin/bash` 默认已配置好composer，可以直接使用
* Nginx：`docker exec -it nginx sh`
* Node：`docker exec -it php /bin/bash` npm直接使用即可

进入后可以用相关命令安装依赖或创建项目即可
