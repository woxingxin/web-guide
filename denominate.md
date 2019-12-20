# 命名规范
设计参考 [https://www.npmjs.com/package/change-case](https://www.npmjs.com/package/change-case)

## 规范详情
- 命名空间用 [dotCase](/guide/denominate.html#dotcase)
- 文件夹、文件名用 [kebab-case](/guide/denominate.html#kebab-case) (短横线命名)
- js变量、函数名用 [camelCase](/guide/denominate.html#camelcase) (驼峰命名)
- js常量用 [CONSTANT_CASE](/guide/denominate.html#constant-case)
- vue组件变量、react中class类用 [PascalCase](/guide/denominate.html#pascalcase) (帕斯卡命名)

## dotCase
`dotCase` 命名具体表现为 `xxx.xxx`，用于同名变量的区分，将变量控制在不同模块下，便于变量管理。
``` js
let foo = {
  id: '1',
  name: 'apple'
};
let bar = {
  id: '2',
  name: 'banana'
};
==> a.name !== b.name
```

## pathCase
`pathCase` 命名具体表现为 `xxx/xxx`，适用于命名空间或路径的管理。

## kebab-case
`kebab-case` 命名又称烤串式命名、短横线命名，适用于文件夹、文件命名。

例如iview3.0中的 `auto-complete.vue`，用法是单个单词之间用 `-` 字符相连，单词全为小写。
```
common
  └─async-validator
      form-item.vue               # ✓ ok
      form-item-section.vue       # ✓ ok
      index.js                    # ✓ ok

common
  └─async-validator
      form_item.vue               # ✗ avoid
      formItemSection.vue         # ✗ avoid
      Index.js                    # ✗ avoid
```

## camelCase
`camelCase` 命名又称驼峰命名。用于js中普通变量命名。
``` js
let orgManageName = '';
```
## CONSTANT_CASE
`CONSTANT_CASE` 的特点是字母全大写，单词用 `_` 分割。适用于js中常量的命名。
``` js
const CONSTANT_ORGNAME = '';
```
## PascalCase
`PascalCase` 命名又称帕斯卡命名，与驼峰命名的区别是帕斯卡命名要求首字母大写。适用于对象变量、组件变量、`jsx`。
``` js
// 组件变量引入
import DropDown from '../select/dropdown.vue';

// react代码段
export default class HeaderView extends Component {
  render () {
    return (
      <View style={ styles.topViewStyle }>
        <TouchableOpacity onPress={ this.onPress } style={ styles.left }>
        </TouchableOpacity>
      </View>
    );
  }
}
```
