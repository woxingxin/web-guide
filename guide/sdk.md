# SDK组件管理

## 目录、文件

- **目录命名用 `kebab-case`**
```
common                            // ✓ ok
  ├─async-validator               // ✓ ok
  └─biz-moudles                   // ✓ ok

Common                            // ✗ avoid
  ├─asyncValidator                // ✗ avoid
  └─biz_moudles                   // ✗ avoid
```

- **目录结构简名，避免重复**
```
common                            // ✓ ok
  ├─async-validator               // ✓ ok
  └─biz-moudles                   // ✓ ok

common
  ├─common-async-validator        // ✗ avoid
  └─common-biz-moudles            // ✗ avoid
```

- **文件命名用 `kebab-case`**
```
common
  └─async-validator
      form-item.vue               // ✓ ok
      form-item-section.vue       // ✓ ok
      index.js                    // ✓ ok

common
  └─async-validator
      form_item.vue               // ✗ avoid
      formItemSection.vue         // ✗ avoid
      Index.js                    // ✗ avoid
```

- **文件与目录结构语义化，避免重复**
```
common
  └─validator
      form-item.vue               // ✓ ok
      index.js                    // ✓ ok

common
  └─validator
      common-validator-form.vue   // ✗ avoid
      commonValidatorIndex.js     // ✗ avoid
```

- **每个目录下都有一个 `index` 文件作为入口文件**
``` {3,8}
common
  ├─async-validator
  │   index.js
  │   form-item.vue
  │   form.vue
  │
  └─biz-moudles
      index.js
      buy-cart.vue
      order-detail.vue
```

- **单个文件表示一个模块的，也可以作为入口文件**
``` {3,8}
common
  ├─async-validator
  │   index.js
  │   form-item.vue
  │   form.vue
  │
  └─biz-moudles
      index.js
      buy-cart.vue
      order-detail.vue
```

## 组件开发

### 命名

- **文件命名用 `kebab-case`**
```
common
  └─async-validator
      form-item.vue               // ✓ ok
      form-item-section.vue       // ✓ ok

common
  └─async-validator
      form_item.vue               // ✗ avoid
      formItemSection.vue         // ✗ avoid
```

- **组件变量命名用 `PascalCase`**
``` js
import Welcome from '@/components/welcome';           // ✓ ok
import OrderDetail from '@/components/order-detail';  // ✓ ok

import welcome from '@/components/welcome';           // ✗ avoid
import orderDetail from '@/components/order-detail';  // ✗ avoid
```

- **公共组件加上前缀 `XX`**
``` js
import XXCopyright from '@/components/copyright';   // ✓ ok

import Copyright from '@/components/copyright';       // ✗ avoid
```

- **template中引用组件标签 `kebab-case`**
``` html{3,9}
<template>
  <div id="app">
    <xx-order-detail />                             // ✓ ok
  </div>
</template>

<template>
  <div id="app">
    <XXOrderDetail />                               // ✗ avoid
  </div>
</template>
```

### 组件划分

- **基础组件**

与业务无关，只负责接收数据，展示数据和交互。

- **配置型业务组件**

基于一个或多个基础组件，向基础组件传送数据，控制基础组件实现展示数据和交互。

- **标签型业务组件**

基于配置型业务组件，将获取数据等逻辑封装起来，直接使用标签实现展示数据和交互。

### 组件开发

参考[组件划分](/guide/SDK-compenents.html#组件划分)，按照 `基础组件` :heavy_minus_sign::arrow_forward: `配置型业务组件` :heavy_minus_sign::arrow_forward: `标签型业务组件` 的顺序做渐进式开发。

## 样式开发

- **目录结构**
```
style
  ├─ entry              # 样式打包入口
  ├─ theme              # 样式主题
  ├─ vendors            # 用来存放所有外部库和框架(iview、ztree)
  └─ lib
      ├─ common         # 通用样式(将开放给业务组使用)
      ├─ base           # 基础(rest)
      ├─ kit            # 工具包（全局变量、函数、混合）
      ├─ components     # 组件样式（表格、表单)
      └─ classic-page   # 经典页面
```

- **文件管理**

SDK涉及的样式【DEMO除外】`必须`单独抽离为`独立样式文件`存放到`style`目录下，每个目录下要有一个`index`文件作为入口文件

```css
css
└─common
    public.scss
    layout.scss
    index.scss
```

```css
// index.scss

@import "base";
@import "layout";

```

- **文件命名规则**

采用  `kebab-case`，本着简单、直观原则，样式文件命名应与对应功能页面名保持一致。如：组件名`modal.vue`样式名应该为`modal.scss`

- **样式命名规则**

`公司前缀（xx）- 模块名（语义） + "-" + "元素" "-" + "修饰"`，如：`.xx-classicpage-m12`

- **变量或混合命名规则**

采用  `kebab-case`，如：`$color-table-choose-bg` `@mixin border-top-dashed`

- **代码规范**


> **禁用** 行内样式

> **禁用** `!important`

 > **统一** 组件的尺寸、颜色、文字都应使用变量


- **注释规则**

> 为提高团队内协助的效率以及代码的可维护性，工具包下涉及的样式文件必须提供**文件级注释**,。

 采用 `///`  作为 Sass的注释标识,参照[sassDoc](http://sassdoc.com/annotations/)

 ```CSS
// 跨浏览器的渐变背景，垂直渐变，自上而下
///
/// @group 外观
/// @name gradient_vertical
/// [@param](/user/param) {Color} $start-color [#555] - 渐变的开始颜色
/// [@param](/user/param) {Color} $end-color [#333] - 渐变的结束颜色
/// [@param](/user/param) {Number} $start-percent [0%] - 渐变的开始位置，需要以百分号为单位
/// [@param](/user/param) {Number} $end-percent [100%] - 渐变的结束位置，需要以百分号为单位
@mixin gradient_vertical($start-color: #555, $end-color: #333, $start-percent: 0%, $end-percent: 100%){
  background-image: -webkit-gradient(linear, left top, left bottom, color-stop($start-percent, $start-color), color-stop($end-percent, $end-color)); // Safari 4-5, Chrome 1-9
  background-image: -webkit-linear-gradient(top, $start-color $start-percent, $end-color $end-percent);  // Safari 5.1-6, Chrome 10+
  background-image: -moz-linear-gradient(top, $start-color $start-percent, $end-color $end-percent); // Firefox 3.6+
  background-image: -o-linear-gradient(top, $start-color $start-percent, $end-color $end-percent);  // Opera 12
  background-image: linear-gradient(to bottom, $start-color $start-percent, $end-color $end-percent); // Standard, IE10, Firefox 16+, Opera 12.10+, Safari 7+, Chrome 26+
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#{ie-hex-str($start-color)}', endColorstr='#{ie-hex-str($end-color)}', GradientType=0); // IE9 and down
}

 ```

## 工具库开发

- **目录，文件命名采用 `kebab-case`**

- **模块内容过大时用目录加文件，内容很小时直接用文件**
```
js
│  basic-tools.js
│  browser.js
│  git-config.js
│  msg.js
│  route-uitl.js                  // 一个文件可以将模块内容表达清楚
│
└─order                           // 模块的内容过多时，用目录加文件管理
    index.js
    user-validate.js
    payment.js
```

- **每个目录下要有一个`index`文件作为入口文件**，其作用是引入文件并导出模块的内容
``` js
import userValidate from './user-validate';
import payment from './payment';

export default {
  userValidate,
  payment
};
```

- **工具库需要暴露一个全局变量**

参考 `jQuery、zepto、lodash` 等知名工具库，将其设计为 [UMD](https://github.com/umdjs/umd) 模式，既可以通过包的模式引入，又可以通过 script 标签引入。

## 定制化

- **模块文件必须有注释**

@module 模块名称 <br />
@entry 是否入口文件，并声明入口文件名称 <br />
@name 模块名称，模块被外部调用时使用的名称，如果没有该标签，则使用 @module <br />
@memberof 隶属于模块，(以根模块为起点，用 '.' 分离)

chart/index.js 文件
``` js
/**
 * 购物车模块
 * @module Chart
 * @entry Chart
 * @memberof SDK.JsTool
 */
```

table/index.vue 文件
``` js
/**
 * 表格组件
 * @module Table
 * @memberof SDK.VueComponent
 */
```

style/color.scss 文件
``` css
/**
 * 颜色变量
 * @module Color
 * @entry Color
 * @memberof SDK.Style
 */
```


- **版本**

采用 semver (语义化版本)。请参考[版本管理](./release.md)
