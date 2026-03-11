# AI开发规范

> 编辑代码时，如发现当前文件未按本规范执行，应及时优化并补齐（例如缺少注释则补齐），确保与本规范一致，注意不要出现中文乱码，使用 UTF-8 编码

- 执行前读取 `AGENTS_BUSINESS.md`
- 不要执行 `package.json` 中定义的脚本命令

## 注释

- template 内每个功能模块需添加注释，且注释前必须空一行
- template 内模块注释需描述业务含义，不得使用 `模块: div` 这类无实际语义的注释
- 每一个函数、变量、类型都需要生成注释
- 导出的类型需要注释
- 导出的对象需使用 `/** @description xxx */` 格式注释
- 注释双斜杠后面不能加空格
- Vue 生命周期不需要加注释
- Vue 监听器相关的方法使用 `/*  */` 注释，而不是 `@description`
- 注释内容统一使用中文
- 原有注释语义清晰时，不得擅自删除、替换或改写原意，仅可在缺失时补齐
- 自定义函数使用 `/** @description 这是一个函数 */` 格式注释
- 函数调用的上面不需要添加注释
- 函数内部的功能模块上方需要使用 `//` 注释说明
- define 开头的 Vue 方法上边不需要注释

```ts
/** 这是一个变量 */
const username = '';
/** 这是一个对象 */
const obj = {
  name: '',
  age: '',
};

/** @description 这是一个函数 */
const getUserInfo = (username: string, age: number) => {};

/** @description 这是一个类 */
class User {
  /** 用户名 */
  username: string;
  /** 年龄 */
  age: number;

  /** @description 构造函数 */
  constructor(username: string, age: number) {
    this.username = username;
    this.age = age;
  }

  /** @description 获取用户信息 */
  getUserInfo() {}
}

/** @description 用户信息 */
interface UserInfo {
  /** 名字 */
  name: string;
  /** 年龄 */
  age: number;
}

/** @description 多语言 */
type Lang = 'zh' | 'en';
```

## Typescript 类型

- 能自动推导的类型不必手动补充
- 函数统一使用箭头函数
- 若文件内的参数类型或泛型较长，在当前文件顶部定义 `interface` 或 `type`

## Vue

- 组件标签名称使用大驼峰
- 当页面变量名与标签属性名一致时，可以用 `:xxx` 简写绑定
- 布尔属性为真时（如 `:xxx="true"`），可以直接写成 `xxx`
- 页面结构顺序：`<script>` 在顶部，其次 `<template>`，最后 `<style>`
- 组件必须单独建文件夹，文件夹内包含 `index.vue`
- 当 Vue 文件中 `style` 标签内的 CSS 超过 50 行时，再抽离到 `index.less`
- 页面出现循环列表时，可将列表元素抽成组件，并在当前页面文件夹下创建 `components` 文件夹存放
- 页面功能模块较多时，可按区块抽成组件，避免单文件代码过多
- Vue 文件中可解耦的复杂功能逻辑应拆分为一个或多个 hooks，避免 `script` 中存在过多逻辑代码
- `ref` 绑定对象或者数组时，类型使用 `ref<xxx>()` 的泛型写法

## Vue 文件代码排版

代码排版应按照：

```ts
import

interface Props {
}
defineProps<Props>()

const $emit = defineEmits<{
  change: [v: number];
}>()

//Router 路由相关引入

//Pinia Store相关引入

//ref 绑定的 DOM 元素

//hooks

//非响应式数据

//响应式变量

//计算属性

//监听相关的方法

//创建生命周期

//函数

//销毁相关的生命周期
```

- `defineProps` 统一使用以下格式：

```ts
interface Props {
  add?: boolean;
  batchUpdate?: boolean;
  batchSend?: boolean;
}
defineProps<Props>();
```

- `defineEmits` 统一使用以下格式：

```ts
const $emit = defineEmits<{
  "tab-change": [index: number];
}>();
```

- 组件双向绑定统一使用 `defineModel`，格式如下：

```ts
const modelValue = defineModel<string>({ required: true });
const tabIndex = defineModel<number>("tabIndex", { required: true });
```

## 数据排版

- 变量与变量之间不要换行

```ts
//数字
//字符串
//布尔值
//数组
//对象
//优先使用空对象/空数组作为默认值，避免直接写带数据的对象或数组
```

## 通用代码使用

- 实现页面时，可直接复用 `src/components` 或 `src/styles` 下的通用代码
- 页面不必严格按设计图 1:1 还原，优先使用通用组件并保证结构与交互合理
- 图标优先使用 `vue-icons` 库提供的资源
- 无通用组件可复用时，使用 Element UI Plus 组件
- 页面出现滚动区域时，统一使用 `ElScrollbar`

## CSS

- CSS 中出现重复的颜色或尺寸时，可在顶部定义 CSS 变量复用
- 必要时可使用 Less 函数
- 使用 CSS 嵌套提高结构清晰度
- 编写 Less 时按 DOM 树结构进行嵌套

