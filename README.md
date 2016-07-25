# jquery.underscore.render jQuery Plugin

## Demo & Examples

<https://virtuecai.github.io/jquery.underscore.render/>

## Example Usage

### HTML
```html
<style>
  .underscore-template {
    display: none;
  }
</style>
```
```html
<table>
    <tbody id="tbody1">
        <script class="underscore-template" type="text/html">
            <tr>
                <td>{%= $index %}</td>
                <td>{%= name %}</td>
                <td>{%= age %}</td>
                {% _.each(cars, function(a , b, c){ %}
                <td>{%= a %}</td>
                {% }); %}
            </tr>
        </script>
    </tbody>
</table>
```

```js
var userList = [
    {name: 'virtuecai', age: 18, cars: ['car1','car2']},
    {name: 'lq', age: 20, cars: ['car1','car2', 'car3']}
];
$('#tbody1').templateRender({data: userList});
```

```html
<table>
    <tbody id="tbody2">
        <tr class="underscore-template">
            <td>{%= $index %}</td>
            <td>{%= name %}</td>
            <td>{%= age %}</td>
        </tr>
    </tbody>
</table>
```

```js
var userList = [
    {name: 'virtuecai', age: 18},
    {name: 'lq', age: 20}
];
$('#tbody2').templateRender({data: userList});
```

```html
<div class="container">
    <h1 class="underscore-template">
        <span>hello, {%= name %}, {%= age %}</span>
    </h1>
</div>
```

```js
var user = {name: 'virtuecai', age: 18};
$('div.container').templateRender({data: user});
```

## Options

```javascript
options: {
    data: {} || [], //渲染模版的数据, 对象{} 或者 对象数组[{..},{..}]
    enableDefaultImageSrc: false, // default-src 为 data-src 加载失败后显示的图片, data-src='' 最终会 set attr src 中
    autoRemove: true,  //自动移除上一次渲染的元素
    beforeCallback: function () {}, //渲染前
    afterCallback: function () {}, //渲染后
    emptyDataCallBack: function () {} //检查到传入 data 数据为空时回调
}
```

## Notes
* 依赖 [underscore](http://www.css88.com/doc/underscore/)
* 轻量级
* 正对于图片显示, 请使用 data-src;
* Demo 示例, 用的 seajs, 不熟悉移除即可.
* 可渲染单个/多个数据;
* 针对于table(强解析)动态td, tr, th 等, 采用`<script>`;

