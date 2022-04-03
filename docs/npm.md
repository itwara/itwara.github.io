# npm 
npm全称为Node Packaged Modules；它是一个用于管理基于node.js编写的package的命令行工具，其本身就是基于node.js写的。

## 一、npm配置
npmrc(npm running cnfiguration), npm运行时配置文件;

### 1. npm配置级别
npm获取配置有7种方式，优先级由高到底。

+ 命令行参数
   ```
   --registry https://registry.npm.taobao.org
   ```

+ 环境变量
    <br>以npm_config_为前缀的环境变量将会被认为是npm的配置属性。如设置registry可以加入这样的环境变量
    ```
    npm_config_registry=https://registry.npm.taobao.org
    ```

+ 项目级配置文件
    <br>你可以在项目的根目录下创建一个.npmrc文件，只用于管理这个项目的npm安装。
    + 只能通过操作文件来修改或者查看配置
        ```
        registry=https://registry.npm.taobao.org
        ```
+ 用户级配置文件
    <br>在你使用一个账号登陆的电脑的时候，可以为当前用户创建一个.npmrc文件，之后用该用户登录电脑，就可以使用该配置文件。可以通过 npm config get userconfig 来获取该文件的位置。
    +  操作文件来修改或者查看配置
        ```
        registry=https://registry.npm.taobao.org
        ```
    + 通过命令
        ```
        npm config get registry
        npm config set registry https://registry.npm.taobao.org
        ```

+ 全局级配置文件
   <br>一台电脑可能有多个用户，在这些用户之上，你可以设置一个公共的.npmrc文件，供所有用户使用。该文件的路径为：$PREFIX/etc/npmrc，使用 npm config get prefix 获取$PREFIX。如果你不曾配置过全局文件，该文件不存在。
    +  操作文件来修改或者查看配置
        ```
        registry=https://registry.npm.taobao.org
        ```
    + 通过命令
        ```
        npm config get registry -g
        npm config get registry --global
        npm config set registry https://registry.npm.taobao.org -g
        npm config set registry https://registry.npm.taobao.org --global
        ```
+ npm内置配置文件
    <br>安装npm的目录下的npmrc文件
    + 只能通过操作文件来修改或者查看配置
        ```
        registry=https://registry.npm.taobao.org
        ```

+ 默认配置
   <br>npm本身有默认配置参数，如果以上5条都没设置，则npm会使用默认配置参数。

### 2. 配置相关命令
```
npm config set <key> <value> [--global]
npm config get <key>
npm config delete <key>
npm config list
npm config ls
npm config ls -l
npm config edit
npm get <key>
npm set <key> <value> [--global]
npm help config
```