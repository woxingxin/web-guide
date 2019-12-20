# 发布规范

## 分支管理

前端开发采用 `Git` 做版本控制，分支管理采用 `gitflow`。

::: tip 主要分支
  - **master(stable)：** 主分支，永远处在即将发布 (production-ready) 状态
  - **develop：** 开发分支，最新的开发状态
:::

::: tip 辅助分支
  - **feature：** 开发新功能的分支, 基于 `develop`, 完成后 merge 回 develop
  - **release：** 准备要发布版本的分支, 用来修复 bug. 基于 `develop`, 完成后 merge 回 develop 和 master
  - **hotfix：** 修复 master 上的问题, 等不及 release 版本就必须马上上线. 基于 `master`, 完成后 merge 回 master 和 develop
:::

![An image](../static/img/gitflow.png)

::: warning 注意
  - 分支的命名空间用 [pathCase](/guide/denominate.html#pathcase)，如 `feature/style`、 `release/1.2.0`、 `hotfix/1.3.1`
  - 每次发布时 Git 必须打 Tag
  - Tag 的命名与 [版本管理](/guide/release.html#版本管理) 保持一致，如 `1.2.0`、 `1.3.1`
:::

关于 `gitflow` 的详细介绍请参考：

[GIT版本管理：Git Flow模型](https://www.jianshu.com/p/62b4ebe283f3)

[Git基本命令和GitFlow工作流](https://www.cnblogs.com/myqianlan/p/4195994.html)

## 版本管理

前端开发的版本管理采用 `semver` (语义化版本)，版本格式为：`主版本号.次版本号.修订号` `(x.y.z)`。

``` json{3}
{
  "name": "...",
  "version": "1.0.0",
  "description": "...",
  "main": "index.js",
  "devDependencies": {
    "vuepress": "^0.14.1",
    "vuepress-theme-vue": "^1.1.0"
  },
  "author": "",
  "license": "ISC"
}
```

- 当项目有巨大变化时，如前端框架从 [angular.js](https://angular.io/) 变成了 [vue.js](https://cn.vuejs.org/)，升级主版本 `((x + 1).y.z)`

- 项目每周一迭代，每次迭代发布时，升级次版本号 `(x.(y + 1).z)`

- 如果线上发现有 Bug ，对 Bug 修复后再发布时，升级修订号 `(x.y.(z + 1))`

- 另外还有 `alpha`、 `beta`、 `rc` 等版本，如 `(x.y.z-alpha.m)`、 `(x.y.z-beta.m)`、 `(x.y.z-rc.m)`

关于 `semver` 的详细介绍请参考：

[语义化版本 2.0.0](https://semver.org/lang/zh-CN/)

[深入 Node 模块的安装和发布](https://segmentfault.com/a/1190000004221514)
