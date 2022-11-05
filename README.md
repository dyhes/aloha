# Aloha

## 所需环境
* GIT
* Docker-Compose
* Node 14.4.0(推荐版本)
* npm

## 下载nodejs依赖

```sh
npm install
```

## 在本地运行RChain节点与Aloha服务器

整个流程由[package.json](package.json)中的预定义指令操纵

通过`docker-compose`运行Aloha、RChain、Postgresql镜像

```sh
npm run start-docker
```

查看镜像日志

```sh
# 查看所有镜像日志
npm run dc -- logs -f

# 仅查看boot镜像日志
npm run dc -- logs -f boot
```

### 检查镜像是否运行成功

Aloha: [https://localhost:1443/](https://localhost:1443/).  
RNode: [http://localhost:40403/status](http://localhost:40403/status).

（若运行出错可查看日志排查错误原因）

## 初始化组织账号

仅需在第一次启动时运行

```sh
npm run zulip-gen-org-link
```

## 部署智能合约

仅需在第一次启动时运行

```sh
npm run iddb-deploy
```
将输出的uri赋值给[**.env**](.env)文件的 __IDDB_CONTRACT_URI__ 

当 __.env__ 文件中的 __IDDB_CONTRACT_URI__ 已经更新时，运行

```sh
npm run myzulipdb-deploy
```
同上，将输出的uri赋值给[**.env**](.env)文件的 __DB_CONTRACT_URI__

_提示: 每次重新运行`iddb-deploy` 和 `myzulipdb-deploy` 重新部署时需要重新更新 __.env__ 文件。_

## 链接Aloha服务器与RChain节点

运行

```sh
npm start
```
