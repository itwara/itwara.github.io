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
npm [config | c] set <key> <value> [--global]
npm [config | c] get <key>
npm [config | c] delete <key>
npm [config | c] list
npm [config | c] ls
npm [config | c] ls -l
npm [config | c] edit
npm get <key>
npm set <key> <value> [--global]
npm help [config | c]
```




## 二、npm包版本
<br>版本号：[^|~]major.major.patch-[标签].[扩展]
<br>如：3.2.3-beta.3


1. 版本限定
    + ~ 指定主版本号或者主次版本号相同
        ```
        ~1.2.3版本包括：>= 1.2.0 并且 < 1.3.0
        ~0.2.3版本包括：>= 0.2.0 并且 < 0.3.0
        ~0.0.3版本包括：>= 0.0.0 并且 < 0.0.9
        ```
        
    + ^ 第一个非零版本号相同
        ```
        ^1.2.3版本包括：>= 1.2.3 并且 < 2.0.0
        ^0.2.3版本包括：>= 0.2.3 并且 < 0.3.0
        ^0.0.3版本包括：>= 0.0.3 并且 < 0.0.4
        ```

2. semver 语义化版本控制
    - 主版本号（major）：软件做了不兼容的变更（breaking change 重大变更）；
    - 次版本号（minor）：Feature版本, 添加功能或者废弃功能，向下兼容；
    - 补丁版本号（patch）：Bug fix版本, bug 修复，向下兼容。
    - 版本升级
        + 升级大版本号：npm version major
        + 升级补丁版本号：npm version patch
        + 升级小版本号：npm version minor
        

3. dist-tag
    - demo: demo版本, 可能用于验证问题的版本;
    - dev: 开发版,开发阶段用的，bug 多，体积较大等特点，功能不完善;
    - alpha: 内部测试（α版本）, 用于内部交流或者测试人员测试，bug较多;
    - beta: 灰度测版(β版本), 较α版本，有较大的改进，但是还是有bug;
    - gamma:（γ版本）伽马, 较α和β版本有很大的改进，与稳定版相差无几，用户可使用;
    - rc：全写：Release Candidate（候选版本）
    - trial: 试用版本, 本软件通常都有时间限制，过期之后用户如果希望继续使用，一般得交纳一定的费用进行注册或购买。有些试用版软件还在功能上做了一定的限制;
    - stable: 稳定版;
    - csp: 内容安全版本, js库常用;
    - latest: 最新版本, 不指定版本和标签，npm 默认安最新版;


## 三、npm包依赖管理
    + 查看包安装目录
        ```
            npm root -g   //查看全局node_modules路径
            npm root      //查看本地node_modules路径
        ```
    + [依赖地狱](http://aprilandjan.github.io/npm/2019/08/02/how-npm-handles-dependency-version-conflict/)
    + [peerDependencies](https://www.cnblogs.com/wonyun/p/9692476.html)
    + package-lock
      把npm更新到v5.x.x以后, npm i会出现一种新的自动生成文件 - package-lock.json。
      package-lock.json简言之，就是锁定安装时包的版本号。
    + 自动化
      + makefile
      + autod


## 四、npm包发布


## 五、npm link
    + 查看项目中的link包
        npm link --global --depth 0
    + npm link 报 babel 错误
        + 原因：symlink 带来的路径问题; babel-loader 处理 import/export，软链接的 webpack：babel-loader 默认会从其真实路径读 .babelrc 配置，而不是从当前项目读相关配置；
        + 解决办法： 
           + [将webpackConfig.resolve.symlinks： false 即可改为从当前项目读相关配置](https://webpack.docschina.org/configuration/resolve/)
           + link 的库是不能有 node_modules
        + 参考资料
            + [当 webpack 遇上 symlink](https://segmentfault.com/a/1190000011100006)
            + [记一次npm不发布的情况下调试依赖包遇到的问题](https://blog.csdn.net/ffwangkun/article/details/118156019)


