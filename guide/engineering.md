# 工程规范

## 路由管理

- **错误示范**：
模块过大，用一个文件管理路由


- **正确引用**：
供统一入口，引入各模块路由 (代码更优雅可参考es6的扩展运算符)

`router` **模块目录**
```
router
  ├─ index.js                 # 路由入口文件
  ├─ action.js                # action 模块
  ├─ base.js                  # base 模块
  └─ other.js                 # other 模块
```
`router` **文件内容**
``` js
// index.js
import Vue from 'vue';
import Router from 'vue-router';
import action from './action.js';
import base from './base.js';
import other from './other.js';

export default new Router({
  routes: [
    {
      path: '/',
      redirect: '/basic/vue-study',
      hidden: true
    },
    ...action,
    ...base,
    ...other
  ]
});
```

``` js
// action.js 采用对象扩展的形式
import BasicDemoComp from '../page/basic/index.vue';

export default [
  {
    path: '/basic',
    title: '基本demo',
    component: BasicDemoComp
  }
];
```

``` js
// other.js 采用es6扩展的形式
import Others from '../page/others/index.vue';
import GotoFrame from '../page/others/goto-frame.vue';

export default [
  {
    name: 'Others',
    path: '/others',
    title: '其他',
    component: Others,
    children: [
      {
        name: 'GotoFrame',
        path: 'goto-frame',
        title: '外框Tab跳转',
        component: GotoFrame
      }
    ]
  }
];
```

## 静态文件管理
- 通用文件，由公共组统一管理
- 项目独有的文件，放置在项目的 `assets` 目录中。如 `image`, `style`, `js`, `font` 等

```
src
 └─assets
    ├─fonts                   # 字体
    ├─images                  # 图片
    └─style                   # 样式
       color.scss
       index.scss
```

## 目录结构
```
项目名
  ├─build                     # 构建流程文件文件
  ├─config                    # 配置文件
  ├─dist                      # 构建后的静态文件
  ├─src                       # 业务代码文件
  │  ├─api                    # 接口文件
  │  ├─assets                 # 静态文件
  │  ├─business               # 较为复杂的业务逻辑
  │  ├─components             # 业务中的可复用组件
  │  ├─config                 # 业务中的配置文件
  │  ├─modules                # 多页面应用
  │  ├─pages                  # 业务中的路由文件
  │  ├─router                 # 路由配置文件
  │  ├─store                  # vuex 文件
  │  └─tools                  # 业务中的可复用工具库
  ├─static                    # 外部引用库、全局配置文件
  ├─.babelrc                  # babel 配置文件
  ├─.gitignore                # git 忽略配置
  ├─package.json              # npm 包配置文件
  └─README.md
```

## 数据缓存

### vuex
- 一个模块一个文件管理
```
store
  ├─ index.js                # vuex 入口文件
  ├─ actions.js              # 根级别的 action
  ├─ mutations.js            # 根级别的 mutation
  ├─ getters.js
  ├─ state.js
  ├─ mutation-types.js       # 使用常量替代 mutation 事件类型
  └─ modules
      ├─ cart.js             # 购物车模块
      └─ products.js         # 产品模块
```

### locastorage

请参考 [vue-localstorage](https://github.com/pinguinjkeke/vue-local-storage)。在项目中的使用方法如下：

``` js
<script>
  ...
  this.$ls.get('userInfo.userId');
  this.$ls.set('userInfo.userId', '...');
  ...
</script>

```

<!-- 可用公共js文件进行配置
``` js
export default {
  get: key => {
    if (!window.localStorage) return false
    return JSON.parse(window.localStorage.getItem(key) || '')
  },
  set: (key, data) => {
    if (!window.localStorage) return false
    window.localStorage.setItem(key, JSON.stringify(data))
    return true
  },
  has: key => window.localStorage && window.localStorage.hasOwnProperty(key)
}
``` -->

## 网络请求

### getData
基于 [axios](https://github.com/axios/axios) ，重新封装网络请求

### RESTful
请求接口的设计风格采用 `RESTful`。

### 路由命名
url命名要简单明了，层次清晰，比如用户设置`user/setting`, 不能写成`userSetting`或`user/userSetting`,如无必要尽量避免两个单词拼接的情况，两个单词拼接采用`kebab-case`命名，以'-'分隔，如`/user/roles-list`
