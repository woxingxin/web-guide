
# 代码规范

## HTML

### 语法：
- 引入 HTML5 规范，使用 `<!DOCTYPE html>`。
- 网站默认编码是 utf-8, `<meta charset="utf-8">`。
- 对于属性的定义，确保全部使用双引号，绝不要使用单引号。
- 每一个块级元素都另起一行，每一行都使用Tab缩进对齐（head 和 body 的子元素不需要缩进）。删除冗余的行尾的空格。
- 使用2个空格代替1个 Tab（大多数编辑器中可设置）。

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Page title</title>
</head>
<body>
  <img src="images/company-logo.png" alt="Company">
  <h1 class="hello-world">Hello, world!</h1>
</body>
</html>
```

### 代码书写顺序：
- 按照从上至下、从左到右的视觉顺序书写HTML结构。

### 常用标签释义：

标签|语义|嵌套常见错误
-|-|-
`<a></a>`	|超链接or锚 |	a不可嵌套a
`<span></span>` |内联容器|
`<p></p>`|  段落| 不能嵌套块级元素
`<div></div>`|块级容器| |
`<dl></dl>`|定义列表|只能嵌套dt和dd|
`<dt></dt>`|定义列表中的定义术语|只能以dl为父容器，对应多个dd|
`<dd></dd>`|定义列表中的定义（描述内容）|
`<table></table>` |表格|  只可嵌套表格元素
`<thead></thead>  `|表格表头| 只用于table
`<th></th>  `|表格中的标题单元格|  只用于tr
`<tbody></tbody>` |表格主体 |只用于table
`<td></td>`|  表格中的单元格|  只用于tr
`<tr></tr>` |表格行  |嵌套于table或thead、tbody、tfoot
`<tfoot></tfoot>` |表格表尾|  只用于table
`<ol></ol>  `|有序列表| 只能嵌套li  |
`<ul></ul>` |无序列表|  只能嵌套li
`<li></li>  `|列表项|  只能以ul或ol为父容器|
`<i></i>`|斜体||
`<em></em>`|强调文本||
`<strong></strong>`|  强调文本|
`<del></del>`|文本删除| |
`<h1></h1>`|标题|从h1到h6，不可嵌套块级元素|
`<br />	`|换行|
`<form></form>`|表单|
`<label></label>`|  标签为input元素定义标注|
`<input />  `|各种表单控件  |
`<textarea></textarea>`|  多行文本输入控件
`<select></select>` |列表框或下拉框|只能嵌套option或optgroup
`<option></option>` |select中的一个选项|  仅用于select
`<button></button>`|按钮| 不可嵌套表单元素
`<iframe></iframe>`|内嵌一个网页|
`<img />  `|图像|  |
`<link />`| 引用样式或icon|  不可嵌套任何元素
`<style></style>  `|引用样式| 不可嵌套任何元素
`<sub></sub>` |下标|
`<sup></sup>` |上标|
`<title></title>  `|文档标题| 只用于head
`<meta /> `|文档信息| 只用于head
`<script></script>`|  引用脚本| 不可嵌套任何元素| type,src

### 实用高于完美
尽量遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价.任何时候都要用尽量小的复杂度和尽量少的标签来解决问题

### 减少标签数量
在编写 HTML 代码时，需要尽量避免多余的父节点.很多时候，需要通过迭代和重构来使 HTML 变得更少. 参考下面的示例:

``` html

<!-- 不推荐 -->
<span class="avatar">
    <img src="...">
</span>

<!-- 推荐 -->
<img class="avatar" src="...">

```

### 属性顺序
HTML 属性应该按照特定的顺序出现以保证易读性.

- id
- class
- name
- data-*
- src, for, type, href
- title, alt

### Boolean 属性
不要为 Boolean 属性添加取值.
``` html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
<select>
    <option value="1" selected>1</option>
</select>
```

### 常用HTML字符实体名

(注：实体名对大小写敏感！)[详情](http://www.w3school.com.cn/html/html_entities.asp)：

字符|名称|实体名
-|-|-
`"`	|双引号|	`&quot;`
`&	`|&符|	`&amp;`
`<`	|左尖括号（小于号）|	`&lt;`
`>`	|右尖括号（大于号）|	`&gt;`
` `|空格|	`&nbsp;`

### 常用特殊字符实体名

（注：实体名对大小写敏感！）：

字符|名称|实体名
-|-|-
¥|	元	|`&yen;`
¦|	断竖线|	`&brvbar;`
©|	版权|	`&copy;`
®|	注册商标R	|`&reg;`
™|	商标TM|	`&trade;`
·	|间隔符|`	&middot;`
«|	左双尖括号|	`&laquo;`
»	|右双尖括号|	`&raquo;`
°|	度	|`&deg;	`
×|乘	|`&times;`
÷|	除	|`&divide;`
‰|	千分比|	`&permil;`

## CSS

### 引用
- head中引入css文件, 避免页面加载出现页面闪烁

- 自有css文件在第三方css后引入，提高自定义样式权重

- 不要直接修改第三方CSS文件内的样式

- 减少使用javascript 操作dom的style属性来修改样式, 推荐使用修改class的方式来修改样式

-  **禁止**使用行内样式，尽量做到样式结构分离（除非特别极端的情况）

- 所有的样式应集中在外部的css文件中, 方便维护、管理和方便浏览器缓存css部分

### 语法
- 使用类选择器，不要使用id选择器。id 是唯一的，从而导致了如果以 id 为选择器，后面相同的模块就无法重用了。

- 使用2个空格代替1个 Tab（大多数编辑器中可设置）。

- 选择器、属性和值都使用小写。

- 当一个样式规则包含多个 selector 时，每个选择器必须独占一行。
- 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
- 每条声明语句的 `: ` 后应该插入一个空格。
- 所有声明语句都应当以分号 `;`（方便压缩工具"断句"）。
- 为选择器中的属性添加双引号，例如，`input[type="text"]`。
-  色值用十六进制，少用rgb,因为使用rgb是一个函数，它还要计算一下转换。如果是带有透明度的再用rgba。用 `color: rgb(80, 80, 80)` 代替 `color: #505050`。
-  十六进制值应该全部小写，如果色值的六个数字一样，那么写3个就好，因为在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。例如，用 `#fff` 代替 `#ffffff`。
- 避免为 0 值指定单位，例如，用 `margin: 0`; 代替 `margin: 0px`。

-  不要设置太大的z-index，原则上业务逻辑代码的z-index应该保持在个位数（除非是需要覆盖公共样式）例如：`z-index: 3`。

-  **慎用** `!important`,important用来覆盖属性，特别是在CSS里面用来覆盖style里的属性。但是important还是少用为妙，如果要覆盖还是先通过增加选择器权重的方式。

-  选择器一般不要写超过3个，因为Chrome里面是用递归从最后一个选择器一直匹配到第一个，选择器越多匹配的时间就越长，并且代码的可读性也比较差。

- 媒体查询位置尽量将媒体查询的位置靠近他们相关的规则. 不要将他们一起放到一个独立的样式文件中, 或者丢在文档的最底部

-  相关的属性声明应当归为一组，并按照下面的顺序排列：`Positioning` => `Box` => `modelTypographic`  =>  `Visual`。


```css
 /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 单条声明的声明块

- 在一个声明块中只包含一条声明的情况下，为了易读性和快速编辑可以考虑移除其中的换行. 所有包含多条声明的声明块应该分为多行。

### 属性简写

坚持限制属性取值简写的使用，属性简写需要你必须显式设置所有取值。常见的属性简写滥用包括:

- padding
- margin
- border
- border-radius

### SASS
- **不要让嵌套选择器的深度超过 3 层**

如果有必要用到嵌套选择器，把它们放到最后，在规则声明和嵌套选择器之间要加上空白，相邻嵌套选择器之间也要加上空白。嵌套选择器中的内容也要遵循上述指引。

```css
.btn {
  background: green;
  font-weight: bold;

  .icon {
    margin-right: 10px;
  }
}
```

- **变量命名规则**

变量名应使用[kebab-case](denominate.html#dotcase)（例如 `$my-variable`）。

### 命名规则
命名方法：模块名（语义） + "-" + "元素" "-" + "修饰"

`< input  class = "search-form-input" >`

- **常用模块名:**：

1. **页面结构**

- 容器: container
- 页头：header
- 内容：content/container
- 页面主体：main
- 页尾：footer
- 导航：nav
- 侧栏：sidebar
- 栏目：column
- 页面外围控制整体布局宽度：wrapper
- 左右中：left right center

2.**导航**
- 导航：nav
- 主导航：mainbav
- 子导航：subnav
- 顶导航：topnav
- 边导航：sidebar
- 左导航：leftsidebar
- 右导航：rightsidebar
- 菜单：menu
- 子菜单：submenu
- 标题: title
- 摘要: summary

3.**功能**
- 标志：logo
- 广告：banner
- 登陆：login
- 登录条：loginbar
- 注册：regsiter
- 搜索：search
- 功能区：shop
- 标题：title
- 加入：joinus
- 状态：status
- 按钮：btn
- 滚动：scroll
- 标签页：tab
- 文章列表：list
- 提示信息：msg
- 当前的: current
- 小技巧：tips
- 图标: icon
- 注释：note
- 指南：guild
- 服务：service
- 热点：hot
- 新闻：news
- 下载：download
- 投票：vote
- 合作伙伴：partner
- 友情链接：link
- 版权：copyright

### 理解CSS优先级
a = 标签内嵌样式
b = ID选择器
c = 类选择器
d = 标签选择器
以下组合值越大，优先级越高：

选择器|a|b|c|d
-|-|-|-|-
style="..." |	1	|0|	0|	0
#father #child	|0|	2	|0|	0
#father .child	|0|	1|	1|	0
div#father	|0|	1	|0|	1
#father div|	0	|1|	0|	1
#father	|0|	1	|0	|0
div.father .child|	0|	0	|2	|1
div.father p |	0|	0|	1	|2
.father p |	0|	0	|1|	1
div.father |	0	|0	|1	|1
.father	|0|	0	|1	|0
div p	|0|	0	|0|	2
p	|0|	0	|0|	1
**注意** `!important`可以大于以上优先级。

### 注释规范
-  建议使用行注释 (在 Sass 中是 //) 代替块注释。
-  建议注释独占一行。避免行末注释。
- 兼容性处理或者针对特定浏览器的 hack
```css
// Mixins Function 通用方法描述
```

## JS

### 语法
- 使用2个空格代替1个Tab（大多数编辑器中可设置）。
- 变量名使用驼峰法来命名(camelCase)，例如：
```js
var firstName = "John";
var lastName = "Doe";
```
- 常量命名必须采用全大写的命名( CONSTANT_CASE)，且单词以_分割，常量通常用于ajax请求url，和一些不会改变的数据。例如：
```js
const MAX_COUNT = 10;
const URL = 'http://xx.xx.com';
```
- 函数名使用统一采用驼峰命名法(camelCase)，例如：
```js
 function createNums () {
   //....

 }
```
- 置空基础类型用` undefined`,引用类型用` null`。
- 统一按照[JS代码规范](https://github.com/standard/standard/blob/master/docs/RULES-zhcn.md)要求编写代码,统一使用[ESLint](http://eslint.cn/ )做为一个代码规范和错误检查工具。

- 复杂语句的通用规则:

1. 将左花括号放在第一行的结尾。

2. 左花括号前添加一空格。

3. 将右花括号独立放在一行。
```js
if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### 注释
1. 单行注释

- 说明：单行注释以两个斜线开始，以行尾结束。

- 语法： `//` 这是单行注释。

- 使用方式：单独一行 `//` (双斜线)与注释文字之间保留一个空格。
```js
// 设置title的值
setTitle();
```
2. 多行注释
- 说明：以 `/* ` 开头， `*/ ` 结尾。
- 语法： `/* 注释说明 */` 。
- 使用方法：若开始/和结束/都在一行，推荐采用单行注释。若至少三行注释时，第一行为/，最后行为/，其他行以开始，并且注释文字与保留一个空格。
```js
/*
* 代码执行到这里后会调用setTitle()函数
* setTitle()：设置title的值
*/
setTitle();
```

3. 函数(方法)注释
- 说明：函数(方法)注释也是多行注释的一种，但是包含了特殊的注释要求，参照[JSDoc](http://www.css88.com/doc/jsdoc/about-namepaths.html)。
```js
/**
 * 合并Grid的行
 * @param grid {Ext.Grid.Panel} 需要合并的Grid
 * @param cols {Array} 需要合并列的Index(序号)数组；从0开始计数，序号也包含。
 * @param isAllSome {Boolean} ：是否2个tr的cols必须完成一样才能进行合并。true：完成一样；false(默认)：不完全一样
 * @return void
 * @author polk6 2015/07/21
 * @example
 * _________________                             _________________
 * |  年龄 |  姓名 |                             |  年龄 |  姓名 |
 * -----------------      mergeCells(grid,[0])   -----------------
 * |  18   |  张三 |              =>             |       |  张三 |
 * -----------------                             -  18   ---------
 * |  18   |  王五 |                             |       |  王五 |
 * -----------------                             -----------------
 */
function mergeCells(grid: Ext.Grid.Panel, cols: Number[], isAllSome: boolean = false) {
  // Do Something
}
```

常用注释关键字：(只列出一部分，并不是全部)

注释名|	语法|	含义|	示例
-|-|-|-
@param|	@param 参数名 {参数类型} 描述信息	|描述参数的信息	|@param name {String} 传入名称
@return	|@return {返回类型} 描述信息|	描述返回值的信息	|@return {Boolean} true:可执行;false:不可执行
@author|	@author 作者信息 [附属信息：如邮箱、日期]	|描述此函数作者的信息|	@author 张三 2015/07/21
@version|	@version XX.XX.XX	|描述此函数的版本号	|@version 1.0.3
@example|	@example 示例代码	|演示函数的使用	|@example setTitle(‘测试’)

## VUE

### 语法
- 对于单文件组件，每个文件中 `template`=>  `script`=>  `style` 标签的顺序保持一致。
- 在` data` `created` `methods` 等中间加一个空行，便于阅读。[详情](https://cn.vuejs.org/v2/style-guide/index.html#%E7%BB%84%E4%BB%B6-%E5%AE%9E%E4%BE%8B%E9%80%89%E9%A1%B9%E4%B8%AD%E7%9A%84%E7%A9%BA%E8%A1%8C-%E6%8E%A8%E8%8D%90)

- [scoped](https://cn.vuejs.org/v2/style-guide/index.html#%E4%B8%BA%E7%BB%84%E4%BB%B6%E6%A0%B7%E5%BC%8F%E8%AE%BE%E7%BD%AE%E4%BD%9C%E7%94%A8%E5%9F%9F-%E5%BF%85%E8%A6%81)目前暂时不做强制要求，所有组件最外层DIV 需要一个<strong class="font-red">全局的class</strong>达到样式隔离避免样式污染,命名规则：<strong class="font-red">工程-文件路径-文件名</strong>

- JS使用两个空格进行缩进

- style中的样式要全部采用[sass](ttps://www.sass.hk/docs/) 的开发模式

```html
<template>
  <!-- 最外层class命名规范 工程-文件路径-文件名 -->
  <div class="demo-basic-vueStudyChild-attrDemo">
  <!--必须在div中编写页面-->
  </div>
</template>

<!-- JS -->
<script>
  export default {
    name: '',
     // 注册
    components: {
    }
    // 组件属性、变量
    props: {
      bar: {}, // 按字母顺序
      foo: {},
      fooBar: {}
    },

    // 变量
    data () {
      return {
      }
    },

    // 计算属性
    computed: {
    },

    // 挂载成功后
    mounted () {
    },

    // 定义方法
    methods: {
    }

  }
</script>

```

- 多个特性的元素，每个特性应该单独一行。[详情](https://cn.vuejs.org/v2/style-guide/index.html#%E5%A4%9A%E4%B8%AA%E7%89%B9%E6%80%A7%E7%9A%84%E5%85%83%E7%B4%A0-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

```html
  // Good example
  <MyComponent
    foo="a"
    bar="b"
    baz="c"
  />

  // Bad example
  <MyComponent foo="a" bar="b" baz="c"/>

```

### vue文件方法声明顺序
```
  - name
  - components
  - props
  - data
  - computed
  - watch
  - created
  - mounted
  - beforeDestroy
  - metods
  - filter
```

### 组件命名规范

#### 命名可遵循以下规则：
-  有意义的名词、简短、具有可读性
-  以小写开头，采用短横线分割命名[kebab-case](denominate.html#kebab-case)
-  公共组件命名以公司名称简拼为命名空间(xx-xx.vue)
-  文件夹命名主要以功能模块代表命名

### 注释规范
> 代码注释在一个项目的后期维护中显的尤为重要，所以我们要为每一个被复用的组件编写组件使用说明，为组件中每一个方法编写方法说明。

 **以下情况，务必添加注释**

- 公共组件使用说明。

-  各组件中重要函数或者类说明。
- 复杂的业务逻辑处理说明。
-  特殊情况的代码处理说明,对于代码中特殊用途的变量、存在临界值、函数中使用的hack、使用了某种算法或思路等需要进行注释描述。


 **语法**

-  单行注释使用 `//`。

```js
// 来说明该方法主要作用
```

- 多行注释必须以 `/**` （至少两个星号）开头 `*/` 结尾。

```js
/**
 * 组件名称
 * @module 组件存放位置
 * @desc 组件描述
 * @author 组件作者 xp
 * @date 2019年12月19日17:22:43
 * @param {Object} [title] - 参数说明
 * @param {String} [columns] - 参数说明
 * @example 调用示例
 * <xx-table :title="title" :columns="columns" :tableData="tableData"></xx-table>
 */

```

<style>
.font-red {
  color:#f00;
}
</style>


### 待办事项

在代码的注释中使用 TODO (全大写)关键字来标识待办事项, 使用TODO(联系人) 的形式附上联系信息(姓名, 邮箱等)方便联系; 在冒号后加上待办事项内容. 在代码发布时要确认代码中无任何TODO标识.

``` javascript
// TODO(张工): 参数暂未校验
funtion submitOrder (data) {
    ....
}
```
