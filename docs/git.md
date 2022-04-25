# git

## 实例
+ [Git创建一个空的分支]https://juejin.cn/post/6844904056436031496
+ [Git使当前分支为空分支](https://www.weipxiu.com/3710.html)
+ 撤销创建仓库后第一次提交
    ```
    git update-ref -d HEAD
    ```
+ 删除远程分支
<br>如果分支是protect分支，需要先设置为非protect，否则执行不成功
    ```
    git push origin --delete <branchName>
    ```

+ 内网gitlab组件库fork新库(原始仓库地址完全拷贝到目标仓库地址)
  ```
  git clone --bare 原始仓库地址
  cd project.git（project即为你的项目名称）
  git push --mirror http：//...(目标仓库地址)
  ```

+ 从repo A 迁移 多个文件夹到 repo B 中，要求保留历史记录；
方案-： subtree split