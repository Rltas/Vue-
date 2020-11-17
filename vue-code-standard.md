# vue代码风格

## 项目结构
* 标准结构（适用小型项目）

```js
public //里面的静态资源会被复制到输出目录（dist）中，不会经过webpack处理
----index.html //项目入口文件
src
----asstes
--------css //放一些全局css、font.css
--------images //项目图片
--------js //外部js
----components //一些公共组件、元素组件
----router //vue-router相关配置
----store //vuex相关配置
--------global //全局vuex使用配置
--------modules //模块化vuex使用配置
--------index.js //导出vuex所有配置
----utils //工具函数
--------utils.js //封装工具函数
--------storage.js //本地存储的存取
----api //请求相关配置
--------axios.js //封装使用的axios方法，拦截器等
--------config.js //项目接口配置、接口地址等
--------index.js //api出口
----config //本地静态配置文件
----views //所有路由组件
----main.js //vue入口文件
----App.vue //路由组件的顶层路由
```

## 风格
* 组件名为多个单词且首字母全大写。组件名应该倾向于完整单词而不是缩写。（这样做可以避免跟现有的以及未来的 HTML 元素相冲突，
  因为所有的 HTML 元素名称都是单个单词的。）

```js
MyComponent.vue
```

* 在DOM模板中使用 '-'。

```js
<my-component></my-component>
```
* 引入组件时，尽量加上后缀以免不必要得解析错误。

```js
import TodoList from 'components/TodoList.vue'
```

* props定义尽量详细，其命名应该始终使用 camelCase。

```js
props: {
  greetingText: {
    type: String,
    required: true,
    validator: (value) => {
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].includes(value);
    }
  }
}
```
* 为 v-for 都要设置上键值。

```js
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```
* 为组件样式设置作用域（scoped）,以免造成样式污染难以维护。
* 当使用mixin时，请带上私有前缀'$_',以避免与组件内容冲突。

```js
var myGreatMixin = {
  // ...
  methods: {
    $_myGreatMixin_update: function () {
      // ...
    }
  }
}
```

* 只要有能够拼接文件的构建系统，就把每个组件单独分成文件。（当需要编辑一个组件或查阅一个组件的用法时，可以更快速的找到它。）

```js
components/
|- TodoList.vue
|- TodoItem.vue
```
* 多个 attribute 的元素应该分多行撰写，每个 attribute 一行。以便容易阅读，一目了然。

```html
  <van-coupon-list
    :coupons="coupons"
    :chosen-coupon="chosenCoupon"
    :disabled-coupons="disabledCoupons"
    @change="onChange"
    @exchange="onExchange"
  />
  ```

## last
* 当不需要涉及双向数据绑定的数据，可以提出来写在一个js文件中，不需要全部写在data里面，减少双向数据绑定时所消耗的性能时间。
* Modal框的控制，一个页面种通常会存在很多个不同功能的弹框，若是每一个弹框都设置一个对应的变量来控制其显示，则会导致变量数量比较冗余和命名困难，
  可以使用一个变量来控制同一页面中的所有Modal弹框的展示。

```js

// 当modalType为对应的值时 展示其对应的弹框
data() {
    return {
        modalType: '' // modalType值为 modal1，modal2，modal3
        }
    }
```
* data数据切勿过度扁平化或者嵌套过深。
* 策略模式的使用，避免过多的if else判断，也可以替代简单逻辑的switch。

```js

const formatDemandItemType = (value) => {
    switch (value) {
        case 1:
            return '基础';
        case 2:
            return '高级';
        case 3:
            return 'VIP';
    }
}
 
// 策略模式
const formatDemandItemType2 = (value) => {
    const obj = {
        1: '基础',
        2: '高级',
        3: 'VIP',
    }
    
    return obj[value];
}
```
* 方法职责单一，任何时候尽量是的一个函数就做一件事情，而不是将各种逻辑全部耦合在一起，提高单个函数的复用性和可读性。

```js
created() {
  this.init();
},
methods: {
  init() {
    this.getDataList();
    this.dealData();
  },
  getDataList() {
    .....
    .....
  },
  dealData() {
    ....
    ....
  }
}
```

